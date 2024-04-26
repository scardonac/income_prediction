# Predicción de ingresos en tienda de mobiliario

[![Python](https://img.shields.io/badge/Python-3.12%2B-blue)](https://www.python.org/)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)](https://jupyter.org/)
[![XGBoost](https://img.shields.io/badge/XGBoost-2.0.3-blue)](https://xgboost.readthedocs.io/en/latest/)
[![LightGBM](https://img.shields.io/badge/LightGBM-4.3.0-blue)](https://lightgbm.readthedocs.io/en/latest/)
[![Optuna](https://img.shields.io/badge/Optuna-3.6.1-blue)](https://optuna.org/)
[![mlflow](https://img.shields.io/badge/mlflow-2.12.1-blue)](https://mlflow.org/)

![GitHub License](https://img.shields.io/github/license/MateoVelasquez/book_catalog)
![GitHub watchers](https://img.shields.io/github/watchers/MateoVelasquez/book_catalog)
![GitHub forks](https://img.shields.io/github/forks/MateoVelasquez/book_catalog)

## Tabla de Contenido
1. [Introducción](#introducción)
2. [Descripción de los Datos](#descripción-de-los-datos)
3. [Imputación de Datos en el Catálogo](#imputación-de-datos-en-el-catálogo)
4. [Preparación de Datos](#preparación-de-datos)
5. [Análisis Descriptivo](#análisis-descriptivo)
6. [Preprocesamiento de Datos](#preprocesamiento-de-datos)
7. [Modelado de Datos](#modelado-de-datos)
8. [Evaluación del Modelo](#evaluación-del-modelo)
9. [Conclusiones y Recomendaciones](#conclusiones-y-recomendaciones)

## Introducción
Este proyecto tiene como objetivo predecir los ingresos de una tienda de mobiliario utilizando técnicas avanzadas de aprendizaje automático. Los ingresos son una métrica fundamental para la gestión efectiva de negocios, ya que permiten evaluar el desempeño financiero, realizar proyecciones de crecimiento y tomar decisiones estratégicas en la gestión de inventario y la optimización de la cadena de suministro.

La predicción precisa de los ingresos de una tienda de mobiliario es crucial para garantizar niveles óptimos de stock, maximizar la rentabilidad y satisfacer la demanda de los clientes de manera eficiente. Mediante el uso de herramientas como pandas, matplotlib, seaborn, XGBoost, LightGBM y Optuna, este proyecto busca construir modelos predictivos robustos que aprovechen patrones históricos, variables estacionales y factores contextuales para ofrecer pronósticos precisos y orientados al negocio.

Al aplicar técnicas de preprocesamiento de datos, imputación de valores faltantes, escalado de características y optimización de hiperparámetros, se pretende crear un flujo de trabajo de aprendizaje automático integral que permita obtener insights significativos y tomar decisiones informadas para mejorar el rendimiento y la competitividad de la tienda de mobiliario en el mercado.

## Descripción de los Datos
El conjunto de datos comprende información detallada sobre los ingresos de los productos de la tienda, que incluyen las siguientes variables:

- date: Representa el momento en que se produjo el evento de venta.
- product_id: Identificador único para cada producto.
- category: Categorización de los productos.
- size: Tamaños de los productos categorizados como pequeño, mediano o grande.
- premium: Variable ficticia que indica si el producto es premium (1) o no (0).
- exclusive: Variable ficticia que indica si el producto es exclusivo (1) o no (0).
- seasonal: Variable ficticia que identifica productos vendidos solo durante estaciones específicas (1 para noviembre, diciembre, enero; 0 para todo el año).
- total_amt: Variable objetivo que indica el ingreso en dólares por día para cada producto.

## Estructura de carpetas
```
├── README.md
├── data
├── notebooks
│ ├── income_prediction.ipynb
└── requirements.txt
```
En esta estructura:

- **data**: Contiene los archivos CSV que contienen los datos de catalogo de productos, datos de demanda y datos económicos.
- **notebooks**: Contiene el Jupyter notebook utilizados para la exploración de datos, preprocesamiento, modelado y evaluación de modelos.
- **README.md**: Documentación principal del proyecto que describe la estructura, los datos, los pasos y los resultados del proyecto.
- **requirements.txt**: Archivo que lista las dependencias y versiones de Python necesarias para reproducir el entorno del proyecto.

## Imputación de Datos en el Catálogo
La imputación de datos es un paso crucial en el manejo de valores faltantes dentro del conjunto de datos. En este proyecto, empleamos el algoritmo KNNImputer para la imputación. KNNImputer significa Imputador de Vecinos más Cercanos (KNN, por sus siglas en inglés) y es particularmente adecuado para nuestro conjunto de datos debido a su capacidad para imputar valores faltantes al considerar la similitud entre los puntos de datos.

## Preparación de Datos
En esta etapa, se llevan a cabo diversas transformaciones en los datos para prepararlos para el análisis y el modelado. Se crean variables temporales, se identifican los días festivos en Colombia usando la librería [Holidays](https://pypi.org/project/holidays/) y se incorporan los datos del [IPC](https://www.banrep.gov.co/es/estadisticas/indice-precios-consumidor-ipc) y la [tasa de ocupación y desempleo](https://www.banrep.gov.co/es/estadisticas/tasas-ocupacion-y-desempleo) mensual en Colombia. Estas variables adicionales podrían ser importantes para capturar las variaciones estacionales y económicas que pueden afectar la demanda.

## Análisis Descriptivo
Se realiza un análisis exhaustivo de los datos para comprender mejor la distribución de los ingresos a lo largo del tiempo y por categoría de productos. También se exploran las relaciones entre los ingresos y otras variables, como los días festivos, el tamaño del producto, el precio premium y más. Esto proporciona insights valiosos para el modelado y la toma de decisiones.

## Preprocesamiento de Datos
Se realizan tareas de codificación y normalización de datos para garantizar la calidad y coherencia de los datos utilizados en el modelado. 

## Modelado de Datos
Se aplican técnicas avanzadas de modelado de aprendizaje automático, incluyendo [LightGBM](https://lightgbm.readthedocs.io/en/latest/Python-Intro.html) y [XGBoost](https://xgboost.readthedocs.io/en/stable/python/python_intro.html), para predecir la demanda de productos. Estos modelos se seleccionaron por su capacidad para manejar grandes volúmenes de datos y su rendimiento en problemas de regresión. Se utilizó la librería Optuna de Python para encontrar los mejores hiperparámetros que se ajusten al modelo.

## Evaluación del Modelo
Se evalúa el rendimiento de los modelos utilizando métricas como el Root Mean Squared Error (RMSE), que proporciona una medida de la precisión de las predicciones. Esta evaluación es crucial para seleccionar el mejor modelo y comprender su capacidad predictiva.

## Conclusiones y recomendaciones

El modelo final XGBoost, entrenado con los mejores hiperparámetros identificados, representa una herramienta sólida para la predicción precisa de los ingresos futuros de productos, con un bajo error cuadrático medio (RMSE) de 353. Esta precisión es fundamental para la toma de decisiones estratégicas en la gestión de inventario y la planificación de la cadena de suministro, ya que permite una visión clara y confiable del rendimiento financiero esperado.

Para continuar mejorando el rendimiento del modelo de predicción de ingresos, se recomienda la implementación de diversas estrategias:

1. Exploración detallada de características: Se propone realizar un análisis exhaustivo de las características utilizadas en el modelo. Esto incluye la evaluación de la relevancia de cada característica, la creación de nuevas características derivadas que puedan capturar patrones más complejos, y la eliminación de aquellas que no contribuyan significativamente a la predicción.
2. Optimización de hiperparámetros avanzada: Se sugiere continuar con la optimización de hiperparámetros utilizando técnicas avanzadas, como la búsqueda bayesiana de hiperparámetros. Esta metodología busca de manera inteligente la combinación óptima de hiperparámetros para mejorar aún más el rendimiento del modelo y su capacidad predictiva.
3. Exploración de otros modelos: Además del XGBoost, se recomienda explorar otros modelos de aprendizaje automático que puedan complementar y mejorar las predicciones. Entre ellos se incluyen modelos como LSTM (Long Short-Term Memory) para capturar relaciones temporales complejas, modelos ARIMA y SARIMA para análisis de series temporales, y modelos de ensamble como la combinación de XGBoost y LightGBM para aprovechar las fortalezas de diferentes algoritmos y mejorar la robustez de las predicciones.

Estas estrategias combinadas pueden conducir a un modelo de predicción de ingresos más preciso, robusto y versátil, capaz de brindar información valiosa para la toma de decisiones estratégicas en la gestión empresarial.
