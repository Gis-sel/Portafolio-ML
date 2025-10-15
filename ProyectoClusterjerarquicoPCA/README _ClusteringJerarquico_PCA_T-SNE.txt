# README
Exploración de Datos con Clustering Jerárquico y Reducción de Dimensionalidad

**Objetivo del Proyecto**
Este proyecto aplica **clustering jerárquico aglomerativo** sobre un dataset sin etiquetas conocidas (Iris) para explorar patrones ocultos. Posteriormente, se visualizan los resultados utilizando **PCA** y **T-SNE**, comparando su efectividad como herramientas exploratorias en aprendizaje no supervisado.

---

**Estructura del Notebook**
El notebook sigue la siguiente secuencia lógica:

*Importación de librerías*
*Carga y escalado del dataset*
*Aplicación de clustering jerárquico*
   - Generación de dendrograma
   - Agrupamientos con 2 y 3 clusters
*Reducción de dimensionalidad*
   - Visualización con PCA (2D)
   - Visualización con T-SNE (2D)
*Interpretacion de resultados*
   - Estructura
   - Diferencias entre PCA y T-SNE
   - Conclusión

---

## Librerías Utilizadas y Propósito

* numpy: Manipulación numérica y creación de arreglos.  
* pandas: Manejo de estructuras de datos tipo DataFrame.  
* matplotlib.pyplot: Visualización gráfica (dispersión, dendrogramas).Graficar PCA y T-SNE, y los resultados del clustering.

* seabor: Gráficos estadísticos mejorados.  
* sklearn.datasets: Cargar datasets
* sklearn.preprocessing (StandardScaler): Escalado de variables.  Normalizar los datos antes del clustering.
* scipy.cluster.hierarchy: Realización de clustering jerárquico y generar dendrogramas.  linkage y dendrogram.
* sklearn.cluster (AgglomerativeClustering): Creación de  agrupamientos jerárquicos con número de clusters definido.  Generamos 2 y 3 clusters para comparar.
* sklearn.decomposition (PCA): Reducción lineal de dimensionalidad. Representación de datos en 2D para graficar.
* sklearn.manifold (TSNE): Reducción no lineal de dimensionalidad.  Muestra clusters en espacio 2D más realista para datos complejos.

---

## Resultados Esperados
- Dendrograma mostrando jerarquías de agrupamiento.
- Visualizaciones de 2 y 3 clusters en PCA y T-SNE.
- Comparación clara entre métod
