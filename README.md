# Limpieza de Datos - Proyecto de Ciencia de Datos y Machine Learning

Proyecto correspondiente a la materia **Ciencia de Datos y Machine Learning** de la Universidad Mayor de San Simón. El trabajo implementa un proceso reproducible de diagnóstico, limpieza, validación y exportación de dos conjuntos de datos, asi como modelos de aprendizaje, aplicados a dataset de Recursos Humanos y otro de calidad de vino tinto.

## Primer avance: Limpieza de Datos

## Datasets utilizados

### Dataset de Recursos Humanos

El archivo `HRDataset_v14.csv` contiene 311 registros y 36 variables con información laboral, demográfica y de desempeño de los empleados. Para las siguientes etapas del proyecto se considera `Termd` como variable objetivo.

### Dataset de calidad de vinos

El archivo `winequality-red.csv` contiene 1599 registros y 12 variables. Once variables representan propiedades fisicoquímicas del vino tinto y `quality` corresponde a la puntuación de calidad utilizada como variable objetivo.

Los archivos originales deben encontrarse en `datasets/originales/`.

## Procesos implementados

### 1. Diagnóstico inicial

Antes de modificar los datos se analizan:

- Dimensiones y tipos de variables.
- Valores faltantes e infinitos.
- Registros duplicados.
- Espacios externos y variantes de categorías.
- Posibles valores atípicos mediante el rango intercuartílico (IQR).
- Formatos de fecha y reglas lógicas o de dominio.
- Distribución y correlaciones de las variables numéricas del dataset de vinos.

### 2. Dataset de Recursos Humanos

El proceso de limpieza incluye:

- **Incompletitud:** análisis y tratamiento de valores faltantes según el significado de cada variable.
- **Ruido:** detección de registros duplicados y posibles valores atípicos.
- **Inconsistencias:** normalización de textos, códigos y fechas, además de la validación de relaciones lógicas entre variables.

### 3. Dataset de calidad de vinos

El proceso de limpieza incluye:

- **Inconsistencias:** validación de tipos, rangos y relaciones entre las variables fisicoquímicas.
- **Incompletitud:** detección de valores faltantes y tratamiento condicional mediante KNN cuando sea necesario.
- **Ruido:** tratamiento de valores extremos mediante winsorización y eliminación de registros duplicados.

## Segundo avance: modelos de aprendizaje

Los modelos utilizan los datasets limpios del primer avance. El preprocesamiento se integra mediante `Pipeline` y `ColumnTransformer`, con imputación de valores faltantes, codificación de variables categóricas y estandarización cuando corresponde. Los datos se dividen en 80 % para entrenamiento y 20 % para prueba, manteniendo la distribución de la variable objetivo.

### Recursos Humanos

La variable objetivo es `Termd` (`0`: empleado activo, `1`: empleado desvinculado). Se implementan Árbol de Decisión CART, Random Forest, Regresión Logística y SVM con kernel RBF. Los modelos se evalúan con exactitud, precisión, sensibilidad, F1-score, ROC-AUC, reporte de clasificación y matriz de confusión. También se analizan la importancia de las variables, los coeficientes de la regresión logística y los vectores de soporte.

### Calidad de vinos

Para el análisis por clasificación, la calidad se agrupa en las categorías **Bajo**, **Medio** y **Alto**, aplicando CART, Random Forest y Gradient Boosting con validación cruzada y búsqueda de hiperparámetros. También se implementa Regresión Logística para diferenciar vinos de calidad baja/estándar y alta, además de SVR con kernel RBF para predecir el puntaje de calidad. La evaluación incluye métricas de clasificación y regresión, matrices de confusión y comparaciones entre modelos.

## Tecnologías utilizadas

- Python 3.
- Google Colab.
- pandas.
- NumPy.
- scikit-learn (`KNNImputer`).
- scikit-learn (`Pipeline`, `ColumnTransformer`, preprocesamiento, modelos, métricas y validación).
- Matplotlib y Seaborn.
- IPython.
- pathlib y subprocess.
- Git y GitHub.

## Estructura de archivos

```text
Proyecto-C.DatosMachineLearning-1erParcial/
├── datasets/
│   ├── originales/
│   │   ├── HRDataset_v14.csv
│   │   └── winequality-red.csv
│   └── limpieza/
│       ├── HRDataset_v14_limpio.csv
│       └── winequality-red_limpio.csv
└── README.md
```

## Ejecución en Google Colab

1. Abrir el notebook del proyecto en Google Colab.
2. Ejecutar las celdas en el orden establecido.
3. El código clonará el repositorio si todavía no existe en `/content/`; si ya existe, obtendrá sus cambios más recientes.
4. Los datasets originales se cargarán desde `datasets/originales/`.
5. Se mostrarán los diagnósticos, las tablas de acciones y una comparación entre los datos originales y finales.
6. Los archivos limpios se guardarán en `datasets/limpieza/` y se descargarán automáticamente.
7. Ejecutar las celdas del segundo avance después de completar la limpieza.
8. Se prepararán los datos, se entrenarán los modelos y se mostrarán sus métricas y visualizaciones.
9. Las tablas comparativas permitirán contrastar el rendimiento de los modelos implementados.

Los CSV se exportan con separador de punto y coma (`;`) y codificación `UTF-8 con BOM`, para facilitar su apertura en Excel configurado en español.

## Archivos generados

- `HRDataset_v14_limpio.csv`
- `winequality-red_limpio.csv`

Además, durante la ejecución se muestra una tabla de auditoría con el método aplicado, la columna analizada, la cantidad de valores afectados, la acción realizada y su justificación.

## Alcance actual

La versión actual incluye la limpieza de los dos datasets y la implementación del segundo avance de modelos de aprendizaje. Comprende la división de datos, el preprocesamiento, el entrenamiento, la evaluación y la comparación de modelos de árboles, regresión y máquinas de vectores de soporte.

## Integrantes

**Grupo 13**

- Calustro Crespo Dana Lili
- Garcia Gomez Franklin Emanuel
- Peralta Andia Fernando Alan
- Portuguez Colque Jhazmin
- Quiroz Guzmán Juan Pablo
- Rocha Medina Vivian Ruby

**Docente:** Ing. Patricia Erika Rodriguez Bilbao  
**Materia:** Ciencia de Datos y Machine Learning  
**Semestre:** II/2026  
**Universidad:** Universidad Mayor de San Simón

## Fuentes de los datasets

- [Human Resources Data Set - Kaggle](https://www.kaggle.com/datasets/rhuebner/human-resources-data-set)
- [Wine Quality - UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/186/wine+quality)
