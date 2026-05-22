

Usando los datos del archivo SPSS Datos_Tareas_2026.sav (o bien, el mismo archivo en Excel), efectúe un EFA de los datos correspondientes a las variables predictoras y predichas, usando las técnicas y análisis vistos en el curso. Recuerde hacer un análisis descriptivo de los datos y apreciar normalidad de los datos. También recuerde que debe ver bien cuáles serían las variables predictoras, ya que puede haber una cadena de variables predictoras (i.e., una variable predice a otra, que a su vez, predice a otra). Por eso es conveniente apoyarse en teoría (literatura relevante). Por último, recuerde que cuando en un EFA no se extrae la cantidad postulada de factores (usando generalmente extracción de factores con eigenvalores mayor o igual a 1.0), uno puede extraer la cantidad de factores que uno estipule.
Debe entregar un informe impreso (y también en un archivo PDF) que describa lo que efectuó y sus resultados, discutiendo brevemente los resultados. El informe debe permitir reproducir los análisis efectuados y los resultados obtenidos. 


# Guía Paso a Paso: Análisis Factorial Exploratorio (EFA) en SPSS

Esta guía técnica proporciona el procedimiento estándar para la reducción de dimensionalidad y validación psicométrica mediante el Análisis Factorial Exploratorio (EFA). El objetivo primordial es identificar la estructura latente de los indicadores de gestión de mercadeo y logística, asegurando que las variables compuestas resultantes posean alta fidelidad estadística para modelos causales posteriores.

--------------------------------------------------------------------------------

## 1. Introducción al Marco Teórico del Análisis Factorial

El análisis factorial se fundamenta en el modelo clásico de medición: **X = T + e**. Bajo este paradigma, cualquier variable observada (X) se descompone en una "medida verdadera" o constructo latente (T) y un error de medición (e).

En el estudio de fenómenos complejos, como la eficiencia operativa en puntos de venta, las variables de interés no pueden medirse directamente. Por ello, empleamos **variables latentes** (factores) que se manifiestan a través de **variables observadas** (indicadores o _proxy variables_). El EFA permite reducir el "ruido" de medición que, de no ser tratado, provocaría una **atenuación de las relaciones** entre variables en modelos de regresión o ecuaciones estructurales (SEM).

### Indicadores del Caso de Estudio: Reposición Eficiente

Para este análisis, se utilizan indicadores evaluados en escalas Likert (1 a 7) centrados en dos dimensiones críticas:

- **Dimensión 1: Eficiencia de Mercaderistas**
    - Conocimiento de Productos.
    - Conocimiento de Planogramas.
    - Seguimiento de Planogramas.
    - Desempeño general del mercaderista.
    - Evaluación del supermercado al mercaderista.
- **Dimensión 2: Eficiencia de Operaciones Logísticas**
    - Productos llegan OK (Correctos).
    - Tiempo de llegada de productos (Puntualidad).
    - Productos llegan conforme y sin daños.
    - Retardo del ciclo dentro de límites (OK).

--------------------------------------------------------------------------------

## 2. Fase 1: Análisis Descriptivo y Supuestos de Normalidad

Antes de la extracción de factores, debemos verificar la distribución de los 9 indicadores mencionados. La medición se realiza usualmente en escalas de 1 (Muy malo) a 7 (Muy bueno).

### Pasos en SPSS:

1. Navegue a **Analizar > Estadísticos Descriptivos > Frecuencias**.
2. Traslade los indicadores de mercadeo y logística al cuadro de variables.
3. En **Gráficos**, seleccione **Histogramas** y active "Mostrar curva normal".
4. Para validar la normalidad univariante, use **Analizar > Estadísticos Descriptivos > Explorar**. En la pestaña **Gráficos**, seleccione "Gráficos de normalidad con pruebas" para obtener los **Gráficos Q-Q**.

**Nota Técnica:** Según la evidencia del caso, si se integran datos de encuestas con "datos duros" (variables continuas), estos últimos deben categorizarse previamente. No se recomienda mezclar niveles de medición métricos y categóricos directamente sin una estandarización o categorización previa de los datos continuos.

--------------------------------------------------------------------------------

## 3. Fase 2: Configuración Técnica del Análisis Factorial Exploratorio (EFA)

El motor de análisis se configurará bajo el método de **Factorización de Ejes Principales (PAF)**, el cual es el más robusto para identificar la varianza común cuando se sospecha de error de medición.

### Criterios de Validación Inicial:

- **Prueba de KMO (Kaiser-Meyer-Olkin):** Debe arrojar un valor **> 0.5 o 0.6** para confirmar que la matriz de datos es adecuada para la factorización.
- **Prueba de Bartlett:** Evalúa la hipótesis nula (H_0) de que las variables no están correlacionadas. Se requiere un **p-valor < 0.05** para rechazar la H_0 y proceder.

### Tabla de Configuración de Parámetros:

|   |   |
|---|---|
|Opción / Pestaña|Configuración Requerida|
|**Extracción**|Método: Factorización de ejes principales (PAF).|
|**Extracción**|Basado en Autovalores (Eigenvalues) > 1.0.|
|**Rotación**|Método: Varimax (Ortogonal).|
|**Descriptivos**|KMO y prueba de esfericidad de Bartlett; Matriz de correlaciones.|
|**Opciones**|Supresión de coeficientes pequeños (sugerido < 0.30) y ordenados por tamaño.|

**Nota Técnica Adicional:** Aunque el método PAF es el estándar, el análisis de **Máxima Verosimilitud (ML)** puede ser ejecutado como contraste. En este caso de estudio, el método ML sugirió que podrían existir más de dos factores latentes, un detalle a considerar en la discusión de resultados.

--------------------------------------------------------------------------------

## 4. Fase 3: Determinación de Factores y Rotación

La determinación del número de constructos se apoya en criterios matemáticos y visuales:

- **Gráfico de Sedimentación (Scree Plot):** Se deben retener los factores situados antes del punto de inflexión donde la curva comienza a aplanarse.
- **Regla de Autovalores (Eigenvalues):** Se extraen factores con valores **\lambda \ge 1.0**.
- **Rotación Varimax:** Se aplica para minimizar la complejidad de los factores, maximizando la varianza de las cargas. Esto permite que los 5 indicadores de "Mercaderistas" carguen en un factor y los 4 de "Logística" en otro, sin solapamientos significativos.

**Interpretación de Cargas Factoriales (Loadings):** Las cargas representan la correlación entre el indicador y el factor. Valores altos indican que el indicador es un buen proxy del constructo. Deben evitarse los _cross-loadings_ (indicadores que cargan en ambos factores con valores similares).

--------------------------------------------------------------------------------

## 5. Fase 4: Evaluación de la Confiabilidad de la Escala

Identificados los factores, validamos su consistencia interna mediante el **Alfa de Cronbach (****\alpha****)**. Este coeficiente indica qué proporción de la varianza es "medición verdadera". Por ejemplo, un \alpha = 0.70 implica que el 70% de la varianza es atribuible a la variable latente y el 30% es error.

- **Criterio de Nunnally (1978):** Un valor de \alpha \ge 0.70 es el mínimo aceptable.
- **Resultados del Caso:** El factor "Eficiencia Mercaderistas" obtuvo un **\alpha = 0.82**, mientras que "Eficiencia Logística" se situó entre **0.87 y 0.90**.

### Pasos en SPSS:

1. **Analizar > Escala > Análisis de fiabilidad**.
2. Agrupe los indicadores según su factor respectivo.
3. **Fórmula Conceptual:** \alpha = \frac{k}{k-1} \left( 1 - \frac{\sum \sigma^2_i}{\sigma^2_X} \right) _(Donde_ _k_ _es el número de indicadores)._

--------------------------------------------------------------------------------

## 6. Fase 5: Cálculo de Variables Finales (Constructos)

Habiendo validado la estructura y la confiabilidad, procedemos a la reducción de datos mediante la creación de variables compuestas (promedios aritméticos).

### Procedimiento en SPSS:

1. Vaya a **Transformar > Calcular variable**.
2. Use la función `MEAN` para agrupar los indicadores validados.

**Ejemplos de Sintaxis:**

- `Efic_Mercaderistas = MEAN(Conoc_Prod, Conoc_Plano, Seguim_Plano, Desemp_Gral, Eval_Super)`
- `Efic_Logistica = MEAN(Prod_OK, Tiempo_OK, Daños_OK, Retardo_OK)`

--------------------------------------------------------------------------------

## 7. Conclusiones y Reporte de Resultados

El análisis se considera exitoso si la estructura factorial es limpia (sin _cross-loadings_) y robusta. En este caso de estudio de supermercados, el modelo alcanzó un **58.5% de varianza explicada**, lo cual es un indicador de éxito para la validez del modelo de medición.

### Checklist de Verificación Final:

- [ ] ¿KMO > 0.6 y Bartlett significativo (p < 0.05)?
- [ ] ¿Se extrajeron los factores con Autovalores > 1.0?
- [ ] ¿La varianza explicada total se aproxima al **58.5%**?
- [ ] ¿Los 5 indicadores de mercadeo cargan claramente en el Factor 1?
- [ ] ¿Los 4 indicadores de logística cargan claramente en el Factor 2?
- [ ] ¿El Alfa de Cronbach es \ge 0.70 para ambos constructos?
- [ ] ¿Se calcularon las variables finales mediante el promedio aritmético (`MEAN`)?