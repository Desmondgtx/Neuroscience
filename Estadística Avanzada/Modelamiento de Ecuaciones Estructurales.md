
## Clase 9 de Estadística Avanzada

Clase 8: [[Aplicación EFA]]


## EFA vs SEM
Las diferencias entre el **Modelamiento de Ecuaciones Estructurales (SEM)** y el **Análisis Factorial Exploratorio (EFA):**
- **EFA (Exploratorio):** Es una técnica mayoritariamente **ateórica o empírica** que se utiliza para explorar cuántas variables latentes (factores) subyacen a un conjunto de indicadores. Se deja que los "datos hablen" para agrupar los indicadores en la menor cantidad posible de factores.
- **SEM (Confirmatorio):** Es una técnica utilizada para **verificar o confirmar una teoría** basada en un diseño exacto y explícito. A diferencia del EFA, obliga al investigador a tener un conocimiento previo del fenómeno para probar hipótesis de relaciones específicas


## SEM
- Structural Equation Modeling (SEM), es una combinación de técnicas estadísticas, tales como EFA y regresiones múltiples
- El propósito de SEm es examinar un conjunto de relaciones entre una o más variables independientes (IV) y una o más variables dependientes (DV)
- Cada variable independiente o dependiente puede ser continua o discreta
- Las variables independientes son consideradas usualmente como variables predictoras o causales, ya que predicen o causan a las variables dependientes

### Path Analysis
- SEM está muy ligado a Path Analysis (PA)
- Una vez que se obtienen los datos, el PA se efectua haciendo lo siguiente
	- Dibujar un diagrama de PA según su teoría
	- Estimar los parámetros del modelo correspondiente
	- Comparar los parámetros estimados con la teoría
	- Comparar los parámetros estandarizados con otros estudios
	- Si es necesario, modificar el modelo y volver a ejecutar los pasos previos

#### Suposiciones teóricas:
- Causalidad:
	- $X_1$ e $Y_1% están correlacionadas
	- $X_1$ precede cronológicamente a $Y_1$
	- $X_1$ e $Y_1$ están relacionadas incluso después de controlar por otras variables

#### Suposiciones estadísticas:
- Modelo debe ser recursivo
- Se puede usar datos ordinales

#### Tipos de relaciones:
- **Relación de covarianza:**
	- Una variable COVARÍA con otra no indica necesariamente causalidad
- **Relación espúrea:**
	- Una variable covaría con otra, pero noe stán directametne relacionadas ni una causa a la otra
- **Relación de causalidad:**
	- Una variable causa a otra y no es recursiva (efecto es en un solo sentido)
- **Relación de causalidad con efectos directos e indirectos:**
	- Una variable afecta a otra directamente Y a través de un mediados
- **Relación de causalidad con efecto moderador:**
	- Una variable afecta a otra a través de un mediados
- **Relación de causalidad recursiva:**
	- Tiene causalidad y efecto de forma bidireccional


### Coeficientes:
Indican los efectos directos e indirectos.
Pueden ser:
- Estandarizados ($\beta$)
- No estandarizados (B)

Los coeficientes no estandarizados B permiten examinar los efectos usando la escala original de medición
$$SD = \sqrt{\frac{\sum(x-\bar{x})^2}{N-1}}$$



Clase 9: [[Conceptos SEM]]