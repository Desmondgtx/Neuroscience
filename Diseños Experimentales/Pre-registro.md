
## Clase 1 de Diseños Experimentales

### Objetivos:
1) Elegir preguntas que peudan ser respondidas mediante experimentos
2) Evaluar qué diseños experimentales osn adecuados para responder una pregunta determinada
3) Decidir qué tipo de diseños experimentales van con qué tipo de análisis estadístico
4) Implementar salvaguardas para garantizar la replicabilidad de los resultados obtenidos a partir de experimentos
5) Aprender sobre el uso de pre-registros (plataforma OSF) e implementar integralmente el pre-registro de un estudio


![[Captura de pantalla 2026-04-08 093534.png]]


#### ¿Por qué investigar una cosa y no otra?
- Interesante para uno mismo
- Interesante para otros
- Novedoso
- Impacto
- Consistente con los recursos
- Riesgo/Beneficio 
- Ético


Que sea interesante para uno NO significa que sea interesante para otros
Novedoso NO significa que sea interesante o que tenga impacto
Se pueden sobreestimar los recursos disponibles
Es imposible decidir sobre las implicaciones éticas de los propios experimentos

*Es necesario buscar feedback en una etapa temprana del diseño experimental*
- Hablar con colegas para ver si el problema es interesante
- Hablar con gente que esté trabajando en el tema para ver si es novedoso
- Hablar con autoridades del lugar de trabajo para entender los recursos disponibles
- Buscar la aprobación de un comité de ética en investigación científica



### Pre-registro
- Los revisores no pueden cuestionar tanto los resultados
- Si el diseño está bien elegido y pre-registrado, no lo pueden cuestionar
- Si los análisis están bien elegidos y pre-registrados, no los pueden cuestionar



### Tipos de estudio

#### Experimento Randomizado:
- Between Subject Desing
- Debe incluir asignación aleatoria de los sujetos en distintas condiciones. Usualmente incluye experimentos de laboratorio, de campos, intervenciones, trials aleatorizados, A/B testing
	- A/B testing: condiciones experimentales para evaluar métricas e hipótesis, concepto desde marketing
- Como asignar sujetos:
	- Idealmente los dos grupos deben ser lo más parecidos posibles, *excepto* en relación a la variable que estamos estudiando
	- Queremos controlar variables como la edad, sexo, educación, entre otras, sea lo más parecida posible entre los grupos
- Análisis - Two Sample T-Test

#### Experimento longitudinal
- Within Subject Desing
- Se miden las condiciones experimentales o intervenciones en EL MISMO GRUPO pero en instancias de tiempo distintos
- Problemas asociados:
	- Carry-over: una intervención puede afectar a las siguientes
	- La familiaridad de los sujetos con el experimento importa: los sujetos aprenden, se habituan, se aburren y se cansan
	- Los sujetos deben involucrarse más con el experimento
	- Los riesgos que pueden aparecer cuando los tratamientos se acumulan
	- Cuidar los intervalos de tiempo para que no varia tanto la muestra
- Como resolverlos:
	- Aleatorizar o balancear el orden de las condiciones o tratamientos
		- Orden de condiciones diferentes
		- El objetivo es que, para cada sujeto, el orden de las condiciones sea diferente
- Análisis - Paired T-Test

#### Diseño mixto
- Diseño ENTRE SUJETOS e INTRA SUJETO
- 2 poblaciones y 2 intervenciones
- Análisis - ANOVA

#### Resumen
![[Captura de pantalla 2026-04-08 114443.png]]


#### Diseño Experimental

#### Diseño Quasi-Experimental
- Hay comparación entre gurpos, pero no es posible o ético asignar los grupos de forma aleatoria
	- Comparación entre hogares de ingreso alto vs bajo
	- Comparación entre niños que sufrieron o no maltrato infantil
- Experimentos naturales
- Mediador
	- Si lo quitas deja de ocurrir el fenómeno
- Moderador
	- Cambia su relación causal
- Confounds: variables confundidoras


### Buen experimento
*Validez Interna*
- La habilidad de un estudio y/o experimento para demostrar una relación causa-efecto
- Es alta en estudios con buena asignación aleatoria entre grupos y controles
- Es alta cuando elimino otras psoibles causales de diferencia entre grupos en el diseño
- Los controles pueden ser tantos que el estudio no refleja situaciones de vida real

*Validez Externa*
- La habilidad de mi estudio y/o experimento para generalizarse a otras poblaciones (**replicabilidad**)
- En estos estudios con validez interna alta, la validez externa puede ser baja por *no ser representativos de situaciones naturales*


Clase 2: [[Muestra]]