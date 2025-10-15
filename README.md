---
## Proyectos

### 1. Clasificación con Perceptrón Multicapa (MLP)

**Enlace:** [Ver Notebook](./Clasificador_MPL.ipynb)  
**Objetivo:** Entrenar y evaluar un MLP para predecir la clase objetivo y compararlo con un baseline simple.  
**Tecnologías:** Python, NumPy, pandas, scikit-learn, Matplotlib  
**Resultados:** Evaluación con Accuracy, Precision, Recall, F1; matriz de confusión y, si corresponde, ROC/AUC.  
**Reflexión:** El MLP captura relaciones no lineales; la estandarización y el ajuste de hiperparámetros (`hidden_layer_sizes`, `alpha`, `learning_rate_init`) fueron clave. Próximo paso: búsqueda bayesiana y calibración.

---

### 2. Clustering jerárquico con PCA y t-SNE
![Mini](./assets/p2_mini.png)
**Enlace:** [Ver Notebook](./ClusteringJerarquico_PCA_TSNE.ipynb)  
**Objetivo:** Explorar la estructura interna del dataset con reducción de dimensionalidad (PCA/t-SNE) y agrupar con jerárquico para segmentos interpretables.  
**Tecnologías:** Python, pandas, scikit-learn (PCA), SciPy (linkage/dendrogram), Matplotlib  
**Resultados:** Varianza explicada acumulada (PCA), visualización 2D/3D (t-SNE) y calidad de clusters con Silhouette; opcional: Davies–Bouldin y Calinski–Harabasz.  
**Reflexión:** PCA + jerárquico ofrece visión global/local; t-SNE depende de hiperparámetros. Próximo paso: UMAP y evaluación de estabilidad con diferentes semillas.

---

### 3. Clustering con DBSCAN / HDBSCAN
![Mini](./assets/p3_mini.png)
**Enlace:** [Ver Notebook](./cluster_DBSCAN_HDBSCAN.ipynb)  
**Objetivo:** Detectar clusters por densidad y puntos ruidosos en datos con geometrías no esféricas.  
**Tecnologías:** Python, pandas, scikit-learn (DBSCAN), hdbscan, Matplotlib  
**Resultados:** Número de clusters y porcentaje de ruido; calidad de agrupamiento con Silhouette; persistencia de clusters en HDBSCAN.  
**Reflexión:** Los métodos por densidad separan ruido sin fijar k. HDBSCAN fue más estable; afinar `eps/min_samples` y `min_cluster_size` mejora resultados.

---

### 4. Regresión Lineal, Ridge y Lasso (comparativo)
![Mini](./assets/p4_mini.png)
**Enlace:** [Ver Proyecto](./proyectos/proyecto4)  
**Objetivo:** Predecir una variable continua comparando OLS contra regularización para controlar sobreajuste.  
**Tecnologías:** Python, pandas, scikit-learn, Matplotlib  
**Resultados:** RMSE, MAE y R²; validación cruzada (K-Fold) y curvas de aprendizaje.  
**Reflexión:** La regularización reduce varianza; el tuning de `alpha` equilibra error e interpretabilidad. Próximo paso: Elastic Net.

---

### 5. SVM para Clasificación
![Mini](./assets/p5_mini.png)
**Enlace:** [Ver Proyecto](./proyectos/proyecto5)  
**Objetivo:** Clasificar con SVM lineal y con kernel RBF, comparando contra baselines.  
**Tecnologías:** Python, pandas, scikit-learn, Matplotlib  
**Resultados:** Accuracy, Precision/Recall (macro), F1, ROC/AUC (binario) y matriz de confusión.  
**Reflexión:** El kernel RBF maneja fronteras no lineales; el escalado y los hiperparámetros `C` y `gamma` son determinantes. Próximo paso: calibración de probabilidades y análisis de márgenes.

---

### 6. K-NN Clasificación y Análisis de Vecindad
![Mini](./assets/p6_mini.png)
**Enlace:** [Ver Proyecto](./proyectos/proyecto6)  
**Objetivo:** Evaluar K-NN en datasets con distintas escalas y densidad, estudiando su sensibilidad al ruido.  
**Tecnologías:** Python, pandas, scikit-learn, Matplotlib  
**Resultados:** Curva de error vs K, Accuracy/F1 macro, matriz de confusión y validación K-Fold; pruebas con distintas distancias (Euclidiana/Minkowski).  
**Reflexión:** K-NN es simple pero sensible a escala y K; la normalización y la elección de distancia impactan la frontera de decisión.

---

### 7. Árboles de Decisión y Random Forest
![Mini](./assets/p7_mini.png)
**Enlace:** [Ver Proyecto](./proyectos/proyecto7)  
**Objetivo:** Comparar la interpretabilidad de Árboles con el desempeño y robustez de Random Forest.  
**Tecnologías:** Python, pandas, scikit-learn, Matplotlib  
**Resultados:** Accuracy/F1 (clasificación) o RMSE/R² (regresión); OOB score en Random Forest e importancias de variables.  
**Reflexión:** El bosque reduce sobreajuste del árbol único; existe un trade-off entre interpretabilidad y desempeño. Próximo paso: ajuste de `max_depth`, `n_estimators` y `max_features`.

---

### 8. Pipeline + GridSearchCV (validación y despliegue simple)
![Mini](./assets/p8_mini.png)
**Enlace:** [Ver Proyecto](./proyectos/proyecto8)  
**Objetivo:** Construir un pipeline reproducible con preprocesamiento, modelo y selección de hiperparámetros para un flujo sólido de entrenamiento y evaluación.  
**Tecnologías:** Python, pandas, scikit-learn, joblib  
**Resultados:** Mejor conjunto de hiperparámetros con GridSearchCV, validación (estratificada) K-Fold y métricas principales según la tarea (F1/ROC AUC o RMSE/R²).  
**Reflexión:** El pipeline evita leakage y facilita reproducibilidad; GridSearchCV documenta el mejor modelo y acelera iteraciones. Próximo paso: RandomizedSearch o Bayesian Optimization y empaquetado con joblib.
