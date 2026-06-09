
## Clase 10 de Estadística Avanzada

Clase 9: [[Conceptos SEM]]


## Recordatorio

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



## Matriz de varianza y covarianza

Las matrices de varianzas y covarianzas son el corazón del Modelamiento de Ecuaciones Estructurales (SEM) y del Análisis Factorial Confirmatorio (CFA)
El software LISREL busca minimizar la diferencia entre la **matriz observada (S)** —la que tú calculas con tus datos reales— y la **matriz implícita (Σ)** que el programa intenta reconstruir a partir de los parámetros que tú defines.

- Si ambas matrices son IGUALES, significa que los datos soportan el modelo
- Si ambas matrices son DIFERENTES, significa que los datos NO soportan al modelo

### Matriz Φ (Fi): Varianza y covarianza entre variables latentes exógenas
Esta matriz representa la relación entre tus constructos independientes (ξ - Xi).
- **Contenido:** En la diagonal principal se encuentran las **varianzas** de las variables latentes (por ejemplo, qué tanta variabilidad hay en el constructo "Percepción de violencia"). Fuera de la diagonal, se encuentran las **covarianzas**, que indican si dos constructos latentes se relacionan entre sí (ej. si quienes perciben más armas también perciben más violencia).
- **Importancia:** En CFA, es fundamental permitir que los factores correlacionen para ver si son dimensiones distintas pero relacionadas.
![[Captura de pantalla 2026-06-06 163415 1.png|506]]

### Matriz Ψ (Psi): Varianzas y covarianzas entre errores de variables latentes endógenas (ζ - Zeta)
Esta matriz se refiere a los residuos o la **varianza no explicada** de las variables dependientes (η - Eta).
- **Contenido:** Los elementos ζ representan todo aquello de la variable dependiente que el modelo estructural no logra explicar con las variables independientes.
- **Identificación:** En un CFA puro, a menudo tratas las variables endógenas como si fueran exógenas para validar la medición, pero en el modelo estructural final, esta matriz te dirá qué tan "bueno" es tu modelo para predecir la respuesta final.
![[Captura de pantalla 2026-06-06 190224.png|508]]

### Matrices Θδ​ (Theta-Delta) y Θϵ​ (Theta-Epsilon): Errores de las variables observables
Son las matrices que contienen la varianza de los **errores de medición** de tus indicadores (los ítems de la encuesta).
- Θδ​: Para los indicadores de variables exógenas (X).
- Θϵ​: Para los indicadores de variables endógenas (Y).
- **El supuesto inicial:** Lo normal es postular un modelo donde los errores **no están correlacionados** (diagonal principal con valores, el resto en cero). Sin embargo, si el ajuste es malo, los **Índices de Modificación (MI)** podrían sugerirte correlacionar dos errores si los ítems son muy similares en su fraseo, lo que "limpia" la medición del constructo.

### Relación con la Tare 2 (CFA)
Entender estas matrices es vital para el éxito de tu tarea por tres razones prácticas dadas por el profesor:

1. **La entrada de datos en LISREL:** Para realizar el CFA, el profesor recomienda **no meter los datos brutos**, sino generar primero la matriz de varianza-covarianza en SPSS.
    - _Paso práctico:_ Vas a "Análisis de fiabilidad" en SPSS, seleccionas tus indicadores y en "Estadísticos" marcas **"Covarianzas"**. Esa matriz resultante es la que debes copiar en un archivo de texto (`.txt`) para que LISREL la lea.
2. **Identificación del modelo:** Para que LISREL pueda calcular los valores de estas matrices, debes cumplir reglas de identificación. La más importante es **fijar un indicador por factor a 1.0** (usualmente el primero, como PUA_1 para el factor PUA). Esto le da una escala a la variable latente; de lo contrario, el programa no podrá resolver las ecuaciones.
3. **Refinamiento mediante la matriz de errores:** Si tu CFA inicial arroja un Chi-cuadrado significativo (ajuste malo), deberás revisar los **Modification Indices (MI)**. Estos índices a menudo te sugerirán liberar parámetros en la matriz Θ (correlacionar errores entre indicadores) para mejorar el ajuste, siempre que tengas una justificación teórica (ej. "los ítems PVD_1 y PVD_2 son casi idénticos").

**Consejo clave para la tarea:** El profesor advierte que LISREL es "mañoso" con los nombres y las rutas de archivos largos. Crea una carpeta con un nombre corto (ej. `C:\T2`) y asegúrate de que el orden de los indicadores en tu archivo de matriz coincida exactamente con el orden en que los declaras en el software.



## Máxima Verosimilitud (ML - Maximum Likelihood)
El método de **Máxima Verosimilitud (ML - Maximum Likelihood)** es el estándar en SEM y CFA para estimar los parámetros (θ) que minimizan la diferencia entre la matriz de varianza-covarianza observada (S) y la implícita por el modelo (Σ).

Fórmula:
$$F_{ML} = log|∑| + tr(S ∑^{-1}) - log |S| - (p+q)$$

### Ventajas y Desventajas de ML
- **Ventajas:** 
	- Es un método **asintóticamente insesgado, consistente y eficiente**. 
	- A medida que  la muestra aumenta, las estimaciones tienden a la normalidad
	- Esto permite calcular **errores estándar, intervalos de confianza y valores de significancia (p)** para cada parámetro.
- **Desventajas:** 
	- Requiere muestras grandes (N≥100) 
	- Los datos deben ser normales, especialmente para muestras pequeñas
	- Método de optimización (minimización) puede producir valores impropios (ej: varianzas negativas)
	- Modelo debe estar identificado y matriz de datos debe ser positiva y definida

### Índices de Ajuste Absoluto
Estos miden qué tan bien el modelo reproduce la matriz de datos original:

- **Chi-cuadrado (T):** Evalúa la hipótesis nula de que no hay diferencia entre las matrices (S−Σ=0). A diferencia de otras pruebas, en SEM **NO queremos rechazar** H0​, por lo que buscamos un p>0.05.
- **GFI (Goodness of Fit Index) y AGFI (Adjusted GFI):** Indican la proporción de varianza explicada por el modelo. Se consideran aceptables si son ≥0.90.
- **RMSR (Root Mean Square Residuals):** Mide el promedio de los residuos. Se busca un valor ≤0.05 para matrices de correlación o un **SRMR (estandarizado)** ≤0.08 para covarianzas.
- **RMSEA (Root Mean Square Error of Approximation):** Evalúa el error por cada grado de libertad. Un ajuste bueno requiere un **RMSEA** ≤0.06.


## Estadístico T
Es el estándar fundamental para medir la calidad de un modelo en SEM y CFA, ya que representa el valor de **Chi-cuadrado (χ2)** del modelo.

Puntos clave
- **¿Qué mide?**: Cuantifica la diferencia entre la **matriz de covarianzas observada (S)** (tus datos reales) y la **matriz implícita (Σ)** (la que tu modelo intenta reproducir). Su fórmula es T=(N–1)FML​.
- **Interpretación de calidad**: A diferencia de otras pruebas, aquí **NO queremos rechazar la hipótesis nula (H0​)**. Un modelo de alta calidad es aquel donde T es pequeño y su significancia es p>0.05, lo que indica que el modelo es estadísticamente igual a los datos.
- **Sensibilidad**: Es un indicador muy sensible al tamaño de la muestra (N); si la muestra es muy grande, T tenderá a ser significativo (indicando "mal ajuste") incluso si las diferencias son mínimas.
- **Base de otros índices**: Es el estándar principal porque la mayoría de los otros índices de bondad de ajuste (como RMSEA, GFI o CFI) se calculan basándose en el valor de T y los grados de libertad.



## Identificación (ajuste)
La **identificación** en SEM es el requisito matemático que determina si es posible obtener una solución única para los parámetros del modelo a partir de los datos observados. El profesor la explica mediante una analogía geométrica muy clara:

*df = degrees of freedom*

- **Modelo Subidentificado (df<0):** Es como tener **un solo punto** en un gráfico e intentar trazar una línea. Existen infinitas líneas posibles, por lo que no hay información suficiente para elegir una.
- **Modelo Exactamente Identificado (df=0):** Es como tener **dos puntos**. Solo se puede trazar una línea perfecta. El ajuste será "perfecto" por definición, pero no tienes "grados de libertad" para probar si esa línea realmente representa bien la realidad; simplemente estás obligado a que pase por ahí.
- **Modelo Sobreidentificado (df>0):** Es el objetivo en SEM. Es como tener **tres o más puntos** para trazar una línea. Te "sobran" datos (puntos) respecto a los parámetros que buscas (la línea). Esto genera **grados de libertad**, los cuales permiten medir el **desajuste**: qué tan lejos están los puntos de la línea ideal.

Puntos clave para tus notas:

1. **Condición Necesaria:** 
	- Para que el programa pueda correr, debes tener grados de libertad positivos (df>0).
	- El número de parámetros libres a ser estimados (t) debe ser mayor a la información aportada por el número de variables observables
$$df = \frac{1}{2}(p+q)(p+q+1)-t > 0$$
2. **Relación con el Ajuste:** Al igual que en machine learning, si el modelo está "exactamente identificado", no puedes evaluar su error de aproximación porque el modelo consume toda la información disponible para dar una solución única. La **sobreidentificación** es lo que nos da el "permiso" para ver si el modelo realmente "encaja" o no con los datos reales.
3. **Reglas Prácticas de Identificación:**
    - **Fijar la escala:** Cada variable latente debe tener un ancla. Esto se hace **fijando el lambda (λ) de uno de sus indicadores a 1.0**.
    - **Indicadores únicos:** Idealmente, cada indicador debe medir solo una variable latente (evitar _cross-loadings_ iniciales).
    - **Casos de un solo indicador:** Si una variable tiene solo un indicador, se debe fijar su carga a 1.0 y su error a 0 (asumiendo medición perfecta) o a un valor basado en una confiabilidad previa conocida.
	    - **Para el error:** Otra alternativa es suponer una cierta confiabilidad ($\alpha$) y fijar su error en ($1-\alpha$) multiplicado por la varianza dle indicador
	    - A veces es posible omitir fijar el error y el programa SEM automáticamente fija otros valores que permiten la identificación, pero la matriz de varianzas-covarianzas de los errores puede volverse no positiva o no definida

Si el modelo está **mal identificado**, el algoritmo de LISREL puede no converger, arrojar valores absurdos (como varianzas negativas) o simplemente "congelarse".



## Reespecificación

La **reespecificación** es el proceso de modificar el modelo original cuando los resultados iniciales indican un ajuste pobre (cuando el estadístico T es significativamente distinto de cero). El objetivo es realizar ajustes para mejorar la concordancia entre el modelo y los datos.


### La Regla de Oro: Prioridad a la Teoría
La reespecificación no debe ser un ejercicio meramente matemático. Cualquier cambio realizado debe estar **basado principalmente en la teoría**. Al analizar las salidas del software, el investigador debe evaluar:

- Si las **cargas factoriales (lambdas)** son correctas y tienen sentido teórico.
- Si existen **errores de medición correlacionados** entre indicadores que comparten un fraseo o contenido similar.
- Si es necesario añadir o eliminar **senderos (paths)** entre variables.


### Índices de Modificación (MI - Modification Indices)

Los software como LISREL entregan los **MI**, que son herramientas empíricas para guiar la reespecificación.

- **¿Qué indican?**: Muestran cuánto disminuiría el estadístico Chi-cuadrado (T) si se realizara un cambio específico (liberar un parámetro).
- **Procedimiento**: Se debe elegir el cambio que más reduzca T (siempre que sea teóricamente defendible), re-estimar el modelo y observar si el ajuste mejora.
- **Restricción**: Los MI son válidos para **un solo cambio a la vez**. No se deben aplicar múltiples sugerencias de una sola vez porque el impacto en el ajuste no es acumulativo de forma lineal.

 
### Modelos Anidados (Nested Models)

Para comparar formalmente si el modelo reespecificado es realmente mejor que el anterior, se utiliza el concepto de **modelos anidados**.

- **Definición**: El modelo A está anidado en el modelo B si el modelo A es un subconjunto del modelo B (es decir, tiene las mismas variables pero con más restricciones o menos senderos).
- **Prueba de Diferencia de Chi-cuadrado**: Se calcula la diferencia entre los valores de T de ambos modelos
- **Objetivo**: En esta prueba **SÍ queremos rechazar la hipótesis nula (H0​)**. Si el resultado es significativo, significa que el modelo con menos restricciones (el modelo modificado) mejora el ajuste de forma estadísticamente significativa respecto al modelo base.


### Advertencias sobre la "Cocina" del Modelo

El profesor advierte sobre los peligros de un ajuste excesivo (**overfitting**):

- **La "Fishing Expedition"**: No se debe "pescar" parámetros solo para que el modelo cuadre. Si se añaden demasiadas relaciones sugeridas por los MI sin sustento teórico, el modelo pierde su capacidad de **generalización** a otros datos.
- **Saturación**: Añadir demasiadas correlaciones entre errores puede "limpiar" el ajuste matemáticamente, pero a menudo oculta problemas reales en la calidad de los indicadores o de la batería de preguntas.

**Relevancia para la Tarea 2 (CFA):** En tu tarea, si el CFA inicial de las variables predictoras (como PUA, PBD, PVD) arroja un ajuste pobre, deberás observar los MI. Si LISREL sugiere que los errores entre, por ejemplo, PUA_1 y PUA_2 están correlacionados, revisa el fraseo de esos ítems en el documento de tareas; si son muy parecidos, la reespecificación es justificable



## EFA
- Se asume que todas las variables observables están correlacionadas entre sí, aunque en distintos grados
- Todos los factores cargan con todos los indicadores, aunque en distintos grados
- Los errores entre variables no están correlacionados



## Confirmatory Factor Analysis
- Uno de los principales problemas de EFA es su inhabilidad para incorporar restricciones sutancialmete/conceptualmente significativas
- Las correlaciones entre factores son una parte explícita del análisis, ya que se especifican en una matriz de correlaciones entre dichos factores
- Aún más, en CFA el investigador es capaz de imponer *a priori* si los factores deberían correlacionar o no (decisiones motivadas por la teoría)
	- Qué pares de factores están correlacionados
	- Cuáles variables observables (indicadores) son afectadas por factores comunes
	- Cuales variables observables osn afectadas por un único factor
	- Qué pares de factores únicos están correlacionados
	- Al igual que en EFA, se hace CFA sobre los factores exógenos y endógenos por separado



## Especificación del modelo
La especificación del modelo CFA requiere hacer suposiciones formales y explícitas respecto a:
- Número de factores comunes (variables latentes)
- Numero de variables observables (indicadores)
- Las varianzas y covarianzas entre los factores comunes
- La relación entre variables observadas (indicadores) y variables latentes (factores)




## Ejemplo de CFA en LISREL

Siguiendo el audio de la clase 4 y el material de apoyo, aquí tienes el seguimiento paso a paso del análisis de **Análisis Factorial Confirmatorio (CFA)** realizado por el profesor en **LISREL**, junto con la resolución de tu duda técnica sobre el archivo de matrices.

Paso a paso del análisis de CFA en LISREL

El profesor utiliza una interfaz gráfica que luego traduce a sintaxis **SIMPLIS**. Los pasos realizados fueron:

1. **Inicio del Proyecto:** Ir a `File` -> `New` -> `Path Diagram` y asignarle un nombre al archivo (ej. `CFA_1`).
2. **Definición de Variables:** En `Setup` -> `Variables`, se eliminan las variables por defecto y se agregan las **Variables Observadas** (indicadores) ingresando el rango (ej. `x1-x6`). Luego, se agregan las **Variables Latentes** (factores) dándoles un nombre corto y descriptivo.
3. **Vinculación de Datos:** En `Setup` -> `Data`, se selecciona la opción de leer datos desde un archivo externo (**External ASCII Data**), buscando el archivo `.txt` o `.spl`. Es vital ingresar el **tamaño de la muestra (N)** exacto (ej. 319 o 631 según el caso) para que los cálculos de significancia sean correctos.
4. **Dibujo del Diagrama:** El profesor enfatiza arrastrar **primero las variables latentes** (óvalos) al lienzo y luego los indicadores (rectángulos). Se dibujan las flechas de carga (paths) desde el factor hacia sus indicadores usando la herramienta de flecha unidireccional.
5. **Identificación del Modelo (Fijar Escala):** Para que el modelo sea estimable, se debe anclar la escala de medida. El profesor selecciona el primer indicador de cada factor, hace clic derecho y elige `Set value` para **fijarlo en 1.0**.
6. **Generación de Sintaxis y Ejecución:** Se va a `Setup` -> `Build Simplis syntax` para revisar que la lógica del modelo esté bien escrita. Finalmente, se presiona el botón con el ícono de la "L" (**Run LISREL**) para correr el modelo.
7. **Interpretación de Salidas:**
    - **Estimaciones:** Muestra las cargas factoriales y las varianzas en el diagrama.
    - **T-values:** Se cambia la vista a `T-values` para ver si los parámetros son significativos (∣t∣≥1.96).
    - **Bondad de Ajuste:** Se revisan el **Chi-cuadrado**, los grados de libertad (**df**), el **valor P** (idealmente >0.05) y el **RMSEA** (idealmente ≤0.06) en la parte inferior del diagrama.
8. **Reespecificación:** Si el ajuste es malo, se consultan los **Modification Indices (MI)**, que sugieren qué flechas añadir (como correlacionar errores de indicadores) para bajar el valor del Chi-cuadrado.

### Sobre el archivo .txt de las Matrices
El profesor generó la matriz de varianza-covarianza en **SPSS** siguiendo estos clics: `Analizar` -> `Escala` -> `Análisis de fiabilidad` -> `Estadísticos` -> marcar **Covarianzas**. Luego copió ese resultado a un archivo de texto simple.
Luego agregó esta matriz de varianza-covarianza en el paso 3 para darle mayor calidad a los resulados del CFA



[[Tarea CFA]]

Siguiente Clase: [[Aplicación SEM]]

