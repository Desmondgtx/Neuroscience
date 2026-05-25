

Usando los datos del archivo SPSS Datos_Tareas_2026.sav (o bien, el mismo archivo en Excel), efectúe un EFA de los datos correspondientes a las variables predictoras y predichas, usando las técnicas y análisis vistos en el curso. Recuerde hacer un análisis descriptivo de los datos y apreciar normalidad de los datos. También recuerde que debe ver bien cuáles serían las variables predictoras, ya que puede haber una cadena de variables predictoras (i.e., una variable predice a otra, que a su vez, predice a otra). Por eso es conveniente apoyarse en teoría (literatura relevante). Por último, recuerde que cuando en un EFA no se extrae la cantidad postulada de factores (usando generalmente extracción de factores con eigenvalores mayor o igual a 1.0), uno puede extraer la cantidad de factores que uno estipule.
Debe entregar un informe impreso (y también en un archivo PDF) que describa lo que efectuó y sus resultados, discutiendo brevemente los resultados. El informe debe permitir reproducir los análisis efectuados y los resultados obtenidos. 




## Pasos en SPSS (interfaz gráfica)

> Guía de clics para reproducir todos los análisis de la Tarea 1 (EFA) del curso de Estadística Avanzada. Datos: `Datos_Tareas_2026.sav` · N = 225 · escala Likert 1–7. Variables: PUA (1–3), PBD (1–3), PVD (1–3), PEP (1–3) = predictoras · PIN (1–3) = predicha.

---

## A. Análisis descriptivo

1. `Analizar` > `Estadísticos descriptivos` > `Descriptivos`.
2. Pasa los **15 indicadores** (PUA_1-3, PBD_1-3, PVD_1-3, PEP_1-3, PIN_1-3) al cuadro de variables.
3. Botón `Opciones`: marca `Media`, `Desviación estándar`, `Mínimo`, `Máximo`. (Deja **sin** marcar asimetría y curtosis.)
4. `Continuar` > `Aceptar`.

---

## B. Normalidad

### B.1 Histogramas con curva normal

1. `Analizar` > `Estadísticos descriptivos` > `Frecuencias`.
2. Pasa los 15 indicadores.
3. Botón `Gráficos` > marca `Histogramas` y `Mostrar curva normal en el histograma`.
4. `Continuar` > `Aceptar`.

### B.2 Gráficos Q-Q

1. `Analizar` > `Estadísticos descriptivos` > `Gráficos Q-Q`.
2. Pasa los 15 indicadores.
3. Deja la distribución de prueba en `Normal` (valor por defecto).
4. `Aceptar`.

---

## C. Fiabilidad (Alfa de Cronbach) — repetir 5 veces

> Una corrida por escala: PVD, PIN, PUA, PBD, PEP.

1. `Analizar` > `Escala` > `Análisis de fiabilidad`.
2. Introduce los **3 ítems de una escala** (p. ej. PVD_1, PVD_2, PVD_3).
3. Modelo: `Alfa`.
4. Botón `Estadísticos`: en _Descriptivos para_ marca `Elemento`, `Escala` y `Escala si se elimina el elemento`; en _Inter-elementos_ marca `Correlaciones`.
5. `Continuar` > `Aceptar`.
6. **Repite** los pasos 1–5 para PIN, PUA, PBD y PEP.

---

## D. EFA de las variables predictoras (12 indicadores) — PAF + Kaiser

1. `Analizar` > `Reducción de dimensiones` > `Factor`.
2. Introduce los **12 indicadores predictores** (PUA_1-3, PBD_1-3, PVD_1-3, PEP_1-3). **No incluyas PIN.**
3. Botón `Descriptivos`: marca `Solución inicial` y, en _Adecuación del muestreo_, `KMO y prueba de esfericidad de Bartlett`. > `Continuar`.
4. Botón `Extracción`:
    - Método: `Factorización de eje principal`.
    - En _Extraer_: selecciona `Basado en autovalor` con `Autovalores mayores que: 1`.
    - Marca `Gráfico de sedimentación`. > `Continuar`.
5. Botón `Rotación`: marca `Varimax` y `Solución rotada`. > `Continuar`.
6. `Aceptar`.

---

## E. EFA de las predictoras — Máxima Verosimilitud (ML)

> Igual que D, pero cambia el método de extracción. Esto añade la **prueba de bondad de ajuste** (chi-cuadrado).

1. `Analizar` > `Reducción de dimensiones` > `Factor`.
2. Mismos 12 indicadores predictores.
3. Botón `Descriptivos`: `KMO y prueba de esfericidad de Bartlett`, `Solución inicial`, y opcionalmente `Descriptivos univariados`. > `Continuar`.
4. Botón `Extracción`: Método = `Máxima verosimilitud`; `Autovalores mayores que 1`. > `Continuar`.
5. Botón `Rotación`: `Varimax` + `Solución rotada`. > `Continuar`.
6. `Aceptar`.

---

## F. (Opcional) EFA forzado a 4 factores — análisis de sensibilidad

> Para justificar teóricamente los 4 constructos postulados. Solo cambia el criterio de extracción.

1. `Analizar` > `Reducción de dimensiones` > `Factor`.
2. Mismos 12 indicadores predictores.
3. Botón `Descriptivos`: `KMO y Bartlett`. > `Continuar`.
4. Botón `Extracción`:
    - Método: `Factorización de eje principal` (o ML, para ser consistente con E).
    - En _Extraer_: selecciona `Número fijo de factores` y escribe `4`.
    - > `Continuar`.
        
5. Botón `Rotación`: `Varimax` + `Solución rotada`. > `Continuar`.
6. `Aceptar`.

---

## G. EFA de la variable predicha PIN (3 indicadores)

1. `Analizar` > `Reducción de dimensiones` > `Factor`.
2. Introduce **solo PIN_1, PIN_2, PIN_3**.
3. Botón `Descriptivos`: `KMO y Bartlett`, `Solución inicial`. > `Continuar`.
4. Botón `Extracción`: `Factorización de eje principal`, `Autovalores mayores que 1`. > `Continuar`.
5. Botón `Rotación`: `Varimax`. > `Continuar`.
6. `Aceptar`.

> Resultado esperado: **un solo factor**. SPSS avisará que "la solución no se puede rotar" — esto es **normal y esperado** cuando hay un único factor, no es un error.

---

## H. Crear las variables-promedio de cada constructo

> Una variable nueva por constructo, promediando sus 3 ítems.

1. `Transformar` > `Calcular variable`.
2. _Variable de destino_: escribe el nombre (p. ej. `PVD`).
3. _Expresión numérica_: `MEAN(PVD_1, PVD_2, PVD_3)`.
4. `Aceptar`.
5. Repite para: `PUA = MEAN(PUA_1,PUA_2,PUA_3)`, `PBD = MEAN(PBD_1,PBD_2,PBD_3)`, `PEP = MEAN(PEP_1,PEP_2,PEP_3)`, `PIN = MEAN(PIN_1,PIN_2,PIN_3)`.

> Para el modelo de 1 predictor combinado (`VD_v2`), también: `VD_v2 = MEAN(PUA, PBD, PVD)` (promedio de las tres predictoras de "amenaza").

---

## I. Regresión lineal — los 3 modelos OLS

> En las tres, la **dependiente** es siempre `PIN`. Cambian solo los predictores.

### Pasos comunes (interfaz)

1. `Analizar` > `Regresión` > `Lineales`.
2. _Dependiente_: `PIN`.
3. _Independientes_: según el modelo (ver abajo).
4. Botón `Estadísticos`: marca `Estimaciones` y `Ajuste del modelo`. > `Continuar`.
5. `Aceptar`.

### Gráfico de dispersión (para cada regresión, menos la última si prefieres)

1. `Gráficos` > `Cuadros de diálogo antiguos` > `Dispersión/Puntos` > `Dispersión simple` > `Definir`.
2. _Eje Y_: `PIN`. _Eje X_: el predictor (o el promedio combinado).
3. `Aceptar`.

### Modelo 1 — Las 4 predictoras

- _Independientes_: `PVD`, `PUA`, `PBD`, `PEP`.

### Modelo 2 — Solo las 3 de "amenaza" (sin PEP)

- _Independientes_: `PVD`, `PUA`, `PBD`.

### Modelo 3 — Predictor único combinado

- _Independiente_: `VD_v2` (= promedio de PUA, PBD, PVD).

---

## Resumen del flujo

```
Descriptivos → Normalidad (hist + Q-Q) → Fiabilidad (5 alfas)
   → EFA predictoras [PAF Kaiser] → EFA predictoras [ML]
   → (opcional EFA 4 factores) → EFA PIN
   → Variables-promedio → 3 Regresiones OLS
```