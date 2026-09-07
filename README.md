# Limpieza de Datos - Proyecto de Ciencia de Datos y Machine Learning

Proyecto correspondiente al primer avance de la materia **Ciencia de Datos y Machine Learning** de la Universidad Mayor de San Simón. El trabajo implementa un proceso reproducible de diagnóstico, limpieza, validación y exportación de dos conjuntos de datos: uno de Recursos Humanos y otro de calidad de vino tinto.

## Objetivo

Aplicar los tres procesos de limpieza solicitados en la materia —incompletitud, ruido e inconsistencias— de acuerdo con las características de cada dataset, registrando las acciones realizadas y generando archivos CSV preparados para las siguientes etapas del proyecto.

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

## Tecnologías utilizadas

- Python 3.
- Google Colab.
- pandas.
- NumPy.
- scikit-learn (`KNNImputer`).
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

Los CSV se exportan con separador de punto y coma (`;`) y codificación `UTF-8 con BOM`, para facilitar su apertura en Excel configurado en español.

## Archivos generados

- `HRDataset_v14_limpio.csv`
- `winequality-red_limpio.csv`

Además, durante la ejecución se muestra una tabla de auditoría con el método aplicado, la columna analizada, la cantidad de valores afectados, la acción realizada y su justificación.

## Alcance actual

Esta versión corresponde únicamente al primer avance de limpieza de datos. Todavía no incluye la división en datos de entrenamiento y prueba, el entrenamiento de modelos regresionales o de árboles de decisión, ni la evaluación de su rendimiento.

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
