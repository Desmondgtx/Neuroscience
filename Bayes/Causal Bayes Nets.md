
### Causal Bayes Nets (CBNs)
Produce causal structures from data and variables, causal Bayes nets can derive predictions. This CBNs are used as rational and computational modeling for causal reasoning as the normative or formal models.

**Markov Chains:** States that nodes or variables are independent of other variables that are not directly connected

### Causal Bayes Nets Graphs:
1) Common Cause: B <- A -> C => $P(A, B, C) = P(C|A)*P(B|A)*P(A)$
2) Causal Chain: A -> B -> C => $P(A, B, C) = P(C|B)*P(B|A)*P(A)$
3) Common Effect: A -> C <- B => $P(A, B, C) = P(C|A,B)*P(A)*P(B)$

### Properties:
Nodes represent variables
Arrows represent causal relations
Directed graphs means the relations are unidirectional (vs bidirectional relations)
Acyclic graphs means there are no loops in the graph (vs cyclical graphs)
Causal relations (arrows) have some probabilistic value

### Parameters of computational model in causal reasoning:
Cause     ->     Effect
   A         M        B       (Parameters)