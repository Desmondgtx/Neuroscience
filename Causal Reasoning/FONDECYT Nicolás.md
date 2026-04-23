#  Conociendo las causas de las fallas sitemáticas en el razonamiento causal mediante la comparación de modelos computacionales cognitivos


Violaciones sistemáticas ([[Markov Violations]]) a los supuestos y reglas normativas de las Redes Bayesianas ([[Causal Bayes Nets]])

### Explicaciones existentes

Distintas explicaciones para este fenomeno;
1) **Basadas en heurísticos:** Explicación por atajos mentales, se asume que las personas consideran únicamente los estados prototípicos (presencia/ausencia) de los atributos, y no la probabilidad en su relación causal. Basados en estudios clásics de Kahneman y Tversky (1974)
2) **Recursos cognitivos limitados:** Se asume que las personas no logran obtener un muestreo completo de los atributos, lo cual es computacionalmente desgastante, sesgando sus juicios a los atributos disponibles en memoria explícita. Por lo tanto, las personas realizan un proceso de muestreo, tomando como punto de partida uno de los dos estados prototípicos (000 o 111), luego la búsqueda se mueve paso a paso alterando cada uno de los atributos. 
-  LAS FALLAS en el razonamiento causal ocurriría debido a que las personas no tienen las capacidades cognitivas suficientes para obtener una muestra completa, sesgando las estimaciones probabilísticas de la inferencia.
-  El tiempo que tardó y la precisión de la respuesta son **parámetros** que nos da la cantidad de sampleo que utilizó para responder
-  En teoría el muestreo debería ser aleatorio, mutando entre lo estados vistos y no vistos
3) **Incerteza y conocimiento previo:** Se asume que las personas utilizan información exógena a los atributos, lo que aumenta la desconfianza sobre el modelo causal normativo. Por lo que las personas agregarían conocimientos previos y propios cuando se enfrentan a tareas de razonamiento causal. Incluyen sus propios cómputos inferenciales

### Modelos Computacionales

1) **Modelo de Prototipos Duales:** Basado en heurísticos:
2) **Modelo de Muestreo:** Basado en modelos de recursos cognitivos limitados
3) **Modelo de Incerteza Generalizada:** Basado en incerteza del modelo causal
-  Este último modelo debería ser capaz de capturar las manipulaciones experimentales, logrando gradualidad en los juicios.
-  Los dos primeros modelos deberían ser insensibles a las manipulaciones

**Comparación de modelos:**
1) AIC:
2) BIC: 

Judea Pearl (Pearl, 2000) propuso las redes Bayesianas como una explicación normativa y matemática de cómo se realizan inferencias causales en relaciones probabilísticas. Estas Redes Bayesianas tiene dos particularidades para las representaciones causales:
1) Permiten diagramar las relaciones causales mediante el uso de modelos gráficos y/o pictóricos. Los atributos son nodos y las relaciones causales son aristas.
Cause     ->     Effect
   A         M        B       (Parameters)
2) Permiten establecer relaciones causales probabilísticas entre las entidades involucradas mediante la computación de la distribución conjunta.

### Gráficas de las Redes Causales Bayesianas
1) **Causa común:** B <- A -> C => $P(A, B, C) = P(C|A)*P(B|A)*P(A)$
2) **Cadena causal:** A -> B -> C => $P(A, B, C) = P(C|B)*P(B|A)*P(A)$
3) **Efecto común:** A -> C <- B => $P(A, B, C) = P(C|A,B)*P(A)*P(B)$

### Fallos sistemáticos en el razonamiento causal

1) Violación a la condición de Markov ([[Markov Violations]]):
-  Ocurre cuando las personas consideran atributos de un concepto que no son descendientes directos del atributo que necesitan inferir. Por ejemplo:
	- Estructura de cadena causal (A -> B -> C): Las personas estarían contemplando la primera variable A, para el cómputo de la probabilidad de la variable C, donde solo se debería considerar el padre directo, en este caso la variable B
	- Estructura de causa común (B <- A -> C ): Para el cómputo de la variable C, se considera también la presencia o asusencia de la variable B, donde solo se debería considerar el padre directo, en este caso la variable B
2) Insuficiencia en el descuento:
-  Ocurre cuando en una estructura de efecto común (A -> C <- B) las personas no descuentan una de las causas cuando la otra causa está presente (si A está presente, esto debería descontar la presencia de B)
3) Causas correlacionadas: 
-  En un modelo de efecto común (A -> C <- B), las dos causas deberían ser interpretadas como independientes entre sí, pero las personas las computan como relacionadas entre sí, influyendo en los cálculos de presencia o ausencia de cada una de ellas

### Formalizaciones computacionales de las explicaciones

#### NOISY-OR

Los modelos de razonamiento causal consideran que la causa es generativa de un efecto, y que ambas variables no son aisladas, sino que el efecto es dependiente del estado de la causa (presente o ausente, 1 o 0). Para ello, se emplea la función noisy-OR para causas generativas, siguiendo el marco normativo de las RB, donde:
$$P(E│c_1…c_n )=1-(1-b){∏_{c_i}^n}(1-m)^{c_i}$$
Donde:
- E = El efecto que queremos predecir
- $c_i$ = El estado de la causa (1 = presente, 0 = ausente)
- m = La relación causal, probabilidad de que la causa produzca el efecto cuando la causa está presente (valor de 0 a 1)
- b = Probabilidad base del efecto 
- n = Número de causas
- $P(E | c_1 ... c_n)$ = Probabilidad de un efecto (E) de ser generado por una causa ($c_i$)

La función noisy-OR es INCAPAZ de predecir los fallos sitemáticos del razonamiento causal

##### **Ejemplos:**

**Estructura de causa común: (Y1 <- X -> Y2)**

Dado:
- $c_x$ = 0.75 (probabilidad de base X)
- m = 0.75 (fuerza causal)
- b = 0.20 (causas de base)

**Cálculo de $P(Y_1 = 1 | X = 1)$:**

P(Y₁ = 1|X = 1) = 1 - (1 - 0.20)(1 - 0.75)¹
            = 1 - (0.80)(0.25)
            = 1 - 0.20
            = 0.80

**Cálculo de $P(Y_1 = 1 | X = 0):$

P(Y₁ = 1|X = 0) = 1 - (1 - 0.20)(1 - 0.75)⁰
            = 1 - (0.80)(1)
            = 1 - 0.80
            = 0.20


**Estructura de efecto común: (Y1 -> X <- Y2)**

Dado:
- $c_i$ = 0.75
- m = 0.667
- b = 0.20

**Cálculo de $P(X = 1 | Y_1 = 1, Y_2 = 1)$:

P(X = 1|Y₁ = 1, Y₂ = 1) = 1 - (1 - 0.20)(1 - 0.667)¹(1 - 0.667)¹
	               = 1 - (0.80)(0.333)(0.333)
                   = 1 - 0.089
	               = 0.911

**Cálculo de $P(X = 1 | Y_1 = 1, Y_2 = 1)$:**

P(X = 1|Y₁ = 1, Y₂ = 0) = 1 - (1 - 0.20)(1 - 0.667)¹(1 - 0.667)⁰
                   = 1 - (0.80)(0.333)(1)
                   = 1 - 0.267
                   = 0.733


**Estructura de cadena causal: (X -> Z - > Y)**

Dado:
- $c_i$ = 0.85
- m = 0.667
- b = 0.20

**Para calcular P(Z = 1 | X = 1), ecesitamos marginalizar sobre Y:**

P(Z = 1|X = 1) = P(Z = 1|Y = 1)·P(Y = 1|X = 1) + P(Z = 1|Y = 0)·P(Y = 0|X = 1)

Donde:
P(Y = 1|X = 1) = 0.733 (calculado como en causa común)
P(Y = 0|X = 1) = 0.267
P(Z = 1|Y = 1) = 0.733
P(Z = 1|Y = 0) = 0.20

P(Z = 1|X = 1) = (0.733)(0.733) + (0.20)(0.267)
	        = 0.537 + 0.053
            = 0.590


**Conclusión:**
- Mientras más alto la relación causal (parametro "m") y si se ve validado por la presencia de la causa (1-m)¹, más va a disminuir a la expresión (1-b), lo cual va a aumentar la probabilidad de la presencia del efecto
- Por otro lado, si la relación causal se ve invalidada por la ausencia de la causa (1-m)⁰, esto va a aumentar a la expresión (1-b) lo cual va a disminuir la probabilidad de la presencia del efecto

#### Modelo de Prototipos Duales

El Modelo de Prototipos Duales realiza las predicciones de inferencia para todas las combinaciones posibles en un modelo causal siguiente la ecuación del NOISY-OR.
Mientras que la influencia de los estados prorotípicos dentro de un concepto causal es mediadia por la siguiente ecuación:
$$Pr(X_1YX_2|H,d) ∝ ∈^{X_1YX_2} + Pr(X_1YX_2|H)$$
La contribuciónh de los estados prototípicos está mediada por una función de energía $∈^{X_1YX_2}$


#### Modelo de Mutación de Muestreo

El modelo de Mutación de MUestreo realiza un proceso secuencial de muestreo de los atributos causales, comenzando siempre por uno de los dos estados prototipos (111 o 000)
Luego, la aproximación probabilística de las inferencias específicas a cada caso se realiza mediante el cómputo de cadenas de Monte Carlo usando un algoritmo de Metropolis-Hastings
El MM utiliza la ecuación del NOISY-OR para derivar las probabilidades normativas de cada probabilidad condicional de un modelo causal H. Una vez obtenido el resultado de probabilidades, el algoritmo de Metropolis-Hastings comienza su proceso de muestreo secuencial siguiendo la siguiente ecuación:
$$\frac {Pr(q)} {Pr(q')} = \frac {Pr(X_1=1, Y=1, X_2=1)} {Pr(X_1=0, Y=1, X_2=1} = \frac {Pr(X_2=1 | X_1=1, Y=1,) Pr(Y=1) Pr(X_1=1)} {Pr(X_2=1 | X_1=0, Y=1,) Pr(Y=1) Pr(X_1=0)} = \frac {Pr(X_2=1 | X_1=1, Y=1,)Pr(X_1=1)} {Pr(X_2=1 | X_1=0, Y=1,)Pr(X_1=0)}$$
Modelo de Mutación de Muestreo se considera un parámetro libre λ, que supone el número máximo de cadenas obtenidas en el muestreo.
MM supone que λ siempre será bajo, dado que los sujetos tienen capacidades de memoria limitadas


#### Modelo de Incerteza Generalizada

Las fallas sitemáticas den el razonamiento causal ocurren debido a que los participantes aumentarían sus grados de incerteza sobre las cuales basan sus inferencias para estimar la probabilidad de un atributo
En este sentido, su conceptualización es similar a las explicaciones basadas en el uso de causas alternativas y de links causales exógenos
$$Pr(X_1=x_1, Y=y, X_2=x_2) = Pr(X_1=x_1, Y=y, X_2=x_2) Pr(H) + Pr(X_1=x_1, Y=y, X_2=x_2) Pr(H')$$

Donde: 
- X1, Y, X2 = Tienen valores de presencia o ausencia (1 o 0)
- Pr(H) = Corresponde a la creencia subjetiva o expectativa previa de que el modelo en su conjunto SÍ ocurra
- Pr(H') = Corresponde a la creencia de que el modelo alternativo (1 - Pr(H)) ocurra


### Hipótesis y Objetivos

#### Objetivo principal:
Conocer las causas de los fallos sitemáticos en el razonamiento causal mediante tareas de inferencia utilizando diferentes concepualizaciones causales

#### Hipótesis:
1) Las personas cometeán fallas sistemáticas en el razonamiento causal para las distintas estructuras causales
2) Las personas asignadas a la condición con evidencia empírica de un concepto causal realizarán juicios conservadores de inferencia (más cercanos al 50% en la escala)
3) El MIG obtendrá mejores ajustes de predicción con los datos empíricos en comparación a los modelos MPD y MM a través de los diferentes modelos causales
4) Las predicciones de los modelos MPD y MM empeorarán a mayor complejidad de los modelos causales, en comparación al modelo MIG
5) El MIG tendrá predicciones sensibles a la manipulación experimental, mientras que los modelos MPD y MM no serán capaces de capturar la incerteza del concepto causal

