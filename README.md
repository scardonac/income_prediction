# Proyecto de Predicción de Demanda de Productos

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)


![GitHub License](https://img.shields.io/github/license/MateoVelasquez/book_catalog)
![GitHub watchers](https://img.shields.io/github/watchers/MateoVelasquez/book_catalog)
![GitHub forks](https://img.shields.io/github/forks/MateoVelasquez/book_catalog)

## Tabla de Contenido
1. [Introducción](#introducción)
2. [Descripción de los Datos](#descripción-de-los-datos)
3. [Imputación de Datos en el Catálogo](#imputación-de-datos-en-el-catálogo)
4. [Preparación de Datos](#preparación-de-datos)
5. [Análisis Descriptivo](#análisis-descriptivo)
6. [Impacto del Competidor](#impacto-del-competidor)
7. [Preprocesamiento de Datos](#preprocesamiento-de-datos)
8. [Modelado de Datos](#modelado-de-datos)
9. [Evaluación del Modelo](#evaluación-del-modelo)
10. [Conclusiones y Recomendaciones](#conclusiones-y-recomendaciones)
11. [Recursos](#recursos)

## Introducción
Este proyecto tiene como objetivo predecir la demanda de productos utilizando técnicas de aprendizaje automático. La demanda es una variable crítica para la planificación de inventario y la optimización de la cadena de suministro en una empresa.

## Descripción de los Datos
El conjunto de datos comprende información detallada sobre la demanda de productos, que incluyen las siguientes variables clave:

- Fecha: Representa el momento en que se produjo el evento de venta.
- id_producto: Identificador único para cada producto.
- Categoría: Categorización de los productos.
- Sub_categoria: Subcategorías dentro de la categoría principal.
- Tamaño: Tamaños de los productos categorizados como pequeño, mediano o grande.
- Premium: Variable ficticia que indica si el producto es premium (1) o no (0).
- Marca_exclusiva: Variable ficticia que indica si el producto es exclusivo (1) o no (0).
- Estacional: Variable ficticia que identifica productos vendidos solo durante estaciones específicas (1 para noviembre, diciembre, enero; 0 para todo el año).
- Nit_proveedor: Código de identificación del proveedor.
- Demanda: Variable objetivo que indica la cantidad de unidades vendidas por día para cada producto.

Los datos 

## Estructura de carpetas
```
├── README.md
├── data
│ ├── train
│ ├── test
│ └── exogenous
├── notebooks
│ ├── demand_prediction.ipynb
├── models
│ ├── xgboost
│ └── lightgbm
├── results
│ ├── resultado_prueba.csv
└── requirements.txt
```
En esta estructura:

- **data**: Contiene los archivos CSV que contienen los datos de catalogo de productos, datos de demanda y datos económicos.
- **notebooks**: Contiene el Jupyter notebook utilizados para la exploración de datos, preprocesamiento, modelado y evaluación de modelos.
- **models**: Almacena los modelos entrenados en formato de archivo pickle (.pkl) para su posterior uso.
- **README.md**: Documentación principal del proyecto que describe la estructura, los datos, los pasos y los resultados del proyecto.
- **results**:Archivo separado con comas asociado a la predicción con el mejor modelo.
- **requirements.txt**: Archivo que lista las dependencias y versiones de Python necesarias para reproducir el entorno del proyecto.

## Imputación de Datos en el Catálogo
La imputación de datos es un paso crucial en el manejo de valores faltantes dentro del conjunto de datos. En este proyecto, empleamos el algoritmo KNNImputer para la imputación. KNNImputer significa Imputador de Vecinos más Cercanos (KNN, por sus siglas en inglés) y es particularmente adecuado para nuestro conjunto de datos debido a su capacidad para imputar valores faltantes al considerar la similitud entre los puntos de datos.

## Preparación de Datos
En esta etapa, se llevan a cabo diversas transformaciones en los datos para prepararlos para el análisis y el modelado. Se crean variables temporales, se identifican los días festivos en Colombia usando la librería [Holidays](https://pypi.org/project/holidays/) y se incorporan los datos del [IPC](https://www.banrep.gov.co/es/estadisticas/indice-precios-consumidor-ipc) y la [tasa de ocupación y desempleo](https://www.banrep.gov.co/es/estadisticas/tasas-ocupacion-y-desempleo) mensual en Colombia. Estas variables adicionales podrían ser importantes para capturar las variaciones estacionales y económicas que pueden afectar la demanda.

## Análisis Descriptivo
Se realiza un análisis exhaustivo de los datos para comprender mejor la distribución de la demanda a lo largo del tiempo y por categoría de productos. También se exploran las relaciones entre la demanda y otras variables, como los días festivos, el tamaño del producto, el precio premium y más. Esto proporciona insights valiosos para el modelado y la toma de decisiones.

## Impacto del Competidor
Se identifica que la apertura de un competidor tuvo un impacto significativo en la demanda, resultando en una disminución del 19%. Este análisis permite entender cómo eventos externos pueden afectar la demanda y cómo mitigar esos impactos en el futuro.

## Preprocesamiento de Datos
Se realizan tareas de codificación y normalización de datos para garantizar la calidad y coherencia de los datos utilizados en el modelado. 

## Modelado de Datos
Se aplican técnicas avanzadas de modelado de aprendizaje automático, incluyendo [LightGBM]([https://xgboost.readthedocs.io/en/stable/python/python_intro.html](https://lightgbm.readthedocs.io/en/latest/Python-Intro.html)) y [XGBoost](https://xgboost.readthedocs.io/en/stable/python/python_intro.html), para predecir la demanda de productos. Estos modelos se seleccionaron por su capacidad para manejar grandes volúmenes de datos y su rendimiento en problemas de regresión. Se utilizó la librería Optuna de Python para encontrar los mejores hiperparámetros que se ajusten al modelo.

## Evaluación del Modelo
Se evalúa el rendimiento de los modelos utilizando métricas como el Root Mean Squared Error (RMSE), que proporciona una medida de la precisión de las predicciones. Esta evaluación es crucial para seleccionar el mejor modelo y comprender su capacidad predictiva.

## Conclusiones y recomendaciones
El modelo final XGBoost entrenado con los mejores hiperparámetros puede ser utilizado para predecir la demanda futura de productos con un alto grado de precisión, ya que tiene un RMSE de 56.03. Este modelo es una herramienta valiosa para la toma de decisiones estratégicas en la gestión de inventario y la planificación de la cadena de suministro.

Para mejorar el rendimiento del modelo de predicción de demanda, se pueden aplicar varias estrategias. 

- En primer lugar, se sugiere realizar una exploración más detallada de las características utilizadas, considerando la creación de nuevas características derivadas y la eliminación de aquellas que no contribuyan significativamente a la predicción. 

- Continuar con la optimización de hiperparámetros utilizando técnicas avanzadas como la búsqueda bayesiana de hiperparámetros para encontrar la combinación óptima que mejore el rendimiento. 
-  Probar con otros modelos como LSTM, modelos ARIMA y SARIMA y modelos de emsamble como combinar XGBoost + Lightgbm. 
