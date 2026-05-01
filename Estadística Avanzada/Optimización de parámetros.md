
# Clase 5 de Estadística Avanzada

Clase 4: [[Regresión Múltiple]]


## Optimizar hiperparámetros
- Aproximación de fuerza bruta
	- Para cada hiperparámetro hago muchas iteraciones train-test al azar, calculo una medida de performance promedio para ambos conjuntos y los voy poniendo en una grilla


## Observaciones
1) Cuando divido los set de datos (en training y testing), toda transformación que quiera hacer, debo hacerla por separado a cada set
	- De lo contrario se puede transferir información desde el set de entrenamiento al de evaluación del modelo y aumentar artificialmente la performance del modelo
2) Cuando optimizo hiperparámetros, encuentro la performance máxima de la grilla
	- Para obtener un estimativo que NO esté inflado, necesito seleccionar hiperparámetros que me dan esa performance máxima, entrenar al modelo con ello y evaluar la performance en otro dataset distinto


## Curva ROC
![[making-sense-of-the-roc-curve-v0-6zkx70alsv0e1 (1).webp|355]]

### AUC como criterio de performance
AUC cercano a 1: Performance perfecta
AUC cercano a 0.5: Performance a nivel chance


## Problemas con train-test split
- La performance estimada depende de si tuve suerte y quedaron datos muy informativos en el conjunto de entrenamiento
- Si por ejemplo divido los atos 70-30 (training-split)


### Validación cruzada estratificada
Se dividen los datos en 5 partes
- Se entrena el modelo con 4 partes y se evalua con la quinta
- Luego se toman otras 4 partes y se evalua con otra quinta
- Así sucesivamente


### Inclusión de features
- No se trata de sumar features a lo loco
- Select K-Best: Obtengo una medida de qué tan diferente es el feature entre las dos clases y luego me quedo con los features que tienen máximo score


## Incluir datos categóricos
- One-hot encoding: Crear un feature binario por cada valor posible del dato categórico, que vale 1 si ese sample tiene el valor posible y 0 sino

![[mtimfxh.png|614]]



## Arbol de decisión (Random Forest)
Algoritmo de machine learning supervisado, que construye árboles de decisiones para generar predicciones


### Cómo se construye un árbol de decisión
- Seleccionamos un feature muy informativo y le preguntamos si cumple o no una condición
	-  La raíz se escoge como el feature más importante (se explora de forma exhaustiva)
- De aquí se desprenden:
	- Si se cumple dicha condición
	- Si no se cumple dicha condición
- Para cada "hijo" o "nodo" volvemos a seleccionar un feature y una condición que se cumple
- Podemos seguir con tantos features como


### Cómo elegimos un "feature informativo"
- Depende de si es un problema de regresión o clasificación:
	- Clasificación: Buscamos un nodo que separe los datos en grupos lo más "puros" posibles
	- Regresión: Buscamos nodos que separen los datos en grupos donde el error de predicción sea bajo


#### Variables categóricas
- De los nodos se desprenden si se cumple o no la variable categórica


#### Variables numéricas
- Con variables numéricas se elige el corte de los nodos en umbrales del rango de la variable


### Medidas de impureza
#### Coeficiente de Gini
$$G = \sum_{k=1}^K \hat{P}_{mk}(1-\hat{P}_{mk})$$

#### Entropía
$$D = -\sum_{k=1}^{K} \hat{p}_{mk} \log \hat{p}_{mk}$$

#### Ejemplo
![[Captura de pantalla 2026-05-01 193858.png|624]]
![[Captura de pantalla 2026-05-01 193951.png|625]]

### Algoritmo:
- Buscamos el feature y la condición que minimice la impireza del árbol y fijamos ese feature como raíz
- Para cada uno de los dos nodos que se desprenden de la raíz buscamos el feature y la condición que disminuya la impureza de ese subconjunto
- Así siguiendo hasta que cada dato quede denro de una hoja pura, o bien hasta que se cumple algún criterio de convergencia
- Damos como predicción el promedio de valor


### Ventajas de los árboles de decisión
- Fáciles de interpretar: se asemeja bastante a la forma en la que enfrentamos un problema
- No hay que preocuparse por diferencias de escala en datos numéricos
- No hay que hacer one-hot-encoding de features categóricas
- Manejan datos faltantes de una forma natural
- Permite incluir todo tipo de datos:


### Desventajas de los árboles de decisión
- Baja performance
- Árboles de mucha profundidad tienden a hacer overfitting
- Baja performance si justo arrancamos con un feature ruidoso
- Sesgos hacia clases más dominantes (datasets no balanceados)


### Como evitar el overfitting
- Fijar la profundidad del arbol
- Fijar la cantidad de hojas
- *Regularización* = cost complexity pruning. Penaliza árboles con muchas hojas al buscar minimizar la siguiente función:
$$\sum_{m=1}^|T| \sum{i: x_i \in R_m} (y_i - \hat{y}_{R_{m}})^2 + \alpha |T|$$
Donde: 
$(y_i - \hat{y}_{R_{m}})^2$ = Suma de los residuos al cuadrado
$\alpha$ = Constante de regularización
$|T|$ = Número d ehojas


### Resumen
- La idea es encontrar condiciones que separen los datos en grupos.
- Los árboles de decisión pueden crecer tanto a punto de overfittear, por lo tanto es bueno tener en cuenta las técnicas para evitar esto
- Mejor que un único árbol es un bosque
- Random Forest es un algoritmo mucho más poderoso que los árboles individuales



Clase 6: [[]]