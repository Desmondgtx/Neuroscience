
## 1. Distribución Normal (Gaussiana)

|**Aspecto**|**Descripción**|
|---|---|
|**Definición**|Distribución continua simétrica en forma de campana que describe fenómenos influenciados por múltiples factores aleatorios e independientes. Es la distribución más importante en estadística.|
|**Tipo**|**Continua** - puede tomar cualquier valor en un rango|
|**Fórmula (Función de densidad)**|f(x) = (1/(σ√(2π))) × e^(-(x-μ)²/(2σ²))|
|**Parámetros**|• **μ (mu):** Media poblacional - centro de la distribución<br>• **σ (sigma):** Desviación estándar - dispersión de los datos<br>• **σ²:** Varianza|
|**Notación**|X ~ N(μ, σ²)|
|**Características clave**|• Simétrica respecto a la media<br>• Media = Mediana = Moda<br>• Forma de campana<br>• Asíntotas en ambos extremos<br>• Total área bajo la curva = 1<br>• Regla 68-95-99.7|
|**Rango de valores**|-∞ < x < +∞ (teóricamente todos los números reales)|
|**Media y Varianza**|• **E(X) = μ**<br>• **Var(X) = σ²**|
|**Aplicaciones**|• Alturas y pesos de poblaciones<br>• Errores de medición<br>• Puntuaciones en test estandarizados (IQ, SAT)<br>• Fenómenos naturales (temperatura, presión)<br>• Análisis de procesos industriales<br>• Modelos financieros (retornos de inversión)<br>• Biología (características morfológicas)|
|**Estandarización**|**Z = (X - μ)/σ** transforma a N(0,1) - distribución normal estándar|
|**Importancia**|Base del Teorema del Límite Central, fundamental para inferencia estadística|

---

## 2. Distribución Binomial

|**Aspecto**|**Descripción**|
|---|---|
|**Definición**|Distribución discreta que modela el número de éxitos en n ensayos independientes de Bernoulli, donde cada ensayo tiene solo dos resultados posibles (éxito/fracaso) con probabilidad constante.|
|**Tipo**|**Discreta** - solo valores enteros (0, 1, 2, ..., n)|
|**Fórmula (Función de probabilidad)**|P(X = k) = C(n,k) × p^k × (1-p)^(n-k)<br>Donde C(n,k) = n!/(k!(n-k)!)|
|**Parámetros**|• **n:** Número de ensayos independientes<br>• **p:** Probabilidad de éxito en cada ensayo<br>• **k:** Número de éxitos observados (0 ≤ k ≤ n)<br>• **q = 1-p:** Probabilidad de fracaso|
|**Notación**|X ~ B(n, p) o Binomial(n, p)|
|**Características clave**|• Ensayos independientes<br>• Probabilidad constante<br>• Solo dos resultados posibles<br>• Número fijo de ensayos<br>• Simétrica cuando p = 0.5<br>• Sesgada cuando p ≠ 0.5|
|**Rango de valores**|X ∈ {0, 1, 2, ..., n}|
|**Media y Varianza**|• **E(X) = n × p**<br>• **Var(X) = n × p × (1-p)**|
|**Aplicaciones**|• Control de calidad (artículos defectuosos)<br>• Medicina (pacientes que responden a tratamiento)<br>• Marketing (clientes que compran)<br>• Encuestas (respuestas sí/no)<br>• Lanzamiento de monedas o dados<br>• Pruebas de efectividad de vacunas<br>• Tasas de conversión en e-commerce|
|**Aproximación Normal**|Cuando **n×p ≥ 5** y **n×(1-p) ≥ 5**, se puede aproximar con N(np, np(1-p))|
|**Caso especial**|Cuando n=1, se convierte en **Distribución de Bernoulli**|

---

## 3. Distribución de Poisson

|**Aspecto**|**Descripción**|
|---|---|
|**Definición**|Distribución discreta que modela el número de eventos que ocurren en un intervalo fijo de tiempo o espacio, cuando estos eventos ocurren independientemente a una tasa promedio constante.|
|**Tipo**|**Discreta** - valores enteros no negativos (0, 1, 2, 3, ...)|
|**Fórmula (Función de probabilidad)**|P(X = k) = (λ^k × e^(-λ))/k!<br>Donde e ≈ 2.71828|
|**Parámetros**|• **λ (lambda):** Tasa promedio de ocurrencia en el intervalo<br>• **k:** Número de eventos observados (k ≥ 0)|
|**Notación**|X ~ Poisson(λ)|
|**Características clave**|• Eventos raros en intervalo grande<br>• Eventos independientes<br>• Tasa constante<br>• Media = Varianza = λ<br>• Sesgada a la derecha (cuando λ es pequeño)<br>• Se aproxima a normal cuando λ es grande|
|**Rango de valores**|X ∈ {0, 1, 2, 3, ...} (teóricamente infinito)|
|**Media y Varianza**|• **E(X) = λ**<br>• **Var(X) = λ**|
|**Aplicaciones**|• Llamadas telefónicas por hora en call center<br>• Accidentes de tráfico por mes<br>• Clientes que llegan a un banco por hora<br>• Errores de impresión por página<br>• Mutaciones genéticas por secuencia<br>• Visitas a un sitio web por minuto<br>• Radioactividad (desintegraciones por segundo)<br>• Defectos en manufactura|
|**Aproximación Normal**|Cuando **λ ≥ 10**, se puede aproximar con N(λ, λ)|
|**Relación con Binomial**|Límite de Binomial cuando n→∞, p→0, y np=λ permanece constante|

---

## 4. Distribución Exponencial

|**Aspecto**|**Descripción**|
|---|---|
|**Definición**|Distribución continua que modela el tiempo de espera entre eventos en un proceso de Poisson. Describe el tiempo hasta que ocurre el próximo evento.|
|**Tipo**|**Continua** - valores no negativos|
|**Fórmula (Función de densidad)**|f(x) = λ × e^(-λx) para x ≥ 0<br>**Función de distribución:** F(x) = 1 - e^(-λx)|
|**Parámetros**|• **λ (lambda):** Tasa de ocurrencia (eventos por unidad de tiempo)<br>• **β = 1/λ:** Tiempo promedio entre eventos (escala)|
|**Notación**|X ~ Exp(λ) o Exponencial(λ)|
|**Características clave**|• Sin memoria: P(X > s+t|
|**Rango de valores**|0 ≤ x < ∞|
|**Media y Varianza**|• **E(X) = 1/λ = β**<br>• **Var(X) = 1/λ² = β²**<br>• **Desviación estándar = Media**|
|**Aplicaciones**|• Tiempo entre llamadas telefónicas<br>• Vida útil de componentes electrónicos<br>• Tiempo entre llegadas de clientes<br>• Duración de llamadas telefónicas<br>• Tiempo de servicio en sistemas de colas<br>• Tiempo entre fallas en sistemas<br>• Teoría de confiabilidad<br>• Supervivencia y análisis de riesgos|
|**Propiedad sin memoria**|El tiempo futuro de espera no depende del tiempo ya transcurrido|
|**Relación con Poisson**|Si eventos siguen Poisson(λ), entonces el tiempo entre eventos sigue Exp(λ)|

---

## 5. Distribución Logarítmica Normal (Log-Normal)

|**Aspecto**|**Descripción**|
|---|---|
|**Definición**|Distribución continua donde el logaritmo natural de la variable sigue una distribución normal. Modela variables positivas con sesgo a la derecha.|
|**Tipo**|**Continua** - solo valores positivos|
|**Fórmula (Función de densidad)**|f(x) = (1/(xσ√(2π))) × e^(-(ln(x)-μ)²/(2σ²)) para x > 0|
|**Parámetros**|• **μ (mu):** Media del logaritmo natural de X<br>• **σ (sigma):** Desviación estándar del logaritmo natural de X<br>• Si Y = ln(X), entonces Y ~ N(μ, σ²)|
|**Notación**|X ~ LogNormal(μ, σ²) o LN(μ, σ²)|
|**Características clave**|• Siempre sesgada a la derecha<br>• Solo valores positivos<br>• Media > Mediana > Moda<br>• Forma de campana asimétrica<br>• Cola derecha más larga|
|**Rango de valores**|0 < x < ∞|
|**Media y Varianza**|• **E(X) = e^(μ + σ²/2)**<br>• **Var(X) = [e^(σ²) - 1] × e^(2μ + σ²)**<br>• **Mediana = e^μ**|
|**Aplicaciones**|• Ingresos y salarios<br>• Precios de acciones y activos financieros<br>• Tamaños de partículas<br>• Concentraciones de contaminantes<br>• Tiempo de recuperación de enfermedades<br>• Tamaño de ciudades<br>• Longitud de palabras en textos<br>• Distribución de riqueza|
|**Transformación**|Si X ~ LogNormal(μ, σ²), entonces **ln(X) ~ N(μ, σ²)**|
|**Propiedad multiplicativa**|Producto de variables log-normales es log-normal|

---

## 6. Distribución Uniforme

|**Aspecto**|**Descripción**|
|---|---|
|**Definición**|Distribución donde todos los valores en un intervalo tienen la misma probabilidad de ocurrir. Representa total incertidumbre dentro de límites conocidos.|
|**Tipo**|**Continua** o **Discreta**|
|**Fórmula (Continua)**|f(x) = 1/(b-a) para a ≤ x ≤ b<br>f(x) = 0 en otro caso|
|**Fórmula (Discreta)**|P(X = x) = 1/n para cada uno de los n valores posibles|
|**Parámetros**|• **a:** Límite inferior<br>• **b:** Límite superior<br>• **n:** Número de valores posibles (discreta)|
|**Notación**|X ~ U(a, b) o Uniforme(a, b)|
|**Características clave**|• Probabilidad constante en todo el rango<br>• Forma rectangular<br>• Simétrica<br>• Media en el punto medio del intervalo|
|**Rango de valores**|a ≤ x ≤ b (continua) o valores discretos específicos|
|**Media y Varianza (Continua)**|• **E(X) = (a+b)/2**<br>• **Var(X) = (b-a)²/12**|
|**Aplicaciones**|• Generación de números aleatorios<br>• Simulaciones Monte Carlo<br>• Modelado de incertidumbre total<br>• Procesos de redondeo<br>• Llegada aleatoria dentro de intervalo<br>• Distribución inicial en análisis bayesiano<br>• Juegos de azar (dados, ruleta)|
|**Función de distribución**|F(x) = (x-a)/(b-a) para a ≤ x ≤ b|
|**Caso especial**|U(0,1) es la distribución uniforme estándar|

---

## 7. Distribución t de Student

|**Aspecto**|**Descripción**|
|---|---|
|**Definición**|Distribución continua similar a la normal pero con colas más pesadas. Surge al estimar la media de una población normalmente distribuida con muestra pequeña y desviación estándar desconocida.|
|**Tipo**|**Continua** - todos los números reales|
|**Fórmula (Función de densidad)**|f(t) = [Γ((ν+1)/2)/(√(νπ)Γ(ν/2))] × [1 + t²/ν]^(-(ν+1)/2)|
|**Parámetros**|• **ν (nu):** Grados de libertad (usualmente n-1)<br>• Γ: Función gamma|
|**Notación**|t ~ t(ν) o t-Student(ν)|
|**Características clave**|• Simétrica respecto a cero<br>• Colas más pesadas que la normal<br>• Se aproxima a normal cuando ν → ∞<br>• Forma de campana<br>• Mayor variabilidad con menos grados de libertad|
|**Rango de valores**|-∞ < t < +∞|
|**Media y Varianza**|• **E(t) = 0** (para ν > 1)<br>• **Var(t) = ν/(ν-2)** (para ν > 2)<br>• Varianza indefinida para ν ≤ 2|
|**Aplicaciones**|• Pruebas t para medias con muestras pequeñas (n < 30)<br>• Intervalos de confianza para medias<br>• Regresión lineal (significancia de coeficientes)<br>• Comparación de dos medias<br>• Análisis cuando σ es desconocida|
|**Convergencia**|Cuando ν ≥ 30, t(ν) ≈ N(0,1)|
|**Origen**|William Sealy Gosset (seudónimo "Student") en 1908|

---

## 8. Distribución Chi-Cuadrado (χ²)

|**Aspecto**|**Descripción**|
|---|---|
|**Definición**|Distribución continua que representa la suma de cuadrados de variables normales estándar independientes. Fundamental en pruebas de bondad de ajuste e independencia.|
|**Tipo**|**Continua** - solo valores no negativos|
|**Fórmula (Función de densidad)**|f(x) = [x^(k/2-1) × e^(-x/2)] / [2^(k/2) × Γ(k/2)] para x ≥ 0|
|**Parámetros**|• **k:** Grados de libertad (número de variables normales al cuadrado)<br>• Γ: Función gamma|
|**Notación**|X ~ χ²(k) o Chi-cuadrado(k)|
|**Características clave**|• Siempre sesgada a la derecha<br>• Solo valores no negativos<br>• Se aproxima a normal cuando k es grande<br>• Forma cambia según grados de libertad<br>• Aditiva: suma de χ² independientes es χ²|
|**Rango de valores**|0 ≤ x < ∞|
|**Media y Varianza**|• **E(X) = k**<br>• **Var(X) = 2k**<br>• **Moda = k-2** (para k ≥ 2)|
|**Aplicaciones**|• Pruebas de bondad de ajuste<br>• Pruebas de independencia (tablas de contingencia)<br>• Pruebas de varianza<br>• Intervalos de confianza para varianzas<br>• Estadística Q de Cochran<br>• Análisis de confiabilidad<br>• Genética (pruebas de Hardy-Weinberg)|
|**Relación con Normal**|Si Z ~ N(0,1), entonces Z² ~ χ²(1)|
|**Aproximación Normal**|Cuando k > 30, χ²(k) ≈ N(k, 2k)|

---

## 9. Distribución F de Fisher-Snedecor

|**Aspecto**|**Descripción**|
|---|---|
|**Definición**|Distribución continua que representa el cociente de dos variables chi-cuadrado independientes, cada una dividida por sus grados de libertad. Fundamental en ANOVA y comparación de varianzas.|
|**Tipo**|**Continua** - solo valores positivos|
|**Fórmula (Función de densidad)**|f(x) = [√((d₁x)^d₁ × d₂^d₂) / ((d₁x + d₂)^(d₁+d₂))] / [x × B(d₁/2, d₂/2)] para x > 0|
|**Parámetros**|• **d₁:** Grados de libertad del numerador<br>• **d₂:** Grados de libertad del denominador<br>• B: Función beta|
|**Notación**|F ~ F(d₁, d₂)|
|**Características clave**|• Siempre sesgada a la derecha<br>• Solo valores positivos<br>• Asimétrica<br>• Forma depende de ambos grados de libertad<br>• No conmutativa: F(d₁,d₂) ≠ F(d₂,d₁)|
|**Rango de valores**|0 < F < ∞|
|**Media y Varianza**|• **E(F) = d₂/(d₂-2)** (para d₂ > 2)<br>• **Var(F) = [2d₂²(d₁+d₂-2)] / [d₁(d₂-2)²(d₂-4)]** (para d₂ > 4)<br>• **Moda = [d₂(d₁-2)] / [d₁(d₂+2)]** (para d₁ > 2)|
|**Aplicaciones**|• ANOVA (análisis de varianza)<br>• Comparación de varianzas de dos poblaciones<br>• Regresión múltiple (significancia global)<br>• Pruebas de homogeneidad de varianzas<br>• Diseño de experimentos<br>• Control de calidad|
|**Relación con t**|Si t ~ t(ν), entonces t² ~ F(1, ν)|
|**Propiedad de reciprocidad**|Si F ~ F(d₁, d₂), entonces 1/F ~ F(d₂, d₁)|

---

## 10. Distribución Geométrica

|**Aspecto**|**Descripción**|
|---|---|
|**Definición**|Distribución discreta que modela el número de ensayos de Bernoulli necesarios hasta obtener el primer éxito. Es la versión discreta "sin memoria" análoga a la exponencial.|
|**Tipo**|**Discreta** - valores enteros positivos|
|**Fórmula (Función de probabilidad)**|P(X = k) = (1-p)^(k-1) × p<br>Versión alternativa: P(X = k) = (1-p)^k × p (número de fracasos antes del éxito)|
|**Parámetros**|• **p:** Probabilidad de éxito en cada ensayo<br>• **q = 1-p:** Probabilidad de fracaso|
|**Notación**|X ~ Geom(p) o Geométrica(p)|
|**Características clave**|• Propiedad sin memoria (discreta)<br>• Monotónicamente decreciente<br>• Ensayos independientes<br>• Probabilidad constante<br>• Siempre sesgada a la derecha|
|**Rango de valores**|X ∈ {1, 2, 3, ...} o {0, 1, 2, ...} según definición|
|**Media y Varianza**|• **E(X) = 1/p**<br>• **Var(X) = (1-p)/p²**|
|**Aplicaciones**|• Número de intentos hasta primera venta<br>• Lanzamientos de dado hasta obtener un 6<br>• Intentos hasta primer defecto en producción<br>• Llamadas hasta primera respuesta<br>• Intentos hasta primer éxito en experimento<br>• Juegos de azar (intentos hasta ganar)|
|**Propiedad sin memoria**|P(X > m+n|
|**Relación con otras**|Caso especial de distribución binomial negativa|

---

# CUADRO COMPARATIVO GENERAL

## Clasificación por Tipo de Variable

|**Distribución**|**Tipo**|**Rango de Valores**|**Parámetros**|**Media**|**Aplicación Principal**|
|---|---|---|---|---|---|
|**Normal**|Continua|-∞ a +∞|μ, σ²|μ|Fenómenos naturales, errores|
|**Binomial**|Discreta|0 a n|n, p|np|Ensayos éxito/fracaso|
|**Poisson**|Discreta|0 a ∞|λ|λ|Eventos raros en tiempo/espacio|
|**Exponencial**|Continua|0 a ∞|λ|1/λ|Tiempos de espera|
|**Log-Normal**|Continua|0 a ∞|μ, σ²|e^(μ+σ²/2)|Datos positivos sesgados|
|**Uniforme**|Continua/Discreta|[a, b]|a, b|(a+b)/2|Incertidumbre total|
|**t-Student**|Continua|-∞ a +∞|ν|0|Muestras pequeñas|
|**Chi-Cuadrado**|Continua|0 a ∞|k|k|Bondad de ajuste, varianzas|
|**F**|Continua|0 a ∞|d₁, d₂|d₂/(d₂-2)|ANOVA, comparación varianzas|
|**Geométrica**|Discreta|1 a ∞|p|1/p|Ensayos hasta primer éxito|

---

## Comparación por Características

|**Característica**|**Distribuciones Aplicables**|
|---|---|
|**Simétrica**|Normal, Uniforme, t-Student|
|**Sesgada a la derecha**|Poisson (λ pequeño), Exponencial, Log-Normal, Chi-Cuadrado, F, Geométrica|
|**Solo valores positivos**|Exponencial, Log-Normal, Chi-Cuadrado, F, Poisson, Binomial, Geométrica|
|**Propiedad sin memoria**|Exponencial (continua), Geométrica (discreta)|
|**Forma de campana**|Normal, t-Student (modificada)|
|**Se aproxima a Normal**|Binomial (n grande), Poisson (λ grande), t-Student (ν grande), Chi-Cuadrado (k grande)|

---

## Relaciones entre Distribuciones

```
Normal (μ, σ²)
    ↓
    ├─→ Z² ~ Chi-Cuadrado(1)
    ├─→ t-Student (n pequeño, σ desconocida)
    └─→ Base para muchas otras

Binomial(n, p) ──(n→∞, p→0, np=λ)──→ Poisson(λ)
                     ↓
              (n grande) → Normal

Poisson(λ) ←──→ Exponencial(λ)
(número eventos)    (tiempo entre eventos)

Geométrica(p) = caso especial de Binomial Negativa

Chi-Cuadrado: suma de Normales² estándar
    ↓
    F: cociente de dos Chi-Cuadrado

t²(ν) ~ F(1, ν)

ln(X) ~ Normal → X ~ Log-Normal
```

---

## Cuándo Usar Cada Distribución

|**Situación**|**Distribución Recomendada**|
|---|---|
|Variable continua, fenómeno natural|**Normal**|
|Conteo de éxitos en n ensayos|**Binomial**|
|Eventos raros por unidad de tiempo|**Poisson**|
|Tiempo hasta el próximo evento|**Exponencial**|
|Variable positiva con sesgo derecho|**Log-Normal**|
|Total incertidumbre en rango|**Uniforme**|
|Media con muestra pequeña (n<30)|**t-Student**|
|Prueba de independencia/bondad|**Chi-Cuadrado**|
|Comparar varianzas, ANOVA|**F**|
|Ensayos hasta primer éxito|**Geométrica**|

---

## Teoremas Importantes

### **Teorema del Límite Central**

La suma (o media) de muchas variables independientes tiende a una distribución **Normal**, independientemente de sus distribuciones originales.

### **Aproximaciones**

- **Binomial → Normal:** cuando np ≥ 5 y n(1-p) ≥ 5
- **Poisson → Normal:** cuando λ ≥ 10
- **t → Normal:** cuando ν ≥ 30
- **Chi-Cuadrado → Normal:** cuando k > 30

### **Aditividad**

- Suma de Normales independientes es Normal
- Suma de Poisson independientes es Poisson
- Suma de Chi-Cuadrado independientes es Chi-Cuadrado
- Producto de Log-Normales es Log-Normal