# Credit Card Fraud Detection with Machine Learning

**Montserrat Vera y Khoen San Martín · Ciencia de Datos para la Economía · Universidad Diego Portales**

Proyecto académico de implementación y evaluación de modelos de clasificación, basado en la metodología de Ileberi, Sun y Wang (2022). El trabajo contrasta regresión logística, árbol de decisión y Random Forest, examina las selecciones de variables `v1`–`v5` del artículo e incorpora XGBoost como extensión.

El propósito es estudiar y contrastar una metodología publicada; no se reivindica un algoritmo original ni una reproducción numérica exacta de todos los resultados del artículo.

## Datos y enfoque

Se utiliza la base [Credit Card Fraud Detection de ULB/Worldline](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud), con 284.807 transacciones y 492 casos de fraude. Las variables `V1`–`V28` están anonimizadas mediante componentes principales. El archivo `creditcard.csv` no se distribuye en el repositorio; el notebook lo obtiene con `kagglehub`.

El análisis considera exploración de datos, partición estratificada, escalamiento Min–Max, SMOTE aplicado únicamente al entrenamiento, comparación de subconjuntos de variables y una evaluación adicional tras retirar filas duplicadas.

Dado el desbalance, los resultados se examinan con precision, recall, especificidad, F1-score, ROC-AUC, PR-AUC y matrices de confusión, no solamente con accuracy.

## Resultados destacados

En la implementación inicial, Random Forest con las 30 variables obtuvo el mayor F1-score global. Entre los subconjuntos evaluados, `v3` detectó 84 de 98 fraudes utilizando 13 variables.

En la evaluación sin filas duplicadas:

| Modelo | Fraudes detectados | Falsas alertas |
|---|---:|---:|
| Random Forest | 73 de 95 | 8 |
| XGBoost | 79 de 95 | 157 |

XGBoost presentó mayor recall; Random Forest generó considerablemente menos falsas alertas. La elección entre modelos depende del costo de omitir fraudes y del costo de investigar alertas, que no se estiman monetariamente en este trabajo.

## Código y ejecución

El análisis está disponible en [credit_card_fraud_detection_ml.ipynb](credit_card_fraud_detection_ml.ipynb). Para reproducirlo en Jupyter o Google Colab:

```bash
pip install -r requirements.txt
```

Luego, abrir el notebook y ejecutar las celdas en orden. La descarga de la base requiere conexión a Internet. El código y los resultados deben interpretarse en el contexto de este ejercicio académico.

## Referencia y autoría

**Autores del proyecto académico:** Montserrat Vera y Khoen San Martín.

Ileberi, E., Sun, Y., & Wang, Z. (2022). *A machine learning based credit card fraud detection using the GA algorithm for feature selection*. Journal of Big Data, 9, Article 24.

La referencia se reconoce como fuente metodológica; el conjunto de datos se atribuye a ULB/Worldline.
