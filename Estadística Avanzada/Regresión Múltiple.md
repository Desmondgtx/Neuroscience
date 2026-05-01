
## Clase 4 de Estadística Avanzada

Clase 3: [[Regresión No Lineal]]


# Regresión Logística
Motivación:
- Tenemos $x_1$ y $x_2$ como variables

Función como la PROBABILIDAD de encontrar Y entre 0 y 1

Función sigmoidea:
$$P(y|x,\beta) = \frac{1}{1+e^{-(\beta_0 + \beta_1*x)}}$$


### La frontera de decisión
Probabilidad de corte = 0.5

y = 1, cuando $P(y1x,\beta) \geq 0.5$
y = 0, cuando $P(y|x, \beta) < 0.5$

$P(y|x, \beta) = 0.5$
$beta_0 + beta_1 * x_{corte} = 0 => x_{corte} = -\frac{\beta_0}{\beta_1}$


#### Más de un feature o característica
$$P(y|x,\beta) = \frac{1}{1+e^{-(\beta_0 + \beta_1*x_1^c+\beta_2*x_2^c)}} = 0.5$$

$$\beta_0 + \beta_1*x_1^c+\beta_2*x_2^c = 0 => x_2^c = -\frac{(\beta_0+\beta_1*x_1^c)}{\beta_2}$$


### Búsqueda de coeficientes - máximaverosimilitud
EN VEZ DE cuadrados minimos, utilizamos el concepto de probabilidad
Buscamos minimizar el producto de probabilidades de que a cada punto se le asigne la categría correcta

$$l(\beta) = \prod_{i, y = 1} P(y|x,\beta) \prod_{i', y = 0} [1-P(y|x,\beta)]$$

#### Clasificación múltiple:
- Cuando tengo más de dos variables o features
	- Aproximación uno contra todos:
		- A o no A
		- B o no B
		- C o no C
		- $\max_{j =A,B,C} {P_j(y|x, \beta_j)}$


#### Problemas de regresión y clasificación
n = variables independientes (features)
k = samples
y = la variable dependiente (target) puede ser 0 o 1 (clasificación)

Por medio de una función de distancia, la diferencia entre target y targets estimados 
(función de costo o pérdida)
$$d((y_1, \dots, y_k), (\widetilde{y}_1, \dots, \widetilde{y}_k)) = L(\beta_1, \dots, \beta_2)))$$

- Si m (número de parámetros es grande), puedo hacer que la función de costo sea chica sobreajustando los datos
- Dos soluciones posibles: 
	- Regularización ridge 
$(\widetilde{\beta}_1, \dots, \widetilde{\beta}_m) = argmin(L(\beta_1, \dots, \beta_m)+C \sum_{j=1}^m \beta_j^2$
	- Regularización lasso
$(\widetilde{\beta}_1, \dots, \widetilde{\beta}_m) = argmin(L(\beta_1, \dots, \beta_m)+C \sum_{j=1}^m |\beta_j|$


Diferencia entre estadística y machine learning
- Número de parámetros
	- Estadística suele tener pocos parámetros (fácil de interpretar)
	- Machine Learning tiene miles de parámetros (difícil de interpretar)


Cosas que se pueden elegir:
- El modelo $f$
- La función de pérdida L (determinada al modelo)
- Determinar C
- Determinar la performance del modelo
- Preparar los features para el modelo


### Accuracy
Como determinar la performance del modelo

$$Acc = \frac{1}{k}\sum_{i=1}^k |\widetilde{y_i}-y_i|$$
Accuracy: cantidad de veces que el label estimado es crorecto sobre cantidad total de samples

Valor aceptable de Accuracy
acc = 1, todos los labels estimados correctamente
acc = 0, ningún label estimado correctamente
acc = 0.5, valor que obtengo al azar si las clases son balanceadas


### Ejemplo:
Detectar una enfermedad genética muy rara (1 en un millón)
Test de entrenamiento: 999.999 negativos, 1 positivo

acc = 0.999999

Este modelo predice que NADIE tiene la enfermedad


### Entrenamiento de datos:
Train-test split (segmentar los datos)
70% de mis datos para entrenar
30% de mis datos para evaluar y testear el modelo


### Especificidad y sensibilidad
![[Especificidad y Sensibilidad.png]]


### Esquema general para un problema de clasificación
![[Imagen1 1.jpg]]



Clase 5: [[Optimización de parámetros]]