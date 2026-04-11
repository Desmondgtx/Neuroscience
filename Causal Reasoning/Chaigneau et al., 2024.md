# Breaking the chains of independence - A Bayersian uncertainty model of normative violations in human causal probabilistic reasoning
@chaigneauBreakingChainsIndependence [[Papers]]

### Bayesian Uncertainty Model (BUM):
- Causal reasoning reflects an adaptative response to ambiguity, accounting normative violations
- Need for empircal testing

### Normative models
- Normative Models: [[Causal Bayes Nets]] as we seen on [[Hagmayer, 2016]]
- Provides a framework for how people SHOULD reason about cause-effects relationships
- Based on principles of probability and logical consistency
- Human reasoning and empirical data deviates from these normative models

### Causal Bayes Nets Graphs:
1) Common Cause: B <- A -> C => $P(A, B, C) = P(C|A)*P(B|A)*P(A)$
2) Causal Chain: A -> B -> C => $P(A, B, C) = P(C|B)*P(B|A)*P(A)$
3) Common Effect: A -> C <- B => $P(A, B, C) = P(C|A,B)*P(A)*P(B)$

### [[Markov Violations]] 
#### 1) Markov violations with generative causes:

For a causal chain structure, to infer state of X2 only Y should be relevant
Structure: X1 -> Y -> X2
Model: X1 does not influence X2
Reality: X1 state influence X2
**Formula:**
- Model: $$P(X1|Y, X2) = P(X1|Y)$$
- Reality:
$$
\begin{align*}  
P(X1|Y, X2) ≠ P(X2|Y) \\
X1 = 1 → P(X2|Y, X1)>P(X2|Y) \\ 
X1 = 0 → P(X2|Y, X1)<P(X2|Y)
\end{align*}  
$$

#### 2) Markov violations with independent causes:

For a causal common effect structure, people infer that the causes are correlated
Structure: X1 -> Y <- X2
Model: X1 and X2 are independent
Reality: X1 and X2 are correlated
**Formula:**
- Model: $$P(X1,X2) = P(X1)P(X2)$$
- Reality: 
$$
\begin{align*}  
P(X1,X2) ≠ P(X1) \\
X1 = 1 → P(X2|X1)>P(X2) \\ 
X1 = 0 → P(X2|X1)<P(X2)
\end{align*}  
$$
#### 3) Weak Explaining Away Effect:

For a common effect structure, given that X1 is present SHOULD decrease the value that X2 is responsible for Y
Structure: X1 -> Y <- X2
Model: Presence of X1 reduces the effect of X2
Reality: Presence of X1 do not reduces X2
**Formula:**
- Model: $$P(X2=1|Y=1) >> P(X2=1|Y=1,X1=1)$$
- Reality: $$P(X2=1|Y=1) ≥ P(X2=1|Y=1,X1=1)$$
#### 4) Negative Markov violations in mixed generative and inhibitory links:

For a common effect structure, the relations between effects are conditionally independent, people often infer a negative correlation between effects
Structure: X1 -> Y <- X2
Model: X1 and X2 are conditionally independent
Reality: X1 and X2 are negative correlated
**Formula:**
- Model: $$P(X1|Y,X2) = P(X1|Y=1)$$
- Reality: 
$$
\begin{align*}  
P(X1|Y,X2) ≥ P(X1|Y) \\
X2 = 1 → P(X1|Y,X2)=P(X1|Y) \\ 
X2 = 0 → P(X1|Y,X1)>P(X1|Y)
\end{align*}  
$$

#### 5) Conservatism:

Given new evidence about hypothesis H, people tend to NOT update their beliefs as much as they should
Model: Update beliefs with new evidence
Reality: People do not update their plans or beliefs
**Formula:**
- Model: $$P(H|e)∝ P(e|H)P(H)$$
- Reality: 
$$P(H|e) ≈ P(H)$$

### Current models and their basic mechanisms:
All of these models offer mechaniss to account for normative causal reasoning violations
1) Beta-Q Model: Explains systematic violations of the Markov condition in human causal reasoning by introducing a bias toward prototypical states (0-0-0 or 1-1-1)
2) Mutation Sampler: Computes causal inferences by sampling over the state space of a causal system by uing Markov chain Monte Carlo Methods. COgnitive resources are limited, so systematic biases can be introduced
3) Bayesian Mutation Sampler: Extends the Mutation Sampler by integrating generic prior distributios into the sampling framework (prior knowledge on Bayes theorem) 
4) Bayesian Sampling Model: This apporach reconciles normative Bayesian principles with observed human probability errors, emphasizing how cognitive resource limitations shape probabilistic reasoning

## Bayesian Uncertainty Model (BUM)
**Assumptions:**
- When people receive truth H, they consider also a model H' reflecting their uncertainty
- Bayesian Model Averaging (BMA) integrates predictions from multiple model per hypothesis
- BUM model implies very precise marginalization that BMA destroys with mixture
- H' may retain the same relations as H but with different probability and links values
**Account for Markov violations:**
1) **Markov violations with generative causes:** a>c and b>d are generative, causing that X1 and X2 remain correlated, as the empirical data points to
2) **Markov violations with independent causes:** The BMA model assigns partial weights to X1 and X2 generating som correlations between them
3) **Weak explaining away:** The mixture introduces covariance between X1 and X2 so one cause no longer discounts the other
4) **Negative Marko violation in mixed links:** (Ask Nicolas and Sergio)
5) **Conservatism:** BMA reduces the overall adjustment causes by the new evidence

### Conclusions 
- Any model that has a mechanism to "disturb" the normative probability distribution, will be able to account many of the normative violations
- "Uncertainty" introduces the disturbance needed to invalidate assumptions of variable independence
- DIfferent model have different applications
- BUM offers unified frameworks for understanding systematic deviations in human probabilistic and causal reasoning
- Individuals weigh different possible models of reality
- Adaptative responses to uncertainty

