# Clasificación de atributos de imágenes de moda

Este repositorio contiene la comparativa de varias arquitecturas de redes neuronales convolucionales implementadas con [Keras](https://keras.io/) para la clasificación de atributos de imágenes de moda, y su evaluación mediante el dataset [DeepFashion](http://mmlab.ie.cuhk.edu.hk/projects/DeepFashion.html).

## Introducción

El conjunto de datos [DeepFashion](http://mmlab.ie.cuhk.edu.hk/projects/DeepFashion.html) se emplea como *benchmark* para diversas tareas relacionadas con imágenes de moda, tales como la clasificación de la categoría o los atributos de una prenda, o la búsqueda de artículos similares. Este trabajo se basa en el *benchmark* para la [clasificación de atributos](http://mmlab.ie.cuhk.edu.hk/projects/DeepFashion/AttributePrediction.html) (clasificación multi-etiqueta). Se parte de la version reducida del conjunto de datos (conjunto de anotaciones **anno_fine** con 26 atributos clasificados en 6 tipos) y a partir de los resultados obenidos se intenta abortar con junto de datos completo (**anno_coarse** con 1000 atributos clasificados en 5 tipos).

En el trabajo se comparan distintas arquitecturas pre-entrenadas y se establece una comparativa entre un modelo formado por un único clasificador multietiqueta, y un formado por un clasificador por tipo de atributo. Se aborda además la problemática que supone el *data imbalance* en este conjunto de datos empleando varias técnicas para aumentar el rendimiento de los modelos. 

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
    ├── data                    # Datos
    │   ├── anno_coarse         # Anotaciones de la versión completa de DeepFashion
    │   ├── anno_fine           # Anotaciones de la versión reducida de DeepFashion
    │   ├── img                 # Imágenes
    ├── doc                     # Versión html de la ejecución de los *notebooks*       
    ├── model                   # Directorio en el que persisten los modelos generados por los *notebooks*. Autogenerado durante la ejecución.    
    ├── src                     # *Notebooks* de análisis e implementación
    └── README.md
### Orden de ejecución
1. Para la ejecución de los *notebooks* es necesario copiar el dataset para [predicción de atributos](http://mmlab.ie.cuhk.edu.hk/projects/DeepFashion/AttributePrediction.html) en el directorio **data**.
2. Los *notebooks* de análisis e implementación son independientes entre sí. Los *notebooks* de análisis contienen un análisis descriptivo de los datos y el código para la generación de particiones de entrenamiento alternativas para reducir el efecto del *data imbalance* de este conjunto de datos. Los ficheros generados con estos notebooks se incluyen dentro de la carpeta de **data**, por lo que no es necesaria su ejecución antes de ejecutar los *notebooks* de implementación. 

## Resultados

Para la comparación de modelos con la versión reducida del conjunto de datos se ha empleado las métricas de precisión, exhaustividad y F1 empleando *micro-average* y *macro-average* para los *top-6* atributos. La siguiente tabla muestra los resultados obtenidos empleando un único clasificador y un clasificador por tipo de atributo. 

Micro-average:

| Modelo     |Recall   | Precision   | F1 |
|------------|---------|-------------|----|
|Clasif. único | 0.72 | 0.72 | 0.72 | 
|Clasif. múltiple | 0.76 | 0.76 | 0.76 | 

Macro-average:

| Modelo     | Recall | Precision |F1 | 
|------------|---------|-------------|----|
|Clasif. único | 0.50 | 0.56 | 0.48 |
|Clasif. múltiple | 0.54 | 0.54 | 0.51 |

Los resultados obtenidos con el conjunto completo de datos son muy inferiores al estado del arte (*top-5 recal* de 0.01 frente a 0.3-0.6 obtenido por el modelos del estado del arte). En [este repositorio](https://github.com/fdjingyuan/Deep-Fashion-Analysis-ECCV2018) se listan los principales modelos del estado del arte con mejor rendimiento sobre conjunto de datos junto con los resultados obtenidos. 

## Referencias

- [DeepFashion: Powering Robust Clothes Recognition and Retrieval with Rich Annotations](http://mmlab.ie.cuhk.edu.hk/projects/DeepFashion.html). Liu, Ziwei and Luo, Ping and Qiu, Shi and Wang, Xiaogang and Tang, Xiaoou. CVPR 2016.
- [Deep Fashion Analysis with Feature Map Upsampling and Landmark-Driven Attention](https://github.com/fdjingyuan/Deep-Fashion-Analysis-ECCV2018). Liu, Jingyuan and Lu, Hong. ECCV 2018.
