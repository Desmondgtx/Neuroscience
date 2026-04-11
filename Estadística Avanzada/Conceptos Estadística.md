
# Cuadro Comparativo: Conceptos Fundamentales de Estadística

## 1. Suma de Desviaciones (Sum of Deviations)

| **Aspecto**      | **Descripción**                                                                                                                        |
| ---------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| **Definición**   | Es la suma total de las diferencias entre cada valor y la media aritmética. Mide qué tan dispersos están los datos respecto al centro. |
| **Fórmula**      | Σ(xi - x̄) = 0                                                                                                                         |
| **Variables**    | • xi = cada valor individual de la muestra<br>• x̄ = media aritmética<br>• n = número de observaciones                                 |
| **Cálculo**      | 1. Calcular la media: x̄ = Σxi/n<br>2. Restar la media de cada valor: (xi - x̄)<br>3. Sumar todas las diferencias                      |
| **Resultado**    | **Siempre es igual a CERO** para cualquier conjunto de datos                                                                           |
| **Aplicaciones** | • Verificación de cálculos de la media<br>• Base conceptual para otros estadísticos<br>• Demostración de propiedades de la media       |
| **Importancia**  | Fundamental para entender por qué se necesita elevar al cuadrado las desviaciones en otros estadísticos                                |

## 2. Suma de Errores al Cuadrado (Sum of Squared Errors - SSE)

|**Aspecto**|**Descripción**|
|---|---|
|**Definición**|Es la suma de los cuadrados de las diferencias entre cada valor observado y la media (o valor predicho). Elimina el problema de que las desviaciones sumen cero.|
|**Fórmula**|SSE = Σ(xi - x̄)²|
|**Variables**|• xi = cada valor individual<br>• x̄ = media aritmética (o valor predicho)<br>• n = número de observaciones|
|**Cálculo**|1. Calcular la media<br>2. Restar la media de cada valor<br>3. Elevar cada diferencia al cuadrado<br>4. Sumar todos los cuadrados|
|**Aplicaciones**|• Cálculo de varianza y desviación estándar<br>• Análisis de regresión<br>• ANOVA<br>• Medida de bondad de ajuste|
|**Características**|• Siempre es positivo<br>• Penaliza más las desviaciones grandes<br>• Base para muchos estadísticos|

## 3. Error Estándar (Standard Error - SE)

|**Aspecto**|**Descripción**|
|---|---|
|**Definición**|Mide la precisión de una estadística muestral (como la media) estimando cuánto varía esta estadística entre diferentes muestras de la misma población.|
|**Fórmula**|SE = σ/√n o SE = s/√n|
|**Variables**|• σ = desviación estándar poblacional<br>• s = desviación estándar muestral<br>• n = tamaño de la muestra|
|**Cálculo**|1. Calcular la desviación estándar<br>2. Dividir entre la raíz cuadrada del tamaño muestral|
|**Aplicaciones**|• Intervalos de confianza<br>• Pruebas de hipótesis<br>• Determinar precisión de estimaciones<br>• Planificación de tamaños muestrales|
|**Interpretación**|Menor SE = mayor precisión de la estimación<br>Mayor n = menor SE|

## 4. Desviación Estándar (Standard Deviation - SD)

|**Aspecto**|**Descripción**|
|---|---|
|**Definición**|Mide la dispersión promedio de los datos respecto a la media. Es la raíz cuadrada de la varianza y se expresa en las mismas unidades que los datos originales.|
|**Fórmulas**|**Poblacional:** σ = √[Σ(xi - μ)²/N]<br>**Muestral:** s = √[Σ(xi - x̄)²/(n-1)]|
|**Variables**|• xi = cada valor individual<br>• μ = media poblacional<br>• x̄ = media muestral<br>• N = tamaño poblacional<br>• n = tamaño muestral|
|**Cálculo**|1. Calcular la media<br>2. Calcular SSE<br>3. Dividir por N (población) o n-1 (muestra)<br>4. Obtener la raíz cuadrada|
|**Aplicaciones**|• Descripción de variabilidad<br>• Identificación de valores atípicos<br>• Control de calidad<br>• Finanzas (riesgo)<br>• Estandarización (puntuaciones Z)|
|**Interpretación**|En distribución normal:<br>• 68% datos dentro de ±1σ<br>• 95% datos dentro de ±2σ<br>• 99.7% datos dentro de ±3σ|

## 5. Intervalos de Confianza (Confidence Intervals - CI)

|**Aspecto**|**Descripción**|
|---|---|
|**Definición**|Rango de valores que, con un nivel de confianza específico (ej. 95%), contiene el verdadero valor del parámetro poblacional.|
|**Fórmulas**|**Para la media (σ conocida):** x̄ ± z(α/2) × (σ/√n)<br>**Para la media (σ desconocida):** x̄ ± t(α/2) × (s/√n)<br>**Para proporción:** p̂ ± z(α/2) × √[p̂(1-p̂)/n]|
|**Variables**|• x̄ = media muestral<br>• z(α/2), t(α/2) = valores críticos<br>• σ, s = desviación estándar<br>• n = tamaño muestral<br>• α = nivel de significancia|
|**Cálculo**|1. Calcular estadística muestral<br>2. Determinar valor crítico<br>3. Calcular margen de error<br>4. Construir intervalo: estadística ± margen de error|
|**Aplicaciones**|• Estimación de parámetros poblacionales<br>• Toma de decisiones<br>• Investigación médica<br>• Encuestas de opinión<br>• Control de calidad|
|**Interpretación**|"Estamos 95% confiados de que el verdadero parámetro está en este rango"|

### **Diferencias Clave:**

|**Concepto**|**Propósito**|**Unidades**|**Interpretación**|
|---|---|---|---|
|**Suma de Desviaciones**|Verificación conceptual|Mismas que datos originales|Siempre = 0|
|**SSE**|Base para otros cálculos|Cuadradas|Variabilidad total|
|**Desviación Estándar**|Descripción de dispersión|Mismas que datos originales|Dispersión típica|
|**Error Estándar**|Precisión de estimaciones|Mismas que estadística|Variabilidad de la estadística|
|**Intervalo de Confianza**|Estimación con incertidumbre|Mismas que parámetro|Rango plausible|

### **Progresión Conceptual:**

1. Las desviaciones simples suman cero (Suma de Desviaciones)
2. Elevamos al cuadrado para obtener variabilidad (SSE)
3. Estandarizamos para describir dispersión (Desviación Estándar)
4. Ajustamos para muestras y estimaciones (Error Estándar)
5. Creamos rangos de incertidumbre (Intervalos de Confianza)



# Testeo de Hipótesis - Conceptos Fundamentales

## 1. Test de Hipótesis de Una Cola (One-Tailed Test)

| **Aspecto**      | **Descripción**                                                                                                                                                                            |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Definición**   | Prueba estadística que evalúa si un parámetro es significativamente mayor O menor que un valor específico. La región de rechazo está en un solo extremo de la distribución.                |
| **Hipótesis**    | **H₀:** μ = μ₀<br>**H₁:** μ > μ₀ (cola derecha) O μ < μ₀ (cola izquierda)                                                                                                                  |
| **Fórmulas**     | **Estadístico Z:** z = (x̄ - μ₀)/(σ/√n)<br>**Estadístico t:** t = (x̄ - μ₀)/(s/√n)<br>**Región crítica:** z > z_α o z < -z_α                                                               |
| **Variables**    | • x̄ = media muestral<br>• μ₀ = media hipotética<br>• σ = desviación estándar poblacional<br>• s = desviación estándar muestral<br>• n = tamaño de muestra<br>• α = nivel de significancia |
| **Cálculo**      | 1. Establecer hipótesis direccional<br>2. Elegir nivel α<br>3. Calcular estadístico de prueba<br>4. Determinar valor crítico<br>5. Comparar y decidir                                      |
| **Aplicaciones** | • Verificar si un tratamiento mejora resultados<br>• Comprobar si un proceso reduce costos<br>• Evaluar si una variable aumenta o disminuye<br>• Control de calidad direccional            |
| **Ventajas**     | • Mayor poder estadístico para detectar efectos direccionales<br>• Más específico en la dirección del efecto                                                                               |
| **Desventajas**  | • Requiere conocimiento previo de la dirección del efecto<br>• No detecta efectos en dirección opuesta                                                                                     |

## 2. Test de Hipótesis de Dos Colas (Two-Tailed Test)

|**Aspecto**|**Descripción**|
|---|---|
|**Definición**|Prueba estadística que evalúa si un parámetro es significativamente diferente (mayor O menor) de un valor específico. La región de rechazo se divide en ambos extremos de la distribución.|
|**Hipótesis**|**H₀:** μ = μ₀<br>**H₁:** μ ≠ μ₀|
|**Fórmulas**|**Estadístico Z:** z = (x̄ - μ₀)/(σ/√n)<br>**Estadístico t:** t = (x̄ - μ₀)/(s/√n)<br>**Región crítica:**|
|**Variables**|• Las mismas que el test de una cola<br>• α/2 en cada cola (región crítica dividida)|
|**Cálculo**|1. Establecer hipótesis no direccional<br>2. Elegir nivel α<br>3. Calcular estadístico de prueba<br>4. Determinar valores críticos (±)<br>5. Comparar y decidir|
|**Aplicaciones**|• Comparar dos grupos sin dirección específica<br>• Evaluar diferencias sin hipótesis direccional<br>• Investigación exploratoria<br>• Estudios donde no se conoce la dirección del efecto|
|**Ventajas**|• No requiere conocimiento previo de dirección<br>• Detecta diferencias en cualquier dirección<br>• Más conservador|
|**Desventajas**|• Menor poder estadístico que test de una cola<br>• Requiere evidencia más fuerte para rechazar H₀|

## 3. Error Tipo I (Type I Error - α)

|**Aspecto**|**Descripción**|
|---|---|
|**Definición**|Error que ocurre cuando rechazamos una hipótesis nula que es verdadera. Es un "falso positivo" - concluimos que hay un efecto cuando realmente no lo hay.|
|**Fórmula**|**Probabilidad:** P(Error Tipo I) = α<br>**En términos de decisión:** P(Rechazar H₀|
|**Variables**|• α = nivel de significancia (usualmente 0.05, 0.01, o 0.10)<br>• Valor crítico determinado por α|
|**Control**|Se controla estableciendo el nivel α antes del análisis<br>• α = 0.05 → 5% probabilidad de Error Tipo I<br>• α = 0.01 → 1% probabilidad de Error Tipo I|
|**Aplicaciones**|• Investigación médica (falsos positivos en diagnóstico)<br>• Control de calidad (rechazar producto bueno)<br>• Investigación científica (confirmar efecto inexistente)|
|**Consecuencias**|• Implementar tratamientos inefectivos<br>• Tomar decisiones erróneas<br>• Desperdiciar recursos<br>• Conclusiones científicas incorrectas|
|**Relación con α**|**α ES la probabilidad de Error Tipo I**<br>Menor α → Menor riesgo de Error Tipo I, pero mayor riesgo de Error Tipo II|

## 4. Error Tipo II (Type II Error - β)

|**Aspecto**|**Descripción**|
|---|---|
|**Definición**|Error que ocurre cuando no rechazamos una hipótesis nula que es falsa. Es un "falso negativo" - no detectamos un efecto que realmente existe.|
|**Fórmula**|**Probabilidad:** P(Error Tipo II) = β<br>**En términos de decisión:** P(No rechazar H₀|
|**Variables**|• β = probabilidad de Error Tipo II<br>• Depende del tamaño del efecto real<br>• Depende del tamaño de muestra<br>• Depende del nivel α elegido|
|**Factores que afectan β**|• **Tamaño del efecto:** Efectos más grandes → menor β<br>• **Tamaño de muestra:** Muestras más grandes → menor β<br>• **Nivel α:** α más grande → menor β<br>• **Variabilidad:** Menor variabilidad → menor β|
|**Aplicaciones**|• Investigación médica (no detectar enfermedad)<br>• Control de calidad (aceptar producto defectuoso)<br>• Investigación (no detectar efecto real)|
|**Consecuencias**|• No implementar tratamientos efectivos<br>• Perder oportunidades de mejora<br>• No detectar problemas reales<br>• Conclusiones conservadoras erróneas|
|**Cálculo**|Requiere especificar:<br>1. Valor real del parámetro<br>2. Nivel α<br>3. Tamaño de muestra<br>4. Variabilidad|

## 5. Tamaño del Efecto (Effect Size)

|**Aspecto**|**Descripción**|
|---|---|
|**Definición**|Medida estandarizada de la magnitud de la diferencia o relación entre variables. Indica qué tan grande es el efecto, independientemente de la significancia estadística.|
|**Fórmulas Principales**|**d de Cohen:** d = (μ₁ - μ₂)/σ<br>**r de Pearson:** r = correlación<br>**η² (eta cuadrado):** η² = SS_efecto/SS_total<br>**ω² (omega cuadrado):** ω² = (SS_efecto - df_efecto × MS_error)/SS_total + MS_error|
|**Variables**|• μ₁, μ₂ = medias de los grupos<br>• σ = desviación estándar poblacional<br>• SS = suma de cuadrados<br>• MS = cuadrado medio<br>• df = grados de libertad|
|**Interpretación (d de Cohen)**|• **Pequeño:** d = 0.2<br>• **Mediano:** d = 0.5<br>• **Grande:** d = 0.8<br>• **Muy grande:** d ≥ 1.0|
|**Aplicaciones**|• Meta-análisis<br>• Comparación entre estudios<br>• Significancia práctica vs. estadística<br>• Planificación de estudios<br>• Comunicación de resultados|
|**Importancia**|• Independiente del tamaño de muestra<br>• Indica relevancia práctica<br>• Permite comparaciones entre estudios<br>• Complementa la significancia estadística|

## 6. Poder Estadístico (Statistical Power - 1-β)

|**Aspecto**|**Descripción**|
|---|---|
|**Definición**|Probabilidad de rechazar correctamente una hipótesis nula falsa. Es la capacidad de detectar un efecto cuando realmente existe.|
|**Fórmula**|**Poder = 1 - β**<br>**P(Rechazar H₀|
|**Variables**|• β = probabilidad de Error Tipo II<br>• α = nivel de significancia<br>• n = tamaño de muestra<br>• δ = tamaño del efecto<br>• σ = variabilidad|
|**Factores que aumentan el poder**|• **↑ Tamaño de muestra (n)**<br>• **↑ Tamaño del efecto (δ)**<br>• **↑ Nivel α** (pero ↑ Error Tipo I)<br>• **↓ Variabilidad (σ)**<br>• **Diseño experimental más eficiente**|
|**Niveles recomendados**|• **Mínimo aceptable:** 0.80 (80%)<br>• **Deseable:** 0.90 (90%)<br>• **Alto:** 0.95 (95%)|
|**Aplicaciones**|• **Análisis a priori:** Determinar tamaño de muestra necesario<br>• **Análisis post hoc:** Evaluar poder del estudio realizado<br>• **Comparación de diseños**<br>• **Meta-análisis**|
|**Cálculo**|Requiere software especializado (G*Power, R, etc.)<br>Especificar: α, tamaño del efecto, tipo de test|

## 7. Valor p (p-value)

|**Aspecto**|**Descripción**|
|---|---|
|**Definición**|Probabilidad de obtener un resultado igual o más extremo que el observado, asumiendo que la hipótesis nula es verdadera. Mide la evidencia en contra de H₀.|
|**Fórmula**|**p = P(obtener estadístico ≥ observado|
|**Variables**|• Estadístico de prueba calculado<br>• Distribución bajo H₀<br>• Tipo de test (una o dos colas)|
|**Interpretación**|• **p < 0.001:** Evidencia muy fuerte contra H₀<br>• **0.001 ≤ p < 0.01:** Evidencia fuerte contra H₀<br>• **0.01 ≤ p < 0.05:** Evidencia moderada contra H₀<br>• **0.05 ≤ p < 0.10:** Evidencia débil contra H₀<br>• **p ≥ 0.10:** Evidencia insuficiente contra H₀|
|**Cálculo**|1. Calcular estadístico de prueba<br>2. Determinar distribución bajo H₀<br>3. Calcular probabilidad de cola(s)<br>4. Ajustar para una o dos colas|
|**Aplicaciones**|• Toma de decisiones estadísticas<br>• Reporte de resultados de investigación<br>• Comparación con nivel α<br>• Graduación de evidencia|
|**Limitaciones**|• No indica tamaño del efecto<br>• Influenciado por tamaño de muestra<br>• No es probabilidad de que H₀ sea verdadera|

## 8. Valor Alpha (α - Nivel de Significancia)

|**Aspecto**|**Descripción**|
|---|---|
|**Definición**|Umbral predeterminado que define cuán extremo debe ser un resultado para rechazar la hipótesis nula. Es la probabilidad máxima de Error Tipo I que estamos dispuestos a aceptar.|
|**Valores comunes**|• **α = 0.05 (5%):** Estándar en ciencias sociales<br>• **α = 0.01 (1%):** Más conservador, ciencias médicas<br>• **α = 0.10 (10%):** Más liberal, estudios exploratorios|
|**Fórmula de decisión**|**Si p ≤ α:** Rechazar H₀ (resultado significativo)<br>**Si p > α:** No rechazar H₀ (resultado no significativo)|
|**Variables relacionadas**|• Valores críticos de la distribución<br>• Región de rechazo<br>• Poder estadístico<br>• Probabilidad de Error Tipo I|
|**Selección de α**|**Factores a considerar:**<br>• Gravedad de Error Tipo I<br>• Estándares del campo de estudio<br>• Naturaleza exploratoria vs. confirmatoria<br>• Consecuencias de decisiones erróneas|
|**Aplicaciones**|• Establecimiento antes del análisis<br>• Determinación de significancia<br>• Cálculo de intervalos de confianza<br>• Diseño de estudios|
|**Relaciones importantes**|• **↓ α → ↓ Error Tipo I, ↑ Error Tipo II**<br>• **Nivel de confianza = 1 - α**<br>• **α determina valores críticos**|
Ahora necesito entonces que definas diversos tipos de distribuciones (distribución normal, binomial, logarítmica, exponencial, poisson, etc) tal como ibas definiendo previamente los conceptos en sus propios cuadros, donde agregas más info como las aplicaciones, formulas y explicación de variables, para luego crear un cuadro general comparando los tipos de distribuciones