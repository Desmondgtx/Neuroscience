

Usando los datos del archivo SPSS Datos_Tareas_2026.sav (o bien, el mismo archivo en Excel), efectúe un EFA de los datos correspondientes a las variables predictoras y predichas, usando las técnicas y análisis vistos en el curso. Recuerde hacer un análisis descriptivo de los datos y apreciar normalidad de los datos. También recuerde que debe ver bien cuáles serían las variables predictoras, ya que puede haber una cadena de variables predictoras (i.e., una variable predice a otra, que a su vez, predice a otra). Por eso es conveniente apoyarse en teoría (literatura relevante). Por último, recuerde que cuando en un EFA no se extrae la cantidad postulada de factores (usando generalmente extracción de factores con eigenvalores mayor o igual a 1.0), uno puede extraer la cantidad de factores que uno estipule.
Debe entregar un informe impreso (y también en un archivo PDF) que describa lo que efectuó y sus resultados, discutiendo brevemente los resultados. El informe debe permitir reproducir los análisis efectuados y los resultados obtenidos. 


# Guía Paso a Paso: Análisis Factorial Exploratorio (EFA) en SPSS
Preparación: Identificación de Variables e Indicadores

Para este análisis, trabajarás con las siguientes dimensiones medidas en escala Likert de 1 a 7:

- **Predictores (IV):**
    - **Uso de armas (PUA)**: `PUA_1`, `PUA_2`, `PUA_3`.
    - **Bandas organizadas (PBD)**: `PBD_1`, `PBD_2`, `PBD_3`.
    - **Violencia en delitos (PVD)**: `PVD_1`, `PVD_2`, `PVD_3`.
    - **Eficacia policial (PEP)**: `PEP_1`, `PEP_2`, `PEP_3`.
- **Variable Predicha (DV):**
    - **Percepción de inseguridad (PIN)**: `PIN_1`, `PIN_2`, `PIN_3`.

--------------------------------------------------------------------------------

2. Paso 1: Análisis Descriptivo y de Normalidad

Antes de extraer factores, debes verificar la calidad de los datos para los 15 indicadores.

1. Ve a `Analizar` > `Estadísticos descriptivos` > `Descriptivos`.
2. Selecciona todos los indicadores (`PUA_1` al `PIN_3`).
3. En `Opciones`, marca **Media**, **Desviación estándar**, **Mínimo** y **Máximo**.
    - _Objetivo:_ Confirmar que se usó toda la amplitud de la escala (1 a 7) y detectar posibles sesgos.
4. Ve a `Analizar` > `Estadísticos descriptivos` > `Frecuencias`. Pulsa `Gráficos` y elige **Histogramas** con la opción **Mostrar curva normal**.

--------------------------------------------------------------------------------

3. Paso 2: Análisis Factorial Exploratorio (EFA)

**Regla de oro:** No mezcles predictores con la variable predicha. Debes hacer el proceso por separado para respetar la causalidad teórica.

A. EFA de las Variables Predictoras (12 indicadores)

1. Ve a `Analizar` > `Reducción de dimensiones` > `Factor`.
2. Introduce los 12 indicadores predictores (`PUA_1-3`, `PBD_1-3`, `PVD_1-3`, `PEP_1-3`).
3. **Descriptivos:** Marca **KMO y prueba de esfericidad de Bartlett**.
4. **Extracción:**
    - Método: **Factorización de ejes principales (PAF)**.
    - Marca: **Gráfico de sedimentación (Scree Plot)**.
    - Mantener: **Basado en autovalor (eigenvalue) mayor que 1**.
    - _Nota:_ Si el análisis no arroja los 4 factores esperados, puedes forzar la extracción a "4" en esta misma ventana.
5. **Rotación:** Selecciona **Varimax** y marca **Solución rotada**.
6. **Interpretación:** Revisa la **Matriz de factores rotados**. Los indicadores deberían agruparse en sus constructos (ej. los 3 de PUA en un factor).

B. EFA de la Variable Predicha (3 indicadores)

1. Repite el proceso anterior, pero solo con los indicadores `PIN_1`, `PIN_2` y `PIN_3`.
2. Se espera que carguen en un único factor de "Inseguridad".

--------------------------------------------------------------------------------

4. Paso 3: Análisis de Confiabilidad (Alfa de Cronbach)

Debes verificar que cada grupo de indicadores mide su constructo de forma consistente (α≥0.70).

1. Ve a `Analizar` > `Escala` > `Análisis de fiabilidad`.
2. Realiza la prueba **cinco veces** (una por cada constructo):
    - Para PUA (3 ítems).
    - Para PBD (3 ítems).
    - Para PVD (3 ítems).
    - Para PEP (3 ítems).
    - Para PIN (3 ítems).

--------------------------------------------------------------------------------

5. Paso 4: Creación de Variables (Promedios)

Una vez validados, convierte los indicadores en variables únicas para el futuro modelo causal.

1. Ve a `Transformar` > `Calcular variable`.
2. Variable de destino: `Media_Inseguridad` (ejemplo).
3. Expresión numérica: `MEAN(PIN_1, PIN_2, PIN_3)`.
4. Repite para las otras 4 dimensiones (Uso de armas, Bandas, Violencia y Eficacia Policial).

--------------------------------------------------------------------------------

6. Sugerencia Teórica Importante para el Informe

El profesor destaca en las instrucciones que **podría haber una cadena de relación** entre los predictores. Antes de redactar tus conclusiones, reflexiona sobre si la percepción del "Uso de armas" y las "Bandas" en realidad causan la percepción de "Violencia", y si esta última es la que finalmente impacta en la "Inseguridad". Debes apoyar esta lógica con literatura