# NLP Clinic con BERT (Clasificación de Texto)

**Objetivo**  
Entrenar y evaluar un modelo BERT (o variante) para clasificación de textos, comparándolo contra baselines clásicos de NLP.

**Datos**  
Corpus etiquetado (fuente pública o interna). División train/validation/test. Manejo de desbalance si aplica.

**Técnicas**  
Limpieza mínima (tokenización a cargo del tokenizer), manejo de longitudes, fine-tuning de BERT, early stopping, y evaluación por clase.

**Modelos**  
Baselines: TF–IDF + Regresión Logística/SVM/Naive Bayes.  
Modelo principal: BERT (transformers).

**Métricas usadas**  
Accuracy, Precision, Recall, F1 (macro/weighted), matriz de confusión, (opcional) AUC. Reporte por clase.

**Resultados (resumen cualitativo)**  
BERT mejora el rendimiento frente a baselines clásicos, especialmente en clases minoritarias. Se discuten tiempos de entrenamiento e influencia de `learning_rate` y `max_len`.

**Reflexión**  
El fine-tuning de BERT eleva desempeño pero requiere más recursos. Próximo: data augmentation, congelamiento parcial de capas y explicación con LIME/SHAP para texto.

**Cómo reproducir**  
```
pip install transformers datasets scikit-learn pandas numpy matplotlib torch
```
Configura tu GPU/CPU según disponibilidad. Ejecuta el notebook y registra métricas finales.

