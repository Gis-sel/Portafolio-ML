# Scoring de Crédito con Redes Neuronales Profundas

**Objetivo del Proyecto**  
Desarrollar y evaluar un **modelo de scoring crediticio** usando **redes neuronales profundas** para estimar la probabilidad de incumplimiento (PD). Se compara contra baselines clásicos (Regresión Logística/Árboles) y se documenta el flujo de preparación de datos, manejo de desbalance y validación.

---

**Estructura del Notebook**
- **Importación de librerías**
- **Carga y entendimiento de datos** (diccionario de variables, target binario)
- **Preprocesamiento**
  - Imputación de nulos, winsorización/outliers (si aplica)
  - Codificación de categóricas (One-Hot/Target Encoding con cuidado de *leakage*)
  - **Estandarización/normalización** de numéricas
  - División **train/validation/test** (estratificada)
  - **Manejo de desbalance**: *class weights*, *oversampling* (SMOTE) o *undersampling* (según pruebas)
- **Modelado (DNN)**
  - Diseño de arquitectura (capas densas, activaciones, *dropout*, *batch norm*)
  - Función de pérdida (BCE) y **ponderación por clase**
  - Callbacks: **EarlyStopping**, **ReduceLROnPlateau**, *ModelCheckpoint*
- **Baselines**
  - Regresión Logística (regularizada)
  - Árbol/Random Forest o Gradient Boosting (opcional)
- **Evaluación**
  - Curvas **ROC** y **PR**, **AUC ROC** y **AUC-PR**
  - **KS**, **Gini** (= 2·AUC − 1), **Brier score**
  - **Calibración** (calibration curve / isotonic / Platt)
  - Matriz de confusión por **umbral seleccionado** (coste-sensitivo)
- **Explicabilidad y monitoreo**
  - Importancias/SHAP en versión *deep* o sobre un modelo simplificado
  - **Stability**: PSI/ drift sencillo entre train y test (si corresponde)
- **Conclusiones y próximos pasos**

---

## Librerías Utilizadas y Propósito

- **pandas, numpy**: preparación y transformación de datos.  
- **scikit-learn**: partición estratificada, *pipelines*, escalado, métricas (ROC/PR, KS, Brier), calibración y baselines.  
- **imbalanced-learn** (opcional): **SMOTE/SMOTENC** y undersampling.  
- **TensorFlow/Keras** o **PyTorch**: definición y entrenamiento de la red (capas densas, activaciones, *dropout*, *batch norm*, *early stopping*).  
- **matplotlib** (y/o **seaborn**): curvas ROC/PR, calibración, distribución de *scores*.  
- **shap** (opcional): explicabilidad local/global del modelo.

---

## Resultados Esperados
- **AUC ROC** y **AUC-PR** para comparar modelos.  
- **KS** y **Gini** como métricas de *ranking power* en crédito.  
- **Curvas de calibración** y **Brier score** para evaluar probabilidad bien calibrada.  
- **Matriz de confusión** al **umbral óptimo** (coste-sensitivo) y análisis de *trade-offs* (TPR/FPR).  
- Comparativa cualitativa con **Regresión Logística** (baseline) y modelo basado en árboles/ensamble (opcional).  
- Comentarios de **explicabilidad** (SHAP/feature importance) y **estabilidad** (PSI).

---

## Reproducción Rápida

```bash
pip install numpy pandas scikit-learn matplotlib seaborn
# Elige un framework de deep learning:
pip install tensorflow  # o bien
pip install torch torchvision torchaudio
# Opcional:
pip install imbalanced-learn shap
