
## Clase 6 de Estadística avanzada

Clase 5: [[Optimización de parámetros]]


# Aprendizaje No Supervisado
Es el estudio o exploración de cómo están representados los datos y qué conclusiones podemos sacar de dicha representación

Sirven para:
- Exploración de los datos y extracción de conocimiento:
	- Clustering: Agrupar instancias que tengan una descripción similar en el espacio de features. Básicamente respondemos si hay subconjuntos de datos muy parecidos entre si.
	- Reducción de dimensionalidad: Encontrar combinaciones de geatures que reemplacen a los originales para reducir la dimensión del problema

Porque reducirla dimensionalidad:
- Visualizar
- Comprimir



# Descomposición en componentes principales (PCA)
**Problema:** Muchas veces hay variables que contienen práctimcamente la misma información que otras (muy correlacionadas entre sí), **por lo que agregan una dimensión más al problema sin aportar mucha más información**


## Esquema general
Podemos ver cómo se distribuyen los datos proyectando sobre cada uno de los features
De las distribuciones podemos calcular su varianza, como una medida de qué tan dispersos están los datos en esa dirección
Sin embargo, notamos direcciones (combinación lineal de features) donde los datos parecen variar más

Proyectando en esas nuevas direcciones 

Notar que, si nos olvidamos del componente 2, no perdemos tanta información


## Dependencias de las unidades y escaleo
¿Qué pasa con la variabilidad si cambiamos las unidades de alguna de las cariables?


## ¿Cuantos  componentes?

Al ser un problema de aprendizzaje no-supervisado, no tenemos un conjunto de test para validar el número de componentes que elijamos. ¿Con cuántas nos quedamos?


Reducción de dimensionalidad como input de otros modelos:
Podemos usar los primeros componentes principales ($Z_m$) como variable sindependientes en modelos de regresión o clasificación

$$y \sim \beta_0 + \beta_1Z_1+\dots + \beta_nZ_n$$

## Resumen de PCA
Los componentes principales son una combinación lineal de los features originales y se corresponden con los autovect


## Motivación
Es más fácil conseguir datos y más barato, es más que nada data generada con una máquina (no hay que pagarle a alguien para identificar clases o chequear el output)
- Minimizar distancia intra-cluster
- Maximiar distancia entre-cluster


Clustering - diferencia con PCA
- Reducir dimensión maximizando la varianza
- Encontrar grupos homogéneos
- Si son muchos:
	- Podría ser costoso computacionalmente
	- Podrían esconderse las características


Clustering - estrategias
- Hay muchos métodos de clusterización y distintos criterios de división
	- Soft vs hard clustering
	- Prototype vs density based
	- Partitional vs hierarchical clustering


# K-means
Esquema
Damos el número de clusters k que queremos obtener
Computa los centroides de cada cluster como el promedio de las features de sus samples
Le asigna a cada sample la etiqueta del cluster cuyo centroide es más cercano

Función objetivo 
Buena clusterización es la que minimiza la varianza entre datos de un mismo cluster
$$\min_{c_1, \dots, c_k} \sum_{k=1}^k \frac{1}{|C_k|}\sum_{i, i' \in C_k} \sum_{j=1}^p (x_{ij} - x_{i'j})^2$$

Básicamente K-means es un algoritmo de optimización de esta función objetivo
Depende de la inicialización -> modelo NO determinista


Elección del K:
 No es trivial elegir k en la mayoría de los dataset reales. No hay algún método que funcione siempre.
 - Método del codo
 - Coeficiente de Silhouette:
	 - edida de cuan similar es un dado dato a los datos de su cluster en comparación a los datos del cluster más cercano

Ventajas
+ Simple y fácil de implementar
+ Orden del algoritmo es lineal

Desventajas
- Depende de la inicialización
- TIende a caer en un mínimo local
- Sensible a aoutliers
- Los clusters tienen que tener forma esférica
- No se puede aplicar a data categórica


Clase 7: [[Análisis Factorial Exploratorio]]
