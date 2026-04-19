
## Clase 3 de Estadística avanzada

Clase 2: [[Modelos de Regresión]]


# Repaso Regresión Lineal
Regresión con una variable dependiente y una variable independiente
$$\hat{y} ∼ \hat{\beta_0} + \hat{\beta_1}*x_1$$

Regresión de multiples variables independientes: Regresión lineal múltiple
$$\hat{y} ∼ \hat{\beta_0} + \hat{\beta_1}x_1 + \ldots + \hat{\beta_n}x_n$$

Regresión de polinomios:

$$\hat{y} = \hat{\beta_0} + \hat{\beta_1}x^2 + \ldots + \hat{\beta_m}x^m$$


$\beta_0$ = Intercepto de todos los modelos
$\beta_n$ = Coeficiente regresor de la variable $n$


Los parámetros se encuentran minimizando la suma del cuadrado de los residuos:
$$RSS = \sum_i (y_i - \hat{y}_i)^2$$

Regresión de funciones de base
$$y = \beta_0 + \beta_1\phi_1(\bar{x}) + \beta_2\phi_2(\bar{x}) + \ldots + \beta_m\phi_m(\bar{x})$$

## Concepto de coeficientes
Si al polinomio del modelo aumentamos el coeficiente, podemos sobreajustar para estimar con alta precisión el modelo
Si el polinomio aumenta el coeficiente, tendrá baja replicabilidad con otros datos


##  Sub ajuste y sobre ajuste

![[Captura de pantalla 2026-04-19 122211.png]]

Sub Ajustar:
- No se logra captar la variabilidad de los datos
- El modelo queda corto

Sobre Ajustar:
- La estimación es perfecta en los datos
- NO puede predecir o ajustar a nuevos datos


## Sesgo y Varianza:
Fórmula:
$$Y = f(X) + \epsilon$$
Y =  Datos observados
$f$ = función objetivo
$\epsilon$ = ruido en los datos

Error esperado
$E[y_0 - \hat{f}(x_0)]^2 = E[f(x_0) + \epsilon_0 - \hat{f}(x_0)]^2$
$E[y_0 - \hat{f}(x_0)]^2 = E[f(x_0) - \hat{f}(x_0)]^2 + Var(\epsilon)$
$E[y_0 - \hat{f}(x_0)]^2 = \ldots$

$(E[\hat{f}(x_0)] - y_0)^2$ = Sesgo
$E[\hat{f}(x_0) - E[\hat{f}(x_0)]^2$ = Varianza
$Var(\epsilon)$ = Error no reducible


### Sesgo
Fórmula: 
$(E[\hat{f}(x_0)] - y_0)^2$

- Es el error sistemático de nuestras predicciones
- Si aujustamos nuestro modelo en distintos dataset, ¿Cuanto varía el valor de mis predicciones?


### Varianza
Fórmula:
$E[\hat{f}(x_0) - E[\hat{f}(x_0)]^2$

- Cuanto fluctúa mi predicción


### Ejemplo gráfico
![[Captura de pantalla 2026-04-19 123048.png]]



## Regularización
- Cualquier modificación al proceso de entrenamiento que nos permita plasmar ciertas características en el modelo
- Consiste en prevenir que los coeficientes no adeopten valores muy altos para sobre ajustar
- Fórmula:
$$RSS = \sum_i (y_i - \hat{y}_i)^2 + \alpha \sum_{j=1}^M |\hat{\beta}_j|^q$$
Donde:
$\sum_i (y_i-\hat{y}_i)^2$ = Suma de los errores cuadrados
$\sum_{j=1}^M |\hat{\beta}_j|^q$ = término de penalización
$\alpha$ = Parámetro a tunear (hiperparámetro)


q = 2 (ridge regression): Proceso de minimización es parecido al de cuadrados mínimos
q = 1 (lasso regression): Para valores altos de $\alpha$, fuerza a que muchos coeficientes vayan a 0. Actúa como un *selector de variables más importantes*


### Ejemplo de regularización:
- Data Augmentation: se altera un poco los datos para que sea más robusto ante perturbaciones

![[Imagen1.jpg]]


### Determinar alpha:
- Nos permite que el modelo sea más simple y previene el sobre ajuste
![[Captura de pantalla 2026-04-19 123901.png]]


### Estimar hiper-parámetros
 - La elección del grado del polinomio y el parámetro se deben hacer con cuidado, 
 - Objetivo:
	 - Bajo sesgo
	 - Baja varianza
- Técnicas:
	- Separación de datos de testeo y entrenamiento
	- Validación cruzada




Clase 4:  [[Regresión Múltiple]]