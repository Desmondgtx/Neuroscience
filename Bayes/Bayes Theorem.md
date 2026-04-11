
**Concepts:**
P = Probability
H = Hypothesis
E = Evidence 
| = Given
¬ = Not

**Formula:**
$$P(H|E) = \frac {P(H)P(E|H)}{P(H)P(E|H)+P(¬H)P(E|¬H)}$$

**Explanation:**
$P(H)P(E|H)$ = Probability of true Hypothesis GIVEN Evidence
$P(H)P(E|H)+P(¬H)P(E|¬H)$ = Probability of true Hypothesis Given Evidence + Probability of Hypothesis not true

**Resulting Formula:**
$$P(H|E) = \frac {P(H)P(E|H)}{P(E)}$$

**Application:**

| **Description** | Person X is quiet and structure      |
| --------------- | ------------------------------------ |
| **Evidence**    | Ratio of Librarians/farmers are 1:20 |
| **Question**    | Person X is librarian or a farmer?   |
| **Probability** | Librarian Given Description          |
1) 40% of librarians match the description
2) 10% of farmers match the description
3) 1:20 -> 10:200 -> 40%:10% -> 4:20 
4) Replace data on the formula
$$P(H|E) = \frac {4}{4+20}$$
**Resultado Final**
$$P(H|E)= 0.16666666666$$
