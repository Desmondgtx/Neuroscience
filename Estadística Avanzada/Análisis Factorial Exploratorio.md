
## Clase 7 de Estadística Avanzada

Clase 6: [[Modelos No Supervisados]]


## Conceptos Básicos

X = T + e

Donde:
X = Medida
T = True
e = error

- En muchos casos, especialmente en estudios psicométricos, las variables de un modelo no pueden medirse directmente
- Estas variables son denominadas "variables latentes" o "factores"
- Esto hace que la medición de una variable latente deba hacerse indirectamente de la medición de variables que reflejen a la variable latente
- Estas variables sutitutas se denominan *proxy variables* o indicadores
- La medición indirecta de las variables latentes a través de indicadores puede introducir mucho ruido a la medición


## Modelamiento de Ecuaciones Estructurales (SEM)

- La mejor forma de analizar un modelo en el cual se sospecha que las variables se han medido con ruido es usar un modeo estadístico que tome en cuenta lo anterior
- Los modelos y técnicas asociadas para hacer eso se conocen como *Structural Equation Modeling* (SEM)

Se distinguen dos modelos:
- Modelo de medición
- Modelo causal (de causa efecto)

- Una forma alternativa de cuantificar el error de medición de una variable latente es hacer uso de una medida que nos indique qué tan confiable es la medición
- Para ello, se usa el Alpha de Cronbach o Coeficiente $\alpha$

### Alpha de Cronbach
- Valor entre 0 y 1
- Nos indica qué porcentaje de la varianza de los indicadores es atribuible a la variable latente y NO a errores en la medición
- Por ejemplo: 
	- $\alpha = 0.70$ indica que el 70% de la varianza de los indicadores es realmente causada por la medición verdadera de la variable latente y  un 30% corresponde a error de medición
- En general un $\alpha$ mayor a 70 es aceptable

- Para calcular el coeficiente $\alpha$ se necesita tener, al menos, dos indicadores POR variable latente, y se calcula ocupando la siguiente fórmula:
$$\alpha = \frac{k}{k-1}[1- \frac {\sum \sigma_i²}{\sum \sigma_i² + 2 \sum Cov(i,j)}]$$
Donde:
k = Número de indicadores para una variable latente
$\sigma²$ Varianza del incidaor i
Cov(i,j) = Covarianza entre el indicador i y el indicador j


## Exploratory Factor Analysis (EFA)

- La idea fundamental es que algunas variables, pero no todas, pueden ser medidas directamente
- Las variables no observables son denominadas variables latentes o factores
- Se puede obtener información de las variables latentes al ver la influencia de las variables latentes sobre las observables
- EFA analiza la covarianza entre las variables observables, tratando de generar un número menor de variables latentes


### Suposiciones
- En EFA no se especifica la relación entre variables indicadoras (observables) y variables latentes (factores)
- Se asume que todas las variables observables están correlacionadas entre sí, aunque en diferentes grados
- Todos los factores están correlacionados
- Los errores entre variables no están correlacionados
- Todas las variables observadas están correlacionadas por uno o más variables
- Todos los factores no están correlacionados con los errores de las variables observables
- Para hacer un EFA, esto implica que debemos hacerlo sobre las variables observables que miden factores que no estén asociados causalmente entre sí


## Definiciones:

- **Variables latentes o constructos:** Variables que no pueden medirse de forma directa (típicas en estudios psicométricos), por lo que se infieren indirectamente a partir de otras variables que las reflejan. También se les llama "factores".
	- Ejemplos:
		- Eficiencia Mercaderistas
		- Commitment to Work
- **Indicadores:** Las variables observables (medibles directamente) que sirven como variables sustitutas o *proxy* de una variable latente.
	- Esta medición indirecta introduce ruideo (error de medición), que es justamente lo que el modelo $X = T + e$ busca separar.
	- Ejemplos:
		- Escala Likert
		- Preguntas sobre nivel educacional del hogar


## Reducción de Dimensionalidad

![[Captura de pantalla 2026-05-21 150220.png]]

El objetivo principal del EFA es **simplificar la estructura de los datos** transformando un conjunto de variables observadas en un número menor de **variables latentes o factores**. Este proceso se visualiza matemáticamente como la **proyección de vectores** de un espacio de alta dimensión a uno de menor dimensión.

- **Vectores de Respuesta:**
	- El vector za​ representa la respuesta estandarizada original de un sujeto en un espacio de "n" dimensiones (donde cada dimensión es un indicador). La reducción consiste en proyectar ese vector en un nuevo plano (espacio factorial), dando como resultado el vector proyectado $\hat{z}_a$​.
- **Error de Proyección (ϵ_a​):**
	- Al bajar la dimensión (por ejemplo, de 3D a 2D), se pierde información, lo que genera un vector de error (ϵ_a​). El EFA busca que este error sea el mínimo posible para que la simplificación represente fielmente los datos originales.
- **Cargas Factoriales o Loadings (la1​,la2​):**
	- Son las coordenadas o proyecciones del vector $\hat{z}_a$ sobre los ejes de los factores (F1​ y F2​). Estos valores indican qué tanto "carga" o refleja cada indicador a un factor específico.
- **Círculo Unitario (Unit Circle):**
	- Se utiliza como una restricción de normalización* donde la norma de los vectores se fija en 1. Esto permite que todas las respuestas estén en la misma escala, facilitando los cálculos matemáticos para minimizar la diferencia entre las correlaciones originales y las proyectadas.

En resumen, la reducción de dimensionalidad busca encontrar la **mínima cantidad de dimensiones (factores)** que expliquen la mayor cantidad de varianza de los indicadores originales, utilizando los loadings para interpretar la relación entre ellos.


Fórmulas:
$$Z_a = \sum_p l_{ap}F_p + \epsilon_a$$
$$\hat{r}_{ab} = \hat{z}_a * \hat{z}_b$$
Correlación entre respuesta proyectada del sujeto "a" y "b"

$$\epsilon² = \sum_{a,b \ne a} (r_{ab} - \hat{r}_ab)²$$
Minimizar el error entre correlación original y proyectada




Clase 8: [[Aplicación EFA]]