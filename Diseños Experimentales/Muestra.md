
## Clase 2 de Diseños Experimentales

Clase 1: [[Pre-registro]]


## Blinding

### Randomización simple:
- Participantes aleatorizados

### Randomización por bloque:
- Segmentar a la población y luego asignar los participantes a los grupos
- Balancear los grupos

### Randomización estratificada:
- La población se divide en estratos (factores apropiados)
- Luego los estratos se dividen en sub grupos

### Randomización adaptativa covariada:
- Tener en cuenta los participantes que ya tengo el los grupos para luego asignar nuevos participantes



## Sampling
### Población del sampleo
- Criterios de inclusión 
	- Qué población me interesa
- Criterios de exclusión 
	- Quienes no pueden participar)
	- Criterios éticos
	- Medicación que utiliza determinado participante
- Criterios de reclutamiento
	- Qué población termino estudiado

![[Captura de pantalla 2026-05-21 150558.png]]

Donde:
a) Sujetos reclutados
b) Sujetos que podría haber reclutado
c) Se reclutaron pero se excluyeron
d) Podría haber reclutado pero huiese excluido igualmente
e) No participaron ni podrían participar



## Como determinar el tamaño de la muestra}

**Potencia:** probabilidad de rechazar H0 solo si H1 es verdadera
**P - value:** nos demuestra la relación entre H0 y H1

### D de Cohen:
Fórmula:
$$d = \frac{\mu_1 - \mu_2}{\sigma}$$

d = distancia entre las medias de las poblaciones

![[Captura de pantalla 2026-05-21 151116.png]]

Depende de:
- Tamaño de la muestra
- Tamaño del efecto
- Los procedimientos de medición
- Los procedimientos de análisis
- El tipo de comparación (una cola o dos colas)
- El nivel de significancia (p-value)


### Determinar el tamaño muestral:
1) Decidir cual es la potencia estadística deseada
2) Decidir cual es el nivel de significancia
3) Estimar el tamaño del efecto
	- statsmodels (python library)
	- GPower


### Plan de análisis
Especificar:
- Qué modelo voy a usar
- Cual va a ser la variable dependiente
- Cual va a ser la variable independiente (tratmiento)
- Cuales van a ser los covariados
- Como voy a verificar que se cumplan las hipótesis del modelo
- Qué parte de los resultados del modelo voy a mirar


### Tener en consideración
- Transformaciones de variables
- Criterio de inferencia
- Inclusión y exclusión de datos
- Data invalida


### Malas prácticas
- Harking (hipotesis posterior a los resultados)
- P-hacking (modificar el p-value)



## Tarea

OSF: Pre - registro

Incluyendo:
- Hipótesis
- Análisis primario
- Test de hipótesis





