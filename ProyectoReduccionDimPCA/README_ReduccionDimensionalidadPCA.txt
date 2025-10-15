# Reducción de Dimensionalidad con PCA

**Objetivo del Proyecto**  
Aplicar **PCA (Principal Component Analysis)** para reducir la dimensionalidad de un dataset tabular, visualizando los datos en 2D/3D, cuantificando la **varianza explicada** y analizando el impacto de la estandarización previa. Se incluye comparación cualitativa con el espacio original y lineamientos para interpretar las componentes.

---

**Estructura del Notebook**
- **Importación de librerías**
- **Carga del dataset** (o uso de un dataset de ejemplo)
- **Preprocesamiento**
  - Imputación de faltantes (si aplica)
  - **Estandarización** con `StandardScaler`
- **PCA**
  - Ajuste y transformación
  - **Varianza explicada por componente** y **acumulada**
  - Selección de número de componentes (umbral, p. ej. 90–95%)
- **Visualización**
  - **PCA 2D** (componentes 1 y 2)
  - (Opcional) **PCA 3D** (componentes 1–3)
- **Interpretación**
  - Carga de variables por componente (loadings)
  - Discusión de patrones y separabilidad aparente
- **Conclusiones y próximos pasos**

---

## Librerías Utilizadas y Propósito

- **numpy, pandas**: manejo y preparación de datos (arrays/DataFram
