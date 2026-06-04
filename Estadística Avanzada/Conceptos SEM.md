
## Clase 9 de Estadística Avanzada

Clase 8: [[Modelamiento de Ecuaciones Estructurales]]


## Conceptos básicos
Las relaciones entre variables se representan por diagramas causales o estructurales

### Notación
- Círculos = Errores
- Rectángulos = Variables observables o indicadores
- Óvalos = Variables latentes o factores
- Flechas = Efectos o ausalidad
- Flechas arqueadas = Correlaciones

### Definiciones
- *Variables endógenas:*
	- **Definición Conceptual:** Son aquellas variables que actúan como **causas o predictores** dentro del modelo y que **no son explicadas por otras variables**. En términos coloquiales, son variables a las que no les llega ninguna flecha de causalidad (pero sí quizás de correlación).
	- **Relación con la clase:** En el contexto de SEM, se representan comúnmente con la letra griega ξ **(Xi o Ksi)** y sus indicadores se denotan con la letra x. En el ejemplo de la clase sobre rendimiento, las variables exógenas eran la "Motivación al logro", "Autoestima" e "Inteligencia verbal".****
- *Variables exógenas:*
	- **Definición Conceptual:** Son las variables que el modelo **intenta explicar** o que son causadas por otras variables (ya sean exógenas u otras endógenas). Se identifican gráficamente porque **tienen al menos una flecha que les apunta** directamente.
	- **Relación con la clase:** Se representan con la letra griega η **(eta)** y sus indicadores se denotan con la letra y. El profesor explica que una variable puede volverse endógena si se reconoce que otra la afecta; por ejemplo, en la clase, la "Satisfacción con el trabajo" y el "Rendimiento" son variables endógenas.
- *Cargas:*
	- **Definición Conceptual:** Representan la **fuerza de la relación o influencia** de una variable latente (factor) sobre sus indicadores observados. Indican cuánto "carga" o refleja cada indicador al constructo que pretende medir.
	- **Relación con la clase:** En la notación de SEM, las cargas se denominan λ **(lambda)**. Es importante notar que, aunque en el EFA (Análisis Factorial Exploratorio) se usan para agrupar ítems, en SEM la dirección de la flecha va **del óvalo (variable latente) al rectángulo (indicador)**. Los subíndices de los lambdas en las matrices indican primero el indicador y luego el factor (ej. λ21​ es la carga del indicador 2 sobre el factor 1)



## Tabla de Notación SEM

| Concepto                              | Símbolo Griego | Tipo de Indicador | Relación con otros símbolos / Error Asociado                                                                       |
| ------------------------------------- | -------------- | ----------------- | ------------------------------------------------------------------------------------------------------------------ |
| **Variable Latente Exógena**          | ξ (Xi / Ksi)   | x                 | Son variables independientes. Su error de medición en los indicadores es δ.                                        |
| **Variable Latente Endógena**         | η (Eta)        | y                 | Son variables dependientes. Su error de medición en los indicadores es ϵ y su error estructural es ζ.              |
| **Cargas Factoriales (Loadings)**     | λ (Lambda)     | -                 | Representan la fuerza de la relación entre la variable latente (ξ o η) y sus indicadores (x o y).                  |
| **Influencia Exógena → Endógena**     | γ (Gamma)      | -                 | Coeficientes que indican el efecto de una variable independiente (ξ) sobre una dependiente (η).                    |
| **Influencia Endógena → Endógena**    | β (Beta)       | -                 | Coeficientes que indican la relación causal entre dos variables dependientes (η).                                  |
| **Covarianza entre Exógenas**         | ϕ (Phi)        | -                 | Representa la varianza y correlación entre las variables latentes independientes (ξ).                              |
| **Error de Medición de "x"**          | δ (Delta)      | x                 | Es el ruido o error asociado específicamente a los indicadores de las variables exógenas.                          |
| **Error de Medición de "y"**          | ϵ (Epsilon)    | y                 | Es el ruido o error asociado específicamente a los indicadores de las variables endógenas.                         |
| **Residuo Estructural**               | ζ (Zeta)       | -                 | Representa la varianza no explicada de la variable endógena (η) en el modelo causal.                               |
| **Covarianza de Errores de Medición** | θ (Theta)      | -                 | Indica si los errores de los indicadores (δ o ϵ) están correlacionados entre sí (θδ​ o θϵ​).                       |
| **Covarianza de Residuos (ζ)**        | ψ (Psi)        | -                 | Representa la correlación entre la varianza no explicada de diferentes ecuaciones estructurales.                   |
| **Matriz de Covarianza Implícita**    | Σ (Sigma)      | -                 | Es la matriz de varianza-covarianza que el modelo intenta reproducir basándose en todos los parámetros anteriores. |


## Desarrollo de teoría
![[Captura de pantalla 2026-05-26 122811.png|449]]



## Fórmulas
### Variable Endógena
$$X = \lambda_x ξ + \phi $$

Ejemplo:

$$
\begin{vmatrix}
x_1 \\ x_2 \\ x_3 \\ x_4 \\ x_5
\end{vmatrix} = 
\begin{vmatrix}
\lambda_{11} & 0 & 0 \\ 
\lambda_{21} & 0 & 0 \\ 
0 & \lambda_{32} & 0 \\ 
0 & \lambda_{42} & 0 \\ 
0 & 0 & \lambda_{53}
\end{vmatrix} *
\begin{vmatrix}
\xi_1 \\ \xi_2 \\ \xi_3
\end{vmatrix} + 
\begin{vmatrix}
\delta_1 \\ \delta_2 \\ \delta_3 \\ \delta_4 \\ \delta_5
\end{vmatrix}
$$


### Variable Exógena
$$y = \lambda_y \eta + \epsilon$$

Ejemplo:
$$
\begin{vmatrix}
y_1 \\ y_2 \\ y_3
\end{vmatrix} = 
\begin{vmatrix}
\lambda_{11} & 0 \\
0 & \lambda{22} \\
0 & \lambda{32}
\end{vmatrix} *
\begin{vmatrix}
\eta_1 \\ \eta_2
\end{vmatrix} +
\begin{vmatrix}
\xi_1 \\ \xi_2 \\ \xi_3
\end{vmatrix}
$$


Clase 10: [[Estadística Avanzada/Sin título|Sin título]]
