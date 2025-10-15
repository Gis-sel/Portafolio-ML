## README Segmentación y Detección de Anomalías en Pacientes Crónicos


*Objetivo*

Identificar segmentos de pacientes y casos atípicos que requieran revisión prioritaria, usando técnicas no supervisadas: reducción de dimensionalidad, DBSCAN/HDBSCAN y detección de anomalías (Isolation Forest, One-Class SVM).

#Metodología

*Reducción de dimensionalidad*:

        PCA (2D) para estabilizar métricas y explicar varianza.

        t-SNE (2D) para separar visualmente estructuras no lineales.

        UMAP (2D) opcional.

*Clustering por densidad*:

        DBSCAN (hiperparámetros clave: eps, min_samples).

        HDBSCAN (si está disponible; robusto a densidades variables).

*Métricas de calidad (excluyendo ruido -1)*:

    Silhouette (mientras más alto mejor) y Davies–Bouldin (mientras más bajo mejor).

*Anomalías*:

        Isolation Forest (contamination≈0.05).

        One-Class SVM (rbf, nu≈0.05).

*Análisis cruzado:*

    coincidencia de anomalías con ruido o clústeres muy pequeños.



**Análisis de resultados**

*Estructura del espacio (PCA / t-SNE / UMAP)*

    •	PCA 2D – Varianza explicada: 0,459. Es decir, en 2 componentes lineales capturas ~46% de la estructura: moderado. Suficiente para métricas, pero no para ver toda la forma de los datos.

    •	t-SNE y UMAP: las gráficas muestran islas claras; confirman que hay separación no lineal que PCA no alcanza a reflejar del todo. Traducción: visualmente hay grupos; linealmente, la cosa es más mezclada.

*Segmentación por densidad*

    •	DBSCAN → k=1 (sin ruido), Silueta: NaN, Davies–Bouldin: NaN. Con estos hiperparámetros (p.ej., eps=0.8, min_samples=8) no logró separar en ≥2 clústeres válidos. Señal de que:
    o	El eps quedó corto para la escala de tu proyección, o la densidad varía y DBSCAN no se adapta bien.

    •	HDBSCAN → k=2, Silueta = 0,439, Davies–Bouldin = 0,580. Separación moderada (S≈0,44) con buena compacidad/separación (DB≈0,58 ↓). HDBSCAN se ajusta mejor a densidades variables y encontró 2 segmentos “creíbles” en el espacio PCA.
    En las figuras se ve: con DBSCAN los puntos quedan casi en una nube única; con HDBSCAN aparecen dos grupos diferenciados.

*Anomalías*

    •	Isolation Forest: 39 anómalos.
    •	One-Class SVM: 48 anómalos.
    •	Cruces por clúster (clave):
    o	Con DBSCAN: IF → {0: 32, -1: 7}; OCSVM → {0: 43, -1: 5}.
    (Casi todo cae en el “gran” clúster 0, porque DBSCAN no separó bien; algunos quedan como ruido.)
    o	Con HDBSCAN: IF → {-1: 34, 0: 4, 1: 1}; OCSVM → {-1: 40, 1: 2, 0: 6}.
    La mayoría de las anomalías cae en ruido (-1) y apenas unas pocas dentro de los clústeres 0/1.
    Esto es lo que queremos ver: los verdaderos raros quedan fuera de los grupos principales.
    En los scatter de anomalías (PCA) se aprecia que muchos “✗” están en colas/extremos de la nube—coherente con outliers.


*Interpretación*

    •	Segmentos: los 2 clústeres de HDBSCAN sugieren perfiles distintos (combinaciones diferentes de variables).

    Segmentar ayuda a priorizar estrategias: educación, control metabólico o seguimiento intensivo.

    •	Anomalías: concentradas en ruido → son casos atípicos o posibles errores de registro. Priorizar su revisión (validación de dato; si es correcto, seguimiento).

    Puntos anómalos pueden anticipar riesgo o calidad de dato baja.

    UMAP/t-SNE facilitan la comunicación a equipos no técnicos (visual nítida).


**Salidas**  
- Gráficos 2D de PCA / t-SNE (/ UMAP si disponible).  
- Mapas de clústeres DBSCAN y HDBSCAN.  
- Listado de anomalías por técnica.  
- Cruce de anomalías con clústeres (incluye ruido `-1`).  
- Resumen y reflexión final .

**Notas**  
- Esta actividad es *no supervisada*.
- Ajuste `eps`, `min_samples` (DBSCAN) y `min_cluster_size`, `min_samples` (HDBSCAN) para mejorar separación.  
- Para reproducibilidad se usa `RANDOM_STATE=42` cuando aplica.


#Conclusión
HDBSCAN identificó 2 clústeres con separación moderada pero consistente (Silueta=0,439 ↑; Davies–Bouldin=0,580 ↓), mientras DBSCAN no logró segmentar con los parámetros actuales (k=1).

La varianza explicada por PCA (0,459) indica que la estructura no lineal es relevante, lo que explica por qué t-SNE/UMAP muestran islas más nítidas. La detección de anomalías marcó 39 (IF) y 48 (OCSVM), con clara concentración en el ruido (-1) bajo HDBSCAN, lo que respalda su carácter atípico.

Recomendamos usar HDBSCAN como método principal de segmentación, mantener PCA para métricas y t-SNE/UMAP para comunicación, y priorizar la revisión de los casos anómalos detectados (validación y eventual seguimiento).