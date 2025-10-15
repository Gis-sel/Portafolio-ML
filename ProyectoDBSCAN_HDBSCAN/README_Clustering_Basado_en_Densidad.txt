# README Clustering Basado en Densidad: DBSCAN y HDBSCAN

## Objetivo
Aplicar y comparar algoritmos de clustering **DBSCAN** y **HDBSCAN** en datasets sintético y real, evaluando resultados con métricas objetivas y visualización.

## Librerías utilizadas
- `numpy`, `pandas`: manejo y cálculo numérico.
- `matplotlib`: visualización de clústeres.
- `scikit-learn`: generación de datos, escalado, PCA, DBSCAN, métricas.
- `hdbscan`: clustering jerárquico basado en densidad.

## Pasos realizados
1. Generación/carga de datasets (`make_moons`, `load_wine`).
2. Preprocesamiento con `StandardScaler` y reducción con `PCA`.
3. Clustering con DBSCAN (variando `eps`) y HDBSCAN.
4. Evaluación mediante **Silhouette Score** y **Davies-Bouldin Index**.
5. Visualización comparativa de clústeres en 2D.
6. Conclusión comparativa grupal.

## Conclusiones
- HDBSCAN se adaptó mejor a datos con densidades variables.
- DBSCAN funciona bien pero requiere ajuste manual de parámetros.
- Ambos algoritmos son adecuados para datos sin etiquetas previas.
