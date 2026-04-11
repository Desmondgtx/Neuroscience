# Causal Bayes Nets as psychological theories of causal reasoning - Evidence from psychological research
@hagmayerCausalBayesNets2016 [[Papers]]

 [[Causal Bayes Nets]] have been used in psychological theories in two ways:
 1) Computational models of causal reasoning: This models can be used to describe what an optimal learner would infer. Thus, they provide a normative standard to compare the actual performance of the participants
 2) Formal models of mental causal models: This models allow us to represent causal structure, make predictions, plan interventions and induce causal structures.

### Causal Bayes Nets Graphs:
1) Common Cause: B <- A -> C = $P(A, B, C) = P(C|A)*P(B|A)*P(A)$
2) Causal Chain: A -> B -> C = $P(A, B, C) = P(C|B)*P(B|A)*P(A)$
3) Common Effect: A -> C <- B = $P(A, B, C) = P(C|A,B)*P(A)*P(B)$

### Properties:
Nodes represent variables
Arrows represent causal relations
Directed graphs means the relations are unidirectional (vs bidirectional relations)
Acyclic graphs means there are no loops in the graph (vs cyclical graphs)
Causal relations (arrows) have some probabilistic value

### [[Markov Violations]]
### Empirical Data:
Empircal data demostrate that people often violates this principales of causal relations
Participants were rarely able to reproduce the causal structures (Markov Violations)
People assumed positive correlation between an observed and an unobserved cause

### Screening-off:
Occurs on common cause (B <- A -> C) and causal chain (A -> B -> C) structures
The Causal Markov Condition (CMC) entails that variables ONLY depends on the value of the direct variables
Data showed that people correlates both effect variable when the common cause is unknown
People tend to "scree-off" the cause when the value is uknown
On causal chains participats tends to consider the value of all the values behind a node when only its direct father is important.

### Explaining-away:
Occurs on common effect structures (A -> C <- B)
Independent causes becomes negatively dependent 
If effect C is present, learning that cause A is present makes cause B less likely


**Important:**
"It is important to note tat these violations were found with different inference tasks, different material, and even with blank variables. Therefore these violations cannot be easily explained as biases due to the materials being used in the experiments or as the result of participants using previous, more elaborate causal knowledge in addition to the given information"

### Explanations of findings:
1) New Structures:
	1) Intermediate joint mechanism: New node on common cause structure
	2) Additional common cause: New node influence every variable on common cause 
	3) Additional common preventor: New node affects both effects on common cause
	4) Hidden common cause: New node influence both causes on common effect
	5) Different Integrationn rule for effects:
2) Explanations:
	1)  Glymour (2001) & Rehder (2005): Markov violations are not normative deviations, but rather it reflects of different mental models
	2) Park & Sloman (2014): Mental models change if the evidence contradicts the initial causal model
		- A probabilistic relations contradicts a causal model even when its right
		- We update our mental models dynamicly
		- Our mental models are flexibles that its adapts to new evidence and experiences
	3) Rehder (2014): Simulates modeling the empirir reasoning. Propose asociatives strategies, biases or mental shortcuts or SAMPLES.

