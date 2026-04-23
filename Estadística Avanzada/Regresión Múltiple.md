
# Clase 4 de Estadística Avanzada

Clase 3: [[Regresión No Lineal]]


##  Regresión Logística

Motivación:
- Tenemos $x_1$ y $x_2$ como variables

Función como la PROBABILIDAD de encontrar Y entre 0 y 1

Función sigmoidea:
$$P(y|x,\beta) = \frac{1}{1+e^{-(\beta_0 + \beta_1*x)}}$$



### La frontera de decisión
probabilidad de corte = 0.5

y = 1, cuando $P(y1x,\beta) \geq 0.5$
y = 0, cuando $P(y|x, \beta) < 0.5$


$$P(y|x,\beta) = \frac{1}{1+e^{-(\beta_0 + \beta_1*x_1^c+\beta_2*x_2^c)}}$$

$\beta_0 + \beta_1*x_1^c+\beta_2*x_2^c = 0 => x_2^c = -(\beta_0+\beta_1*x_1^c)$



### búsqueda de coeficientes - máximaverosimilitud

EN VEZ DE cuadrados minimos, utilizamos el concepto de probabilidad
buscamos minimizar el producto de probabilidades de que a cada punto se l e asigne la categría correcta

$$l(\beta) = \prod_{i, y = 1} P(y|x,\beta) \prod_{i', y = 0} [1-P(y|x,\beta)]$$


clasificación múltiple:

- cuando tengo más de dos variables o features
	- Aproximación uno contra todos:
		- A o no A
		- B o no B
		- C o no C
		- $\max_{j =A,B,C} {P_j(y|x, \beta_j)}$




n = variables independientes (features)
k = samples
y = la variable dependiente (target) puede ser 0 o 1 (clasificación)


$d((y_1, \dots, y_k), (\widetilde{y}_1, \dots, \widetilde{y}_k)) = L(\beta_1, \dots, \beta_2)))$



Si m (número de parámetros es grande), puedo hacer que la función de costo sea chica sobreajustando los datos
Vimos dos soluciones posibles: 
- regularización ridge 
$(\widetilde{\beta}_1, \dots, \widetilde{\beta}_m) = argmin(L(\beta_1, \dots, \beta_m)+C \sum_{j=1}^m \beta_j^2$

- regularización lasso
$(\widetilde{\beta}_1, \dots, \widetilde{\beta}_m) = argmin(L(\beta_1, \dots, \beta_m)+C \sum_{j=1}^m |\beta_j|$


diferencia entre estadística y machine learning
- número de parámetros
	- Estadística suele tener pocos parámetros
	- Machine Learning tiene miles de parámetros


Cosas que se eligen:
El modelo $f$
La función de pérdida L (determinada al modelo)
Determinar C
Determinar la performance del modelo
Preparar los features para el modelo


como determinar la performance del modelo

$$Acc = \frac{1}{k}\sum_{i=1}^k |\widetilde{y_i}-y_i|$$
accuracy: cantidad de veces que el label estimado es crorecto sobre cantidad total de samples

acc = 1, todos los labels estimados correctamente
acc = 0, ningún label estimado correctamente
acc = 0.5, valor que obtengo al azar si las clases son balanceadas


### Ejemplo:
detectar una enfermedad genética muy rar (1 en un millón)
test de entrenamiento: 999.999 negativos, 1 positivo

acc = 0.999999





entrenamiento de datos:
train-test split
70% de mis datos para entrenar
30% de mis datos para evaluar y testear el modelo



### Especificidad y sensibilidad








tarea:
cambiar datos y demás
