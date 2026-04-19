
## Clase 2 de Estadística avanzada
Clase 1: [[Conceptos Básicos]]

### Fórmula
$Y = f(X) + \epsilon$  

Donde:

Y = variable dependiente
X = variable independiente (grupos experimentales, condiciones experimentales, etc)
$\epsilon$ = ruido de los datos


### ¿Para qué sirven los modelos de regresión?

#### Predicción
$Y = f(X) + \epsilon$  
Tipicamente no nos interesa la forma de f(), ni su simplicidad, siempre que pueda demostrar que la predicción funciona

#### Inferencia
$Y = f(X) + \epsilon$  
Interpretar la función f() y entender la relación entre X e Y
¿Todas las variables X importan para determinar Y?
¿Cómo es la relación entre las variables X e Y? (creciente, decreciente, etc)

##### Ejemplo
Y = cantodad de ventas d eun producto (solo un dato)
X = 
	- precio de venta
	- Inversión en publicidad
	- Precio de venta de la competencia
	- Unidades vendidas por la competencia


### Estadística descriptiva vs Inferencia
Estadística descriptiva:
- Caracterización de los datos

Inferencia:
- Generalizaciones y predicciones 


### Ejemplo
#### Titanic

La fragilidad del acero (medida como la energía de un golpe necesaria para romperlos) depende de la temperatura

Medimos la fragilidad (F) de una pieza de acero y medimos la temperatura de dicha pieza (T)

![[Captura de pantalla 2026-04-07 212851.png]]


### Correlación lineal o de Pearson:
#### Fórmula:
$$x = 1/n \sum_{i=1}^n x_i$$
#### R
$$r = cos(a) = \frac{\sum_{i=1}^N(x_i - x)*(y_i-y)}{\sqrt{\sum_{i=1}^N(x_i - x)^2}*\sqrt{\sum_{i=1}^N(y_i - y)^2}}$$


### Tipos de correlaciones
![[Captura de pantalla 2026-04-07 213921.png]]

Correlación positiva: directamente proporcional
Correlación negativa: inversamente proporcional


### Cuarteto de Anscombe
Misma correlación, distintas relaciones funcionales

![[Cuarteto de Anscombe.jpg]]


### Correlación de Spearman
- Variante NO PARAMETRICA de la correlación lineal (de Pearson)
- Se ordenan los valores y se otorga un rango a cada valor


### Dimensiones
![[Dimensionalidad.png]]

- Correlación de dos variables (2 dimensiones)
- Correlación de tres variables (3 dimensiones)


### Datos y resultados

#### Error estimativo
$$e_i = y_i - y_i$$
Diferencia entre el valor estimado y el valor real

#### Suma de residuos (RSS)
$$RSS = e_i^2+e_2^2+...+e_n^2$$

Mientras más pequeños los residuos, mejor el modelo reproduce y se ajusta a los datos


Se busca el mínimo local para minimizar la suma de los errores cuadráticos y reducir los residuos

![[Imagen1.png]]

*95% de la confianza:* si hago un experimento 100 veces o tomo 100 muestras, el 95% caerá en los resultados que tengo


### Limitaciones de la regresión lineal

#### Cuando la relación entre los datos es lineal
-  Si no es el caso, vemos que los residuoas resultan en una curva no-lineal
- Las regresiones no suelen funcionar en series de tiempo

#### Los errores no están correlacionados
- Esto suele suceder con series de tiempo con correlaciones temporales
- En ese caso, los intervalos de confianza exageran la probabilidad de que los parametros se encuentren en los intervalos

#### La varianza del termino de error es constante
- Esto puede ocurrir si el error depende de la magnitud de la variable. tipicamente el error depende logarítmicamente
- Puede resolverse usanco cuadrados mínimos pesados

#### Outliers
- Podemos detectarlos desde un gráfico
- Se pueden eliminar aplicando algún criterio (N desvíos estandar de la media)

#### Las variables dependientes no son colineales
- En caso de que las variables independientes muestren correlaciones altas, va a haber problemas a la hora de estimar los parámetros. En la práctica, con dos variables correlacionadas, el gráfico del error medio al cuadrado deja de tener un único mínimo y empieza a tener un mínimo en una región extensa del plano


### Tarea

- Ajustar un modelo de regresión
- Visualizar residuos
- Visualizar modelo con intervalo de confianza (R^2, p valor, etc)


Clase 3: [[Regresión No Lineal]]
