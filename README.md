# Clasificación de atributos de imágenes de moda
================================================

Este repositorio contiene la comparativa de varias arquitecturas de redes neuronales convolucionales implementadas con [Keras](https://keras.io/) para la clasificación de atributos de imágenes de moda, y su evaluación mediante el dataset [DeepFashion](http://mmlab.ie.cuhk.edu.hk/projects/DeepFashion.html).

## Introducción

## Prerequisitos
* Jupyter Notebook ([instrucciones](https://jupyter.org/install))
* Tensorflow 2.1.0 ([instrucciones](https://www.tensorflow.org/install?hl=es-419))
* Keras 2.3.1 ([instrucciones](https://keras.io/guides/))
* Pandas ([instrucciones](https://pandas.pydata.org/getting_started.html))
* Numpy ([instrucciones](https://numpy.org/install/))
* Cache Magic ([instrucciones](https://github.com/chpiatt/cache-magic))

## Inicio rápido
### Estructura
    .
    ├── .cache                  # Caché con resultados intermedios precalculados
    ├── data                    # Datos
    │   ├── anno_coarse         # Anotaciones de la versión completa de DeepFashion
    │   ├── anno_fine           # Anotaciones de la versión reducida de DeepFashion
    │   ├── img                 # Imágenes
    ├── doc                     # Versión html de la ejecución de los *notebooks*       
    ├── model                   # Directorio en el que persisten los modelos generados por los *notebooks*. Autogenerado durante la ejecución.    
    ├── src                     # *Notebooks* de análisis e implementación
    └── README.md
### Orden de ejecución
1. Para la ejecución de los *notebooks* es necesario copiar el dataset en el directorio **data**. El enlace hacia estos datos se puede obtener de la [página oficial](http://mmlab.ie.cuhk.edu.hk/projects/DeepFashion.html) de este conjunto de datos.
2. El código de este repositorio ha sido liberado junto con resultados intermedios pre-calculados mediante cachés de la librería [Cache Magic](https://github.com/chpiatt/cache-magic). Para una ejecución del notebook sin emplear los resultados intermedios es necesario eliminar el directorio **.cache**.
3. Los *notebooks* de análisis e implementación son independientes entre sí. Los *notebooks* de análisis contienen un análisis descriptivo de los datos y el código para la generación de particiones de entrenamiento alternativas para reducir el efecto del *data imbalance* de este conjunto de datos. Los ficheros correspondientes a estas versiones alternativas se incluyen en la carpeta de datos, por lo que no es necesaria su generación. 

## Resultados

Para la comparación de modelos se ha empleado las métricas de precisión, exhaustividad y F1 empleando *micro-average* y *macro-average*. La siguiente tabla muestra los resultados obtenidos empleando un único clasificador y un clasificador por tipo de atributo. 



## Referencias

- [DeepFashion: Powering Robust Clothes Recognition and Retrieval with Rich Annotations](http://mmlab.ie.cuhk.edu.hk/projects/DeepFashion.html). Liu, Ziwei and Luo, Ping and Qiu, Shi and Wang, Xiaogang and Tang, Xiaoou. CVPR 2016.
