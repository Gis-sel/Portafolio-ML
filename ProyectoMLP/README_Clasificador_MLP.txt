# README: Clasificador MLP en Fashion-MNIST

**Objetivo:**

Este cuadernillo tiene como objetivo construir y evaluar un clasificador Multi-Layer Perceptron (MLP) sobre el conjunto de datos Fashion-MNIST, comparando el rendimiento de diferentes combinaciones de funciones de pérdida (categorical_crossentropy, mse) y optimizadores (adam, sgd). Se registran curvas de entrenamiento, métricas de evaluación y se presenta una conclusión para justificar la mejor combinación.

**Estructura:**


   **Carga y exploración del dataset:**
    *   Se carga el dataset Fashion-MNIST utilizando `tf.keras.datasets.fashion_mnist.load_data()`.
    *   Se incluye un análisis exploratorio para visualizar ejemplos de imágenes y la distribución de clases.

   **Preprocesamiento de datos:**
    *   Se preparan los datos para el entrenamiento.
    *   Se normalizan los valores de los píxeles a un rango de 0 a 1 dividiendo por 255.0.
    *   Se aplica One-hot encoding a las etiquetas utilizando `tf.keras.utils.to_categorical` para convertirlas en un formato binario adecuado para la clasificación multiclase.

   **Definición y diseño del modelo MLP:**
    *   Se define la arquitectura del clasificador MLP utilizando la API Sequential de Keras.
    *   Se especifica la estructura de las capas densas y las funciones de activación ('relu' y 'tanh') utilizadas en las capas ocultas, así como la capa de salida con activación 'softmax'.

   **Entrenamiento de modelos con diferentes configuraciones:**
    *   Se configura y ejecuta el entrenamiento de múltiples modelos MLP.
    *   Se prueban diferentes combinaciones de funciones de pérdida ('categorical_crossentropy', 'mse') y optimizadores ('adam', 'sgd') para evaluar su rendimiento.
    *   Los modelos se compilan y entrenan durante un número fijo de épocas y tamaño de lote.

   **Evaluación de modelos:**
    *   Se generan y visualizan curvas de pérdida y precisión para el entrenamiento y la validación a lo largo de las épocas.
    *   También se presenta un resumen tabular de los resultados clave (precisión en validación y prueba) para cada experimento.

   **Evaluación detallada del mejor modelo:**
    *   Se identifica el modelo con el mejor rendimiento basado en la evaluación previa y se realiza una evaluación más detallada en el conjunto de prueba.
    *   Esto incluye calcular la precisión general, generar un reporte de clasificación con métricas por clase (precisión, exhaustividad/recall, f1-score) y visualizar estas métricas en un gráfico.

   **Conclusión y reflexión:**
    *   Se presenta una conclusión que resume los hallazgos de los experimentos.
    *   Se justifica la mejor combinación de función de pérdida y optimizador basándose en las métricas de rendimiento.
    *   Se incluye una reflexión sobre el proceso y posibles mejoras futuras.

**Librerías Utilizadas:**

*   **tensorflow:** Utilizada para construir, entrenar y evaluar el modelo MLP, cargar el conjunto de datos Fashion-MNIST y realizar la codificación one-hot.
*   **numpy:** Utilizada para operaciones numéricas, manipulación de arreglos (por ejemplo, calcular la media, desviación estándar, mínimo, máximo de las intensidades de píxeles) y trabajar con los arreglos del dataset.
*   **matplotlib.pyplot:** Utilizada para crear varias gráficas, incluyendo ejemplos de imágenes, distribución de clases, histograma de intensidades, curvas de historial de entrenamiento (pérdida y precisión) y gráficos de métricas por clase.
*   **seaborn:** Utilizada para mejorar la estética de las gráficas de matplotlib y potencialmente para crear visualizaciones estadísticas (por ejemplo, usando sus paletas de colores).
*   **pandas:** Utilizada para crear y mostrar DataFrames para resumir información de los datos (detalles de normalización, detalles de codificación one-hot y resultados del entrenamiento).
*   **sklearn.metrics:** Utilizada para evaluar el rendimiento del modelo en el conjunto de prueba, específicamente para generar el reporte de clasificación y la matriz de confusión (aunque reemplazada por una gráfica de métricas por clase en la versión actual).
