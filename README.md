# Clasificación de Dígitos Escritos a Mano mediante los principales modelos de Machine Learning

Para cada modelo de clasifiación de dígitos MNIST se realizó validación cruzada de 5 folds para obtener los parámetros óptimos. Al obtener los parámetros óptimos obtenemos el mejor modelo lo que es muy útil para hacer una evaluación del mejor modelo para esta tarea.


## Árboles de Decisión CART
En la siguiente figura podemos apreciar la validación cruzada para los modelos de CART obteniendo que el mejor modelo fue con un $\alpha=0.001$.

![gscart](https://github.com/david-mcampa/ClasificacionMNIST-ML/assets/74944322/7bb18973-25c9-48a8-beef-4ab1cd7fa91d)

Después de obtener los mejores parámetros se uso este modelo y se obtuvieron los siguientes resultados que se muestran en la matriz de confusión y en la tabla.

![concart](https://github.com/david-mcampa/ClasificacionMNIST-ML/assets/74944322/2b70ae4d-d93a-4975-843e-67d6c895bb67)

|           | precision | recall | f1-score | support |
|-----------|-----------|--------|----------|---------|
| 0         | 0.85      | 0.91   | 0.88     | 980     |
| 1         | 0.93      | 0.92   | 0.93     | 1135    |
| 2         | 0.77      | 0.74   | 0.76     | 1032    |
| 3         | 0.81      | 0.77   | 0.79     | 1010    |
| 4         | 0.88      | 0.76   | 0.81     | 982     |
| 5         | 0.71      | 0.74   | 0.72     | 892     |
| 6         | 0.69      | 0.83   | 0.76     | 958     |
| 7         | 0.89      | 0.84   | 0.86     | 1028    |
| 8         | 0.69      | 0.72   | 0.71     | 974     |
| 9         | 0.78      | 0.76   | 0.77     | 1009    |
| accuracy  |           |        | 0.80     | 10000   |
| macro avg | 0.8       | 0.8    | 0.8      |         |
| weighted avg | 0.8    | 0.8    | 0.8      |         |

Podemos observar que obtuvo una precisión aceptable para la mitad de las clases y mala para los dígitos 2, 5, 6, 7 y 8 donde la precisión es más baja. Esto indica que el modelo clasificó muchas instancias como estos dígitos cuando no lo eran. En términos de recall, los dígitos que tuvieron menor recall fueron el 2, 3, 4, 5, 8 y 9. Estos son los dígitos que el modelo clasificó como otros dígitos distintos . Entonces, si nos fijamos en el f1-score que toma en cuenta estas dos medidas podemos decir que el 2 y el 8 fue el número mas difícil de clasificar para los árboles mientras que el 1 fue el más fácil. \\

Globalmente podemos decir que el modelo de árboles de decisión CART tuvo un mal desempeño.

## AdaBoost

![gsada](https://github.com/david-mcampa/ClasificacionMNIST-ML/assets/74944322/3181dd5e-52f3-4d75-98e4-4f82be5abea7)

Se obtuvo mediante esta validación que el mejor modelo era con un learning rate de 0.1 y 200 estimadores CART. Los resultados de este modelo se muestran a continuación.

![conada](https://github.com/david-mcampa/ClasificacionMNIST-ML/assets/74944322/1d046e44-41ea-4978-9990-0e711e57a4ef)


|           | precision | recall | f1-score | support |
|-----------|-----------|--------|----------|---------|
| 0         | 0.93      | 0.88   | 0.90     | 980     |
| 1         | 0.94      | 0.94   | 0.94     | 1135    |
| 2         | 0.74      | 0.78   | 0.76     | 1032    |
| 3         | 0.77      | 0.82   | 0.79     | 1010    |
| 4         | 0.79      | 0.83   | 0.81     | 982     |
| 5         | 0.70      | 0.66   | 0.68     | 892     |
| 6         | 0.93      | 0.67   | 0.78     | 958     |
| 7         | 0.93      | 0.79   | 0.86     | 1028    |
| 8         | 0.69      | 0.84   | 0.76     | 974     |
| 9         | 0.73      | 0.83   | 0.78     | 1009    |
| accuracy  |           |        | 0.81     | 10000   |
| macro avg | 0.82      | 0.81   | 0.81     |         |
| weighted avg | 0.82   | 0.81   | 0.81     |         |



AdaBoost tuvo valores de precision bajos en el 2, 5 y 9, y recall bajos en el 5 y 6. Esto se confirma con el f1-score diciéndonos que el 5 es el número con menor valor. Podemos concluir que el número 5 fue complicado de clasificar para AdaBoost. En los demás tuvo buenos valores de precision y
aceptables en recall diciéndonos que AdaBoost no da muchos falsos positivos pero si tiene muchos falsos negativos. 

En general podemos decir que AdaBoost tuvo un rendimiento no tan bueno. 

## Bagging



El mejor modelo fue para Baggin fue con 100 estimadores y un máximo de variables de 5 sin reemplazo en cada bootstrap, el número de muestras tomadas de los datos en cada bootstrap fue de 1.

Los resultados para este modelo fueron los siguientes:

![gsbag](https://github.com/david-mcampa/ClasificacionMNIST-ML/assets/74944322/96de290e-6f37-4498-b2f1-e89a966a1c9f)

|           | precision | recall | f1-score | support |
|-----------|-----------|--------|----------|---------|
| 0         | 0.96      | 0.99   | 0.98     | 980     |
| 1         | 0.98      | 0.99   | 0.99     | 1135    |
| 2         | 0.96      | 0.96   | 0.96     | 1032    |
| 3         | 0.97      | 0.97   | 0.97     | 1010    |
| 4         | 0.97      | 0.97   | 0.97     | 982     |
| 5         | 0.96      | 0.96   | 0.96     | 892     |
| 6         | 0.97      | 0.97   | 0.97     | 958     |
| 7         | 0.97      | 0.96   | 0.96     | 1028    |
| 8         | 0.96      | 0.95   | 0.96     | 974     |
| 9         | 0.96      | 0.95   | 0.95     | 1009    |
| accuracy  |           |        | 0.97     | 10000   |
| macro avg | 0.97      | 0.97   | 0.97     |         |
| weighted avg | 0.97   | 0.97   | 0.97     |         |


Como podemos observar en general se obtuvieron buenos valores de precision y recall para todos los números, métricas que se reflejan en el f1-score. El más bajo fue para el número 9 con 0.95 pero aún sigue siendo un valor muy bueno. Obtuvo un f1-score de 0.99 para el número 1. 

En general Bagging fue un muy buen modelo de clasificación para los dígitos MNIST. 

## Random Forest

A continuación se muestra la validación cruzada para Random Forest obteniendo que el mejor modelo fue con un número de estimadores de 300. 

![gsrf](https://github.com/david-mcampa/ClasificacionMNIST-ML/assets/74944322/f7783031-c5dd-43c9-ab64-02298fa6bac2)

Y los resultados para este modelo se encuentran en la matriz de confusión y el reporte de métricas.

![conrf](https://github.com/david-mcampa/ClasificacionMNIST-ML/assets/74944322/0a7c9174-4d0a-47f2-bd92-501c314af78a)

|           | precision | recall | f1-score | support |
|-----------|-----------|--------|----------|---------|
| 0         | 0.97      | 0.99   | 0.98     | 980     |
| 1         | 0.99      | 0.99   | 0.99     | 1135    |
| 2         | 0.96      | 0.97   | 0.97     | 1032    |
| 3         | 0.96      | 0.96   | 0.96     | 1010    |
| 4         | 0.98      | 0.98   | 0.98     | 982     |
| 5         | 0.97      | 0.97   | 0.97     | 892     |
| 6         | 0.98      | 0.98   | 0.98     | 958     |
| 7         | 0.97      | 0.97   | 0.97     | 1028    |
| 8         | 0.96      | 0.95   | 0.96     | 974     |
| 9         | 0.96      | 0.95   | 0.96     | 1009    |
| accuracy  |           |        | 0.97     | 10000   |
| macro avg | 0.97      | 0.97   | 0.97     |         |
| weighted avg | 0.97   | 0.97   | 0.97     |         |


Se obtuvo un comportamiento similar al obtenido con Bagging, pero fue superior Random Forest por una décima para varios números en precision y recall. En general podemos decir que Random Forest tuvo un desempeño muy bueno para realizar esta clasificación de dígitos MNIST.


## Redes Neuronales

 Para Redes Neuronales se obtuvieron lo siguientes resultados:

![connn](https://github.com/david-mcampa/ClasificacionMNIST-ML/assets/74944322/963c1350-c5f8-4d6f-aa3d-4fd0543d0da5)

|           | precision | recall | f1-score | support |
|-----------|-----------|--------|----------|---------|
| 0         | 0.98      | 0.99   | 0.99     | 980     |
| 1         | 0.99      | 0.99   | 0.99     | 1135    |
| 2         | 0.98      | 0.98   | 0.98     | 1032    |
| 3         | 0.97      | 0.98   | 0.98     | 1010    |
| 4         | 0.97      | 0.98   | 0.98     | 982     |
| 5         | 0.98      | 0.98   | 0.98     | 892     |
| 6         | 0.99      | 0.98   | 0.98     | 958     |
| 7         | 0.99      | 0.97   | 0.98     | 1028    |
| 8         | 0.98      | 0.97   | 0.98     | 974     |
| 9         | 0.98      | 0.98   | 0.98     | 1009    |
| accuracy  |           |        | 0.98     | 10000   |
| macro avg | 0.98      | 0.98   | 0.98     |         |
| weighted avg | 0.98   | 0.98   | 0.98     |         |


Esto se obtuvo con una red de una sola capa con 100 neuronas y un parámetro de regularización de 0.01. Notamos que tiene valores de f1-score muy altos de 0.99 y 0.98 demostrando un rendimiento excelente en la clasificación de los dígitos.

## Máquinas de Soporte Vectorial (SVM)

Los resultados para SVM fueron los siguientes:

![consvm](https://github.com/david-mcampa/ClasificacionMNIST-ML/assets/74944322/e42c3174-ee63-42a8-a63e-272eb5617b51)


|           | precision | recall | f1-score | support |
|-----------|-----------|--------|----------|---------|
| 0         | 0.98      | 0.99   | 0.99     | 980     |
| 1         | 0.99      | 0.99   | 0.99     | 1135    |
| 2         | 0.97      | 0.97   | 0.97     | 1032    |
| 3         | 0.97      | 0.98   | 0.98     | 1010    |
| 4         | 0.98      | 0.98   | 0.98     | 982     |
| 5         | 0.98      | 0.97   | 0.98     | 892     |
| 6         | 0.98      | 0.98   | 0.98     | 958     |
| 7         | 0.97      | 0.96   | 0.97     | 1028    |
| 8         | 0.97      | 0.97   | 0.97     | 974     |
| 9         | 0.97      | 0.96   | 0.96     | 1009    |
| accuracy  | 0.98      |        |          | 10000   |
| macro avg | 0.98      | 0.98   | 0.98     |         |
| weighted avg | 0.98   | 0.98   | 0.98     |         |


Obteniendo de igual manera muy buenos resultados aunque no tan buenos como la red neuronal pero si a la par de Random Forest y de Bagging. 

A continuación se muestran los resultados de los métodos mas simples que se usaron para clasificar los dígitos MNIST.

## Regresión Lineal

Para Regresión Lineal a pesar de un modelo simple fue mejor que los árboles CART por lo que es una alternativa buena si no se tiene la posibilidad de usar modelos más complejos y solo se tiene a la mano modelos simples como CART y regresión lineal.

![conlinr](https://github.com/david-mcampa/ClasificacionMNIST-ML/assets/74944322/86c1264c-92e9-455e-93e4-b6ab7895242e)

|           | precision | recall | f1-score | support |
|-----------|-----------|--------|----------|---------|
| 0         | 0.91      | 0.96   | 0.93     | 980     |
| 1         | 0.83      | 0.98   | 0.9      | 1135    |
| 2         | 0.92      | 0.79   | 0.85     | 1032    |
| 3         | 0.85      | 0.87   | 0.86     | 1010    |
| 4         | 0.81      | 0.9    | 0.85     | 982     |
| 5         | 0.88      | 0.74   | 0.8      | 892     |
| 6         | 0.88      | 0.91   | 0.9      | 958     |
| 7         | 0.85      | 0.86   | 0.86     | 1028    |
| 8         | 0.84      | 0.78   | 0.81     | 974     |
| 9         | 0.84      | 0.79   | 0.82     | 1009    |
| accuracy  |           |        | 0.86     | 10000   |
| macro avg | 0.86      | 0.86   | 0.86     |         |
| weighted avg | 0.86   | 0.86   | 0.86     |         |


Se obtuvieron resultados similares para LDA y Regresión Lineal y muy malos resultados para QDA por lo que sería el único modelo de todos que debería evitarse a toda costa para hacer clasificación de este tipo de datos.

## Análisis de Discrimante Lineal (LDA)

![conlda](https://github.com/david-mcampa/ClasificacionMNIST-ML/assets/74944322/dc20bb74-b242-4b13-b251-8275123a381d)

## Análisis de Discrimante Cuadrático (QDA)

![conqda](https://github.com/david-mcampa/ClasificacionMNIST-ML/assets/74944322/8e2c024d-84ed-494c-875c-3d4577a71e78)

## Regresión Logística
Los resultados de Regresión Logística también fueron buenos, esto concuerda con los resultados de Redes Neuronales ya que podríamos decir que Regresión Logística es como la Red Neuronal más simple de todas. Es también una buena alternativa si no se quieren implementar modelos más complejos y costosos. 

![conlr](https://github.com/david-mcampa/ClasificacionMNIST-ML/assets/74944322/c6e9b342-c845-42c6-83b5-46a2ac6ae99f)

|           | precision | recall | f1-score | support |
|-----------|-----------|--------|----------|---------|
| 0         | 0.95      | 0.97   | 0.96     | 980     |
| 1         | 0.96      | 0.98   | 0.97     | 1135    |
| 2         | 0.93      | 0.9    | 0.91     | 1032    |
| 3         | 0.9       | 0.92   | 0.91     | 1010    |
| 4         | 0.94      | 0.94   | 0.94     | 982     |
| 5         | 0.9       | 0.87   | 0.88     | 892     |
| 6         | 0.94      | 0.95   | 0.95     | 958     |
| 7         | 0.93      | 0.92   | 0.93     | 1028    |
| 8         | 0.88      | 0.88   | 0.88     | 974     |
| 9         | 0.91      | 0.92   | 0.91     | 1009    |
| accuracy  |           |        | 0.93     | 10000   |
| macro avg | 0.92      | 0.92   | 0.92     |         |
| weighted avg | 0.93   | 0.93   | 0.93     |         |


## Conclusión

Después de evaluar todos los modelos para clasificación de estos datos que son los dígitos escritos a mano MNIST yo en lo personal me quedaría con una Red Neuronal. El modelo mas cercano en métricas fue SVM pero es más costoso computacionalmente ya que tarda más tiempo en ejecutarse y aún así no supera las métricas de la red neuronal. Por otra parte modelos que también fueron cercanos fueron Random Forest y Bagging que tardan menos en ejecutarse pero no tanto como para decantarse por ellos, es decir, su costo computacional para mí no compensa el dejar las métricas tan buenas de una red neuronal para la clasificación de este tipo de datos.
