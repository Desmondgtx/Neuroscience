
## Clase 8 de Estadística Avanzada

Clase 7: [[Análisis Factorial Exploratorio]]


## Medición de Indicadores

- Se miden a través de encuestas y datos categorizados
- Los datos continuos deben categorizarse, ya que no podemos combinarlos con datos categóricos

### Técnicas a emplear
- EFA
	- Reducción de dimensionalidad usando:
		- Principal Axis Factoring (PAF)
		- Maximum Likelihodd (ML)
- Coeficiente $\alpha$ de Cronbach
- Ecuación de regresión lineal usando método OLS


## Principal Axis Factoring (PAF)

### Definición
El PAF es un método de extracción que busca identificar las **variables latentes** o factores que subyacen a los indicadores observados. Su funcionamiento se basa en los siguientes puntos:
- **Enfoque en la varianza común:** El PAF solo analiza la **varianza compartida** entre los indicadores (covarianza), ignorando la varianza única de cada ítem y el error de medición.
- **Reducción de dimensionalidad:** Proyecta las respuestas originales de un espacio de alta dimensión (n indicadores) a uno de menor dimensión (pocos factores).
- **Procedimiento matemático:** Utiliza **autovalores (eigenvalues)** y **autovectores** para encontrar los ejes (factores) que maximizan la explicación de la información en la matriz de correlaciones.
- **Minimización del error:** El algoritmo busca que la diferencia entre las correlaciones originales y las correlaciones proyectadas (reducidas) sea la mínima posible.


### Diferencias entre PAF y PCA
Aunque ambos se utilizan para simplificar datos, sus objetivos y supuestos estadísticos son distintos:

|Característica|Principal Component Analysis (PCA)|Principal Axis Factoring (PAF)|
|---|---|---|
|**Objetivo Principal**|**Reducción de datos:** Resumir mucha información en pocos componentes para facilitar el manejo de datos.|**Identificación de constructos:** Descubrir las variables latentes que causan las respuestas observadas.|
|**Tratamiento de la Varianza**|Considera la **varianza total** de los indicadores como información útil.|Solo considera la **varianza común** (compartida entre ítems).|
|**Error de Medición**|Asume que los indicadores no tienen error o no los separa de la información principal [implícito en 63].|Asume explícitamente que X=T+e (la medición está contaminada por ruido o error).|
|**Relación Causal**|Los componentes son simples resúmenes matemáticos de los ítems.|Se postula que el **factor causa** la respuesta en el indicador (flechas del óvalo al rectángulo).|
|**Uso Preferente**|Cuando el interés es puramente descriptivo o técnico (reducir variables).|Cuando se desea validar una **teoría psicométrica** o probar la existencia de un constructo.|

#### Resumen para Obsidian
- **PCA** es una técnica de **síntesis matemática**: toma los ítems y los "empaqueta" para que ocupen menos espacio, sin importar qué parte es error y qué parte es real.
- **PAF** es una técnica de **modelamiento teórico**: trata de "limpiar" el ruido de los indicadores para encontrar la variable latente verdadera (T) que está detrás de ellos.


### Otras métricas:
- Para KMO Test: 
	- Debe ser menor a 0.5 o 0.6
	- Indica la proporción de varianza en los datos que no es común a todos los posibles factores
- Para Bartlet's Test:
	- $H_0$: Todas las correlaciones entre variables osn cero
	- $H_A$: Al menos una correlación es distinta a 0


### Eigenvalues
En el contexto del **Análisis Factorial Exploratorio (EFA)** y específicamente del **Principal Axis Factoring (PAF)**, la relación con los **eigenvalues** (o autovalores) es fundamental, ya que estos sirven como la métrica principal para determinar la estructura del modelo.

![[Captura de pantalla 2026-05-22 134905.png|504]]

#### Qué representan los eigenvalues
Los eigenvalues son valores numéricos que **cuantifican la cantidad de información (varianza)** que explica cada factor extraído de la matriz de correlaciones.

- **A mayor eigenvalue**, mayor es la cantidad de varianza de los indicadores originales que ese factor es capaz de resumir.
- En términos matemáticos, se obtienen al resolver la ecuación característica de la matriz de varianza-covarianza (Σa=λa), donde λ representa el eigenvalue.

#### Para qué se usan
Los eigenvalues se utilizan principalmente para **decidir cuántos factores extraer**:

- **Regla de Kaiser (λ≥1.0)**: Es el criterio empírico más común. Se considera que un factor es relevante y debe ser extraído solo si su **eigenvalue es mayor o igual a 1.0**. Esto indica que el factor explica al menos tanta varianza como un único indicador original estandarizado.
- **Gráfico de Sedimentación (Scree Plot)**: Se grafican los eigenvalues de todos los factores posibles. Los investigadores buscan el **"codo" o punto de quiebre** en la curva; los factores por encima de ese codo son los que tienen eigenvalues significativos y son los que se conservan.
- **Identificación de Dimensiones Ortogonales**: Cada eigenvalue está asociado a un vector propio (eigenvector). En el PAF, esto se usa para asegurar que los factores extraídos sean **ortogonales (a 90 grados)**, lo que significa que la información que aporta cada factor es independiente y no redundante.
- **Soporte a la Teoría**: Si tú postulas que existen, por ejemplo, dos constructos (como "percepción de armas" y "eficacia policial"), esperas que el análisis de los datos arroje exactamente **dos eigenvalues mayores a 1.0**. Si los datos no alcanzan este valor, el investigador a veces debe "forzar" la extracción basándose en la teoría, aunque esto es estadísticamente menos robusto que dejar que los datos "hablen" a través de sus eigenvalues.

En resumen, los eigenvalues son el termómetro que te dice **qué tan "fuerte" o informativo es un factor** y te permite justificar cuántas variables latentes realmente subyacen a tus indicadores observados.



## Maximum Likelihood (ML)
Es un método de extracción de factores alternativo a la Factorización de Ejes Principales (PAF).

- **Funcionamiento:** Busca encontrar la solución factorial que tenga la **máxima probabilidad** de haber generado la matriz de correlaciones observada en la muestra.
- **Ventaja clave:** A diferencia del PAF, el método ML proporciona un **test de bondad de ajuste** (basado en el estadístico Chi-cuadrado). Este test evalúa la hipótesis de si se han extraído suficientes factores o si podrían existir más dimensiones relevantes en los datos.
- **Uso:** Aunque el PAF es más común en psicología, muchos investigadores prefieren el ML por la solidez estadística que aporta su prueba de ajuste, aunque ambos suelen arrojar conclusiones muy similares.


### Rotación Varimax
Es un "truco" matemático o procedimiento de post-extracción utilizado para hacer que los resultados sean interpretables.

- **Objetivo:** Resolver el problema de los indicadores que "cargan" (tienen proyecciones similares) en múltiples factores al mismo tiempo.
- **Mecanismo:** Rota los ejes de los factores de forma que se **maximice la varianza** (la carga) de un indicador en un eje específico y se minimice en los demás.
- **Resultado:** Crea un contraste claro en la **Matriz de factores rotados**. Esto permite identificar visualmente qué grupo de indicadores pertenece a qué constructo (por ejemplo, ver que los ítems PUA_1, 2 y 3 cargan alto en el Factor 1 y casi nada en el Factor 2).



## Ecuaciones de Regresión
En el contexto de este curso, la regresión lineal se utiliza para probar el **modelo causal** tras haber validado el modelo de medición mediante el Análisis Factorial Exploratorio (EFA). Su propósito es examinar el conjunto de relaciones entre una o más variables independientes (IV) y una variable dependiente (DV).


### El Modelo de Regresión
El análisis busca encontrar la mejor línea (o superficie) que represente la influencia de las variables predictoras sobre la respuesta, minimizando el error cuadrático.
- **Variables Independientes (IV):** Actúan como predictoras o causas.
- **Variable Dependiente (DV):** Es la respuesta o variable predicha.


### Coeficientes de Regresión
Es fundamental distinguir entre los dos tipos de coeficientes que entrega el análisis:
- **Coeficientes No Estandarizados (B):**
    - Permiten examinar los efectos usando la **escala original de medición** (ej. de 1 a 7).
    - **Interpretación:** Un incremento de una unidad en la IV produce un cambio de "B" unidades en la DV.
- **Coeficientes Estandarizados (β o Beta):**
    - Se calculan llevando los datos a una media de 0 y desviación estándar de 1.
    - **Interpretación:** Permiten comparar la **magnitud relativa** de los efectos entre diferentes variables del mismo modelo o entre estudios distintos, ya que son independientes de la escala original.


### Relevancia en SEM
La regresión es la base del **modelo estructural** en SEM. A diferencia de la regresión simple por OLS (que usa promedios de indicadores), el modelo SEM completo integra las regresiones con los errores de medición identificados en el EFA/CFA para obtener estimaciones más "verdaderas" y libres de ruido.



## Conclusiones
### EFA
- Indicadores miden adecuadamente las variables:
	- Varianza explicada = 58.5%
	- No hay cross-loadings muy grandes
	- Alpha de Cronbach aceptables
	- Según ML pueden baer más de dos factores

### Ecuaciones de regresión
- Se cumple relación entre variable dependiente y variables independientes
	- Eficiencia Mercaderistas y Operaciones Logísticas explican el 73% de la varianza de Reposición Eficiente
	- El modelo es estadísticamente significativo
	- Eficiencia Mercaderistas y Eficiencia Logísticas tienen coeficientes estadísticamente significativos
- Relación entre Reposición eficiente y variables independientes
	- En promedio, al aumentar la evaluación de Eficiencia Mercaderistas en un punto, la evaluación de Reposición Eficiente aumente en 0.2 puntos
	- En promedio, al aumentar la evaluación de Eficiencia Operaciones Logísticas en un punto, la evaluación de Reposición Eficiente aumente en 0.48 puntos
	- Parece que la Eficiencia Operaciones Logísticas es más importante que Eficiencia Mercaderistas para obtener una Reposición Eficiente



## Tarea EFA
[[Tarea EFA]]


Clase 9: [[Modelamiento de Ecuaciones Estructurales]]