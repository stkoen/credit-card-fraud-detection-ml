# Credit Card Fraud Detection with Machine Learning

Proyecto de detección de fraude con tarjetas de crédito desarrollado a partir del enfoque de Ileberi, Sun y Wang (2022). El análisis compara Regresión Logística, Árbol de Decisión y Random Forest, evalúa los subconjuntos de variables `v1`–`v5` reportados por los autores e incorpora XGBoost como modelo adicional.

## Objetivo

Evaluar distintos modelos supervisados en una base altamente desbalanceada y analizar el equilibrio entre detección de fraude, falsas alertas y capacidad de generalización.

## Datos

Se utiliza el conjunto de datos **Credit Card Fraud Detection** de ULB/Worldline, disponible en Kaggle:

https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud

La base contiene 284.807 transacciones, de las cuales 492 corresponden a fraude. Las variables `V1`–`V28` se encuentran anonimizadas mediante análisis de componentes principales.

El archivo `creditcard.csv` no se incluye en el repositorio debido a su tamaño. El notebook lo descarga mediante `kagglehub`.

## Metodología

El flujo de trabajo incluye:

- análisis exploratorio de datos;
- partición estratificada de entrenamiento y prueba;
- escalamiento Min–Max;
- balanceo mediante SMOTE aplicado solo al entrenamiento;
- evaluación de Regresión Logística, Árbol de Decisión y Random Forest;
- comparación de los vectores de variables `v1`–`v5`;
- análisis de robustez después de eliminar filas completamente duplicadas;
- incorporación de XGBoost como modelo adicional;
- evaluación mediante Accuracy, Precision, Recall, Especificidad, F1-score, ROC-AUC, PR-AUC y matrices de confusión.

## Principales resultados

Random Forest fue el modelo con mejor equilibrio operativo entre los evaluados.

En la implementación inicial, Random Forest con las 30 variables obtuvo el mejor F1-score global. Entre los subconjuntos de variables, `v3` presentó el mejor desempeño y detectó 84 de los 98 fraudes utilizando 13 variables.

En la base sin filas duplicadas:

- Random Forest detectó 73 de 95 fraudes y generó 8 falsas alertas.
- XGBoost detectó 79 de 95 fraudes y generó 157 falsas alertas.

XGBoost alcanzó un recall mayor, mientras que Random Forest ofreció una relación más favorable entre fraudes detectados y falsas alarmas.

## Estructura del repositorio

```text
credit-card-fraud-detection-ml/
├── README.md
├── requirements.txt
└── credit_card_fraud_detection_ml.ipynb
```

## Ejecución

1. Descargar o clonar el repositorio.
2. Instalar las dependencias:

```bash
pip install -r requirements.txt
```

3. Abrir `credit_card_fraud_detection_ml.ipynb` en Google Colab o Jupyter Notebook.
4. Ejecutar todas las celdas en orden.

## Autores

- Monserrat Vera
- Khoen San Martín

## Referencia principal

Ileberi, E., Sun, Y., & Wang, Z. (2022). *A machine learning based credit card fraud detection using the GA algorithm for feature selection*. Journal of Big Data, 9, Article 24.
