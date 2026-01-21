# Análisis Multivariado de Calidad del Aire y Patrones Meteorológicos (SIMA)

## Descripción del Proyecto
Este proyecto tiene como objetivo analizar, modelar y predecir el comportamiento de contaminantes atmosféricos en el Área Metropolitana de Monterrey utilizando datos históricos del **Sistema Integral de Monitoreo Ambiental (SIMA)**.

El análisis abarca el periodo **2020-2025** y sigue la metodología **CRISP-DM**, enfocándose en la interacción entre variables meteorológicas (viento, temperatura, radiación) y contaminantes criterio (PM10, PM2.5, O3, NOx, etc.) mediante técnicas estadísticas multivariadas.

## Estructura del Repositorio

La organización del proyecto sigue una estructura lógica para garantizar la reproducibilidad del análisis científico:

```text
├── data
│   ├── external       <- Diccionarios de datos (catálogos de estaciones, rangos SIMA).
│   ├── interim        <- Datos con limpieza preliminar (e.g., unión de años, corrección de fechas).
│   ├── processed      <- Datos imputados, normalizados y listos para PCA/Modelado.
│   └── raw            <- Archivos CSV originales del SIMA (inmutables).
│
├── docs               <- Documentación extendida (Reportes PDF de etapas del negocio y datos).
│
├── notebooks          <- Jupyter notebooks numerados por etapa:
│                         1.0-eda-inicial.ipynb
│                         2.0-preprocesamiento-imputacion.ipynb
│                         3.0-analisis-multivariado-pca.ipynb
│                         4.0-modelado-predictivo.ipynb
│
├── references         <- Manuales técnicos del SIMA y papers sobre contaminación atmosférica.
│
├── reports            <- Reportes finales generados (HTML/PDF).
│   └── figures        <- Gráficos de series de tiempo, rosas de viento y biplots.
│
└── pyproject.toml     <- Gestión de dependencias (Python).
```
## Instalación y Requisitos
El proyecto utiliza Python 3.x. Las bibliotecas principales para el manejo de datos atmosféricos y estadísticos son:

Pandas & NumPy: Manipulación de series de tiempo y matrices.

Scikit-learn: Algoritmos de imputación, PCA y modelado.

Matplotlib & Seaborn: Visualización estadística.

MetPy / Windrose: (Opcional) Para gráficos especializados de meteorología.

Para instalar las dependencias:
pip install -r requirements.txt
# O si usas poetry/toml
poetry install

Descripción de los Datos
Los datos provienen de la red de monitoreo de Nuevo León.

Variables Principales (Features)

Meteorológicas:

TOUT: Temperatura ambiente (°C)

WSR: Velocidad del viento (km/h)

WDR: Dirección del viento (Grados azimutales)

RH: Humedad relativa (%)

SR: Radiación solar (kW/m²)

PRS: Presión atmosférica (mm Hg)

RAINF: Precipitación (mm/h)

Contaminantes:

PM10, PM2.5: Material particulado (μg/m 3)

O3: Ozono (ppb)

NO, NO2, NOx: Óxidos de nitrógeno (ppb)

CO: Monóxido de carbono (ppm)

SO2: Dióxido de azufre (ppb)

Flujo de Procesamiento (Pipeline)

Raw: Ingesta de archivos CSV anuales/mensuales por estación (Noreste, Sureste, Centro, etc.).

Interim: Concatenación de DataFrames, manejo de banderas de error (códigos de mantenimiento o falla eléctrica).

Processed:

Imputación de valores faltantes (e.g., Interpolación lineal o MICE).

Transformación de variables de viento (descomposición vectorial U/V).

Estandarización (Z-score) para Análisis de Componentes Principales (PCA).

## Metodología
Se aplican las siguientes técnicas estadísticas:

EDA (Análisis Exploratorio): Detección de outliers estacionales y distribuciones.

Correlación: Matrices de correlación (Pearson/Spearman) para identificar multicolinealidad.

Análisis Multivariado: Reducción de dimensionalidad para entender patrones latentes de contaminación.

Modelado: Regresión o Clasificación para predicción de alertas ambientales.

## Contribuidores
Ana Lidia Hernández Diaz 
Ana Paula García Valverde 
René Cumplido Feregrino 
Jorge Eduardo González Cantú 
## Licencia
Este proyecto es de uso académico y divulgativo. Los datos originales pertenecen al gobierno del estado de Nuevo León.

