
## Clase 3 de Estadística avanzada

Clase 2: [[Modelos de Regresión]]


# Repaso Regresión Lineal
Regresión con una variable dependiente y una variable independiente

$$\hat{y} = \hat{\beta_0} + \hat{\beta_1}*x_1$$

Regresión de multiples variables independientes: Regresión lineal múltiple

$$\hat{y} = \hat{\beta_0} + \hat{\beta_1}x_1 + \ldots + \hat{\beta_n}x_n$$


Regresión de polinomios:

$$\hat{y} = \hat{\beta_0} + \hat{\beta_1}x^2 + \ldots + \hat{\beta_n}x^m$$


$\beta_0$ = Intercepto de todos los modelos
$\beta_n$ = Coeficiente regresor de la variable $n$


Los parámetros se encuentran minimizando la suma del cuadrado de los residuos:
$$RSS = \sum_i (y_i - \hat{y}_i)^2$$

Regresión de funciones de base
esquema general

$$y = \beta_0 + \beta_1\phi_1(x) + \beta_2\phi_2(x) + \ldots + \beta_m\phi_m(x)$$



sub ajustar y sobre ajustar:
malas predicciones





sesgo y varianza:

$$Y = f(X) + \epsilon$$
Y =  Datos observados
$f$ = función objetivo
$\epsilon$ = ruido en los datos

Error esperado
$E[y_0 - \hat{f}(x_0)]^2 = E[f(x_0) + \epsilon_0 - \hat{f}(x_0)]^2$
$E[y_0 - \hat{f}(x_0)]^2 = E[f(x_0) - \hat{f}(x_0)]^2 + Var(\epsilon)$
$E[y_0 - \hat{f}(x_0)]^2 = \ldots$

$(E[\hat{f}(x_0)] - y_0)^2$ = Sesgo
Varianza
$Var(\epsilon)$ = Error no reducible

$$
$$


random forest





## Regularización
modificación al proceso de entrenamiento que nos permita plasmar ciertas características en el modelo


$$RSS = \sum_i (y_i - \hat{y}_i)^2 + \alpha \sum_{j=1}^M |\hat{\beta}_j|^q$$
$\alpha$ = Parámetro a tunear (hiperparámetro)
$\alpha \sum_{j=1}^M |\hat{\beta}_j|^q$ = término de penalización

q = 2 (ridge regression): deja a la función minimizar cuadrática
q = 1 (lasso regression): 




data augmentation


determinar alpha





como estimamos hiper-parámetros
 - La elección del grado del polinomio y el parámetro se deben hacer con cuidado, 
 - Objetivo:
	 - Bajo sesgo
	 - Baja varianza
- Técnicas:
	- Separación de datos de testeo y entrenamiento
	- Validación cruzada





