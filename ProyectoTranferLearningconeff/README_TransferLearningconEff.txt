## README Transfer Learning con EfficientNet

### Estructura
- `notebooks/Plantilla.ipynb`: flujo completo de Transfer Learning (este archivo).
- `data/` (opcional): datasets locales si no usas CIFAR-10.
- `models/` (opcional): pesos exportados / TFLite.

### Librerías y para qué se usaron
- **tensorflow / keras**: carga del dataset, definición del modelo base (ResNet50/EfficientNetB0), *transfer learning*, entrenamiento y evaluación.
- **numpy**: manejo de arreglos y utilidades numéricas.
- **matplotlib.pyplot**: visualización de curvas, grid de predicciones y matrices.
- **sklearn.metrics**: `confusion_matrix`, `classification_report` para evaluación detallada.

### Resultados esperados (CIFAR-10)
- Convergencia rápida en pocas épocas con la base congelada.
- Mejora moderada tras el fine-tuning.
- Visualizaciones generadas: **accuracy**, **loss**, **grid predicciones**, **matriz de confusión** y **reporte de clasificación**.