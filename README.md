# Repositorio de Ciencia Reproducible del Capítulo [Red de transmisión y vigilancia de farmacorresistencia del VIH en la CDMX](https://salud.conacyt.mx/vih/)

## Introducción y objetivo

Este repositorio se desarrollo con el proposito de que las personas usuarias puedan reproducir la información (visualizaciones) de una forma similar a la que se encuentran en el capítulo [Red de transmisión y vigilancia de farmacorresistencia del VIH en la CDMX](https://salud.conacyt.mx/vih/) que pertenece al [Ecosistema Nacional Informático de Salud](https://salud.conacyt.mx/).

Para ello, 1) facilita la descarga de los datos directemante desde le portal, 2) lleva a cabo modificaciones a la base de datos descargada y extrae calculos necesarios para crear vizualizaciones y 3) finalmente proporciona un ejemplo de código que permite construir las diferentes visualizaciones que se muestran en el portal en la sección de [Red](https://salud.conahcyt.mx/vih/) y[Estadísticas](https://salud.conahcyt.mx/vih/estadisticas) utilizando bibliotecas de Python.

La información mostrada en el sitio es obtenida y proporcionada por la Clínica Especializado Condesa en colaboración con el Centro de Investigación de Enfermedades Infecciosas y el Centro Nacional para la Prevención y control del VIH/SIDA, dicha información aporta conocimiento acerca de la red de transmisión de VIH en la Ciudad de México y su área Metropolitana.   

Para poder reproducir las visualizaciones es necesario que todas las dependencias del repositorio estén instaladas (ver más adelante) e ir reproduciendo cada cuaderno integrado en la carpeta "procesamiento" en orden ascendente:  


## Requerimientos e instalación

Para instalar las bibliotecas y dependencias de este proyecto se puede utilizar cualquiera de los siguientes archivos:
- `Pipfile` usando [`pipenv`](https://pipenv-fork.readthedocs.io/en/latest/index.html).
- `requirements.txt` para instalar mediante pip o utilizando [`conda`](https://docs.conda.io/en/latest/).

Las bibliotecas principales para ejecutar el procesamieto son:

- [Python](https://www.python.org/) (versión 3.10)
- [pandas](https://pandas.pydata.org/) (1.4.4)
- [openpyxl](https://pypi.org/project/openpyxl/) (3.1.0)
- [geopandas](https://geopandas.org/) (0.12.2)
- [rich](https://pypi.org/project/rich/) (13.3.1)
- [thefuzz](https://github.com/seatgeek/thefuzz) (0.19.0)
- [unidecode](https://pypi.org/project/Unidecode/) (1.3.6)
- [levenshtein](https://pypi.org/project/python-Levenshtein/) (0.20.9)


### Para instalar dependencias con `pipenv`
- Inicar entorno con pipenv y paquetes 

```bash
pip install pipenv
pipenv shell --python 3.10
python -m pip install --upgrade pip
pip install -r requirements.txt
```
- Salir del entorno virtual 
```bash
exit
```
- Si se quiere eliminar entorno virtual `pipenv` 
```bash
pipenv --rm
```

### Para instalar dependencias con `conda`
- Al crear el entorno virtual
```bash
conda create --name <nombre_del_ambiente> --file requirements.txt
```

- En caso de que el ambiente virtual ya exista
```bash
conda install --file requirements.txt
```

## Estructura del repositorio

El repositorio se encuentra dividido en las siguientes carpetas:

- `datos`: Carpeta donde se encuentran los datos de entrada y salida de los procesamientos.
    - `datos_originales`: Carpeta donde se descargaran los datos del portal.
    - `datos_procesados`: Carpeta donde se encuentran los datos de salida generados a partir del notebook "01_descarga" y que se utilizaran en el resto de los procesamintos.        
    - `imagenes`: Guarda las imágenes de referencia del portal.
    - `procesamiento`: Carpeta donde se encuentran los notebooks de procesamiento.


y los siguientes archivos:

- `README.md`: Archivo que contiene la información del repositorio.
- `requirements.txt`: Archivo que contiene las dependencias del proyecto.
- `Pipfile`: Archivo que contiene las dependencias del proyecto en versión `pipenv`.
- `Pipfile.lock`: Archivo que contiene todas las dependencias y subdependencias del proyecto para `pipenv`.


# Descripción detallada de los cuadernos


## 01_descarga
Este cuaderno contiene el código necesario para descargar los datos desde el portal sección: [Datos](https://salud.conahcyt.mx/vih/datos). Posteriormente extrae los datos de la carpeta en formato ZIP descargada y genera las columnas de datos necesarias para los procesamientos porteriores. Al finalizar el proceso se generan los siguientes archivos en formato csv: 

- *nodos.csv*
- *enlaces.csv*
- *sig_nodos.csv*


### 02_bigotes

 Este cuaderno genera las visualizaciones de: **I. Conteo de linfocitos con respecto a edad / II. Carga viral por rango de edad**

### 03_barras_simples.ipynb

 Este cuaderno calcula el promedio de la carga viral (`cv`) y del conteo de linfocitos (`CD4_A`) para diferentes rangos de edad partir de los datos descargados del portal y genera las visualizaciones de: **I. Distribución del conteo de linfocitos T CD4+ / II. Distribución de la carga viral**

### 04_linea_tiempo

Este cuaderno contiene el código para el calculo la cantidad de pacientes presentan resistencia a algún antirretroviral a partir de los datos descargados del portal y genera la visualización de: **I. Cambio en la proporción de participantes con resistencia a antirretrovirales a través del tiempo**. Además, calcula la cantidad de participantes que pertenecen a un conglomerado y el número de conglomerados a través del tiempo y genera las visualizaciones de: **II. Participantes que conforman un conglomerado** y **III. Número de conglomerados en el tiempo**.

### 05_barras_apiladas

Este cuaderno contiene el código para el calculo del número de participantes que cuentan con seguridad social segun su género y crea la visualización de: **I. Segiridad social con respecto al género** y **II. Resistencia a antirretrovirales**.

### 06_violines

Este cuaderno contiene el código para el calculo de los participantes que cuentan con algún tipo de seguridad social segun su edad y crea la visualización de: **I. Segiridad social con respecto a la edad** y **II. Resistencia a antirretrovirales con respecto a la edad**.


## Licencia

#### SOFTWARE LIBRE Y ESTÁNDARES ABIERTOS

Sisdai está alineado a las disposiciones establecidas por la Coordinación de Estrategia Digital Nacional (DOF: 06/09/2021) en donde se estipula que las "políticas y disposiciones tienen como objetivo fortalecer el uso del software libre y los estándares abiertos, fomentar el desarrollo de aplicaciones institucionales con utilidad pública, lograr la autonomía, soberanía e independencia tecnológicas dentro de la APF".
