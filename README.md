# Análisis de posible cáncer de piel mediante IA 



El proyecto se centra en el análisis de imágenes médicas, específicamente en la detección de posibles canceres de piel para respaldar la toma de decisiones clínicas. Esta herramienta tiene como objetivo mejorar la precisión y la prontitud en el diagnóstico, así como reducir los errores de clasificación. Se emplean algoritmos de aprendizaje automático para entrenar modelos que clasifiquen las imágenes como normales o anormales

La metodología que seguiremos es CRISP-DM, el cual es una metodología estándar utilizada en el campo de la minería de datos y el análisis predictivo.

Se utilizarán diferentes tipos de imágenes, incluyendo imágenes DICOM, dermatológicas y otros tipos de imágenes relevantes para el análisis médico. Trabajaremos en colaboración con el Dr. José J. Pereyra Rodríguez del Hospital Universitario Virgen del Rocío de Sevilla, el cual nos proporcionara un conjunto de más de 1500 imágenes tomadas en a pacientes reales. 

El objetivo principal es proporcionar a los profesionales de la salud una herramienta efectiva y eficiente para mejorar la detección temprana y precisa de tumores, reduciendo así la tasa de falsos positivos y negativos, y agilizando el proceso diagnóstico. Este enfoque promete un impacto positivo significativo en la atención médica al mejorar la precisión y la eficiencia en el diagnóstico de condiciones médicas potencialmente graves. Además de poder predecir en tres tonos de piel distintos y que se puedan utilizar imágenes tomadas por un smartphone.

## Comenzando

A continuacion vamos a especificar como ejecutar el proyecto.

### Pre-requisitos

Primero es necesario un interprete de archivos .ipynb, como por ejemplo Jupyter Notebook.

Ademas, se necesitan las siguientes librerias:

```
numpy
pandas
os
cv2
sys
timeit
matplotlib
seaborn
sklearn
imblearn
sklearn
tensorflow
tensorflow_addons
vit_keras
warnings
```

La versión de TensorFlow es 2.10.1, la de Cuda 64_112 y la de Cudnn 64_8.

### Directorios

Organizacion de carpetas:

- TFM-Git-X.ipynb
- Datos
   - CFX
     - imagenes
         - Clase1
         - Clase2
         - ...
     - new_images
     - salidas
     - working
   - metadata_CFX.csv
 - swintransformer

**CFX** - es la configuracion en concreto que queramos utilizar (estan implementadas en el codigo del 1 al 5).

**imagenes** - es la carpeta donde se almacenarian las imagenes, subdividiendose en carpetas con el nombre de la clase.

**ClaseX** - es la carpeta donde se almacenarian las imagenes de una clase concreta. Si bien son binarias (BENIGNO, MALIGNO) o son 7 (CARCINOMA, DERMATOFIBROMA, LENTIGO, LESION_VASCULAR, MELANOMA, NEVUS, QUERATOSIS)

**new_images** - es la carpeta donde se almacenarian las imagenes generadas por el Oversample.

**salidas** - es la carpeta donde se almacenarian los archivos del dataset .npy, los pesos de los modelos, los historiales de los entrenamientos y la matriz de pesos.

**working** - es la carpeta donde se almacenarian la imagen resultado de una imagen concreta de TFM-Git-IC.ipynb.

Es necesario que la implementación de rishigami (https://github.com/rishigami/Swin-Transformer-TF) de Swin Tranformer se encuentre en la carpeta del archivo .ipynb

## Preparacion de los Datos

A continuacion vamos a especificar como preparar los datos para el entrenamiento.

Dependiendo de si se quiere ejecutar una configuracion con clases binarias (CF2 y CF3) o de 7 (CF1, CF4 y CF5), se tendran que almacenar las imagenes en las carpetas de su clase (BENIGNO, MALIGNO) o (CARCINOMA, DERMATOFIBROMA, LENTIGO, LESION_VASCULAR, MELANOMA, NEVUS, QUERATOSIS).

Despues generar los metadatos, con TFM-Git-Lector_datos_Oversampling.ipynb, y una vez se tienen los metadatos generar los archivos .npy. De ser necesario, tambien formar nuevas imagenes con oversample en ese mismo archivo.

## Entrenamiento

A continuacion vamos a especificar como entrenar las distintas configuraciones.

Primero, en TFM-Git-Entrenamiento.ipynb, especifica una configuracion (CF1, CF2, CF3, CF4, CF5) y marcala como 'True'. Despues especifica que modelos entrenar y que modelos testear.

## Medir Accuracy de la Inteligencia Colectiva

A continuacion vamos a especificar como medir el Accuracy de la Inteligencia Colectiva.

Primero es necesario tener todos los pesos de las redes y la matriz de pesos de la configuracion concreta que quieras utilizar. Segundo, en TFM-Git-Medidor-Acc-IC.ipynb, especifica una configuracion (CF1, CF2, CF3, CF4, CF5) y marcala como 'True'.

## Como utilizar la Inteligencia Colectiva para predecir con imagenes

A continuacion vamos a especificar como utilizar la Inteligencia Colectiva para predecir con imagenes.

Primero es necesario tener todos los pesos de las redes y la matriz de pesos de la configuracion concreta que quieras utilizar. Segundo, en TFM-Git-IC.ipynb, especifica una configuracion (CF1, CF2, CF3, CF4, CF5) y marcala como 'True'. Tercero, especificar la imagen la cual se quiere predecir su clase.

## Autores

* **Enrique Fernández Morales**

> Idea original de David Martin Tinaquero 

## Licencia

Este proyecto está bajo la Licencia CC0-1.0 - mira el archivo [LICENSE.md](LICENSE.md) para detalles

