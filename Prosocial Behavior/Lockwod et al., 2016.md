# Neurocomputational mehcanisms of prosocial learning and links to empathy
[[Papers]]

### Definitions of concepts:

[[Concepts Prosocial Behavior]]

### Quotes:

"Empathy is hypothesized to be a critical facilitator of prosocial behavior, but the link between empathy and prosocial behavior is still unclear.
Using computational modeling, this study shows that people can learn to obtain to obtain rewards for others but do so more slowly than learning to obtain rewards forthemselves.
There is a computational mechanism driving prosocial learning in humans"

### Data Collection:

![[Captura de pantalla 2025-07-20 162758.png]]

A) Reinforcement learning task: Participants had to learn the probability that abstract symbols were rewarded. At the beginning of each block, they were told to whom they were playing for.
B) Group-level learning curves: Shows choice behavior in the three learning conditions
C) Comparison of [[Learning Rate]] (α): Participants had a significantly higher learning rate when they playing for themselves
D) Individual differences in empathy: Modulate the prosocial vs self learning rate difference
E) Temperature of softmax (β): Participants were less consistent when choosing for no one compared to other conditions

"These findings suggest that people have a self-bias in their learning, learning more quickly about rewards for themselves compared with for another person or no one. However, people are similarly variable when choosing for themselves and others and most variable when no beneficiary will receive the reward"

## Computational Modeling of Behavioral Data

Learning behavior in the self, prosocial and no one conditions was modeled using a reinforcement learning (RL) algorithm

### Q-Learning Update

**Formula:** 
$$Q_{t+1}(a) = Q_t(a)+ α *[r_t - Q_t(a)]$$
**Where:**
t = Each trial
a = Action or decision
α = Learning Rate, values between 0 (no learning occurs, we ignore new information) and 1 (we completely replace old beliefs with new information)
$r_t$ = Reward recieves. Result of a given action
$Q_t(a)$ = Current expectation (associative value that is updated trial by trial)
$[r_t - Q_t(a)]$ = Prediction Error (PE). Difference between what actually happened ($r_t$) and ours expectations

**Explanation:**
Future reward expectation $Q_{t+1}(a)$ should be a function of curent expectation $Q_t(a)$ and the discrepancy between the actual reward that has just been experienced on this trial $r_t$ (binary value of 1 or 0, reward or no reward) and the expected reward for this trial $Q_t(a)$. 
The degree to which this discrepancy updates the expectation is sacled by the learning rate α (value between 0 and 1)

**Example of Calculation:**

**Values:**
$Q_t(a)$ = 0.8 (high expectation)
α = 0.25 (medium learning rate)
$r_t$ = 0 (no reward recieved)

**Calculation:**
Prediction error: 
$[r_t - Q_t(a)]$ = 0 - 0.8 = -0.8
Scale update: 
$α *[r_t - Q_t(a)]$ = 0.25 * (-0.8) = -0.2
Updated Q-value: 
$Q_{t+1}(a)$ = 0.8 + (-0.2) = 0.6

**Result:**
The Q-value decreased from 0.8 to 0.6 because the participant recieved no reward

**Script: (RStudio)**
[[Q-Learning Update Script]]


### Softmax link function:
**Formula:** 
$$P_t[a|Q_t(a)] = \frac{e^{[Q_t(a)/β]}}{Σ_a e^{[Q_t(a')/β]}}$$
Beta (β) is the parameter that controls the balance between:
**Exploitation:** Consistently choosing the best option (Low β)
**Exploration:** Sometimes making random choices to gather more information (High β)

**Values:**
$Q_t(a)$ = 0.8 (For choosing A)
$Q_t(a')$ = 0.8 (For choosing B)
β = 0.5 (Moderate parameter/temperature)

**Calculation:**
**Step 1:**
$Q_t(a)/β$ = 0.8/0.5 = 1.6
$e^{[Q_t(a)/β]}$  = e^1.6 = 4.953

**Step 2:**
$Q_t(a')/β$ = 0.3/0.5 = 0.6
$e^{[Q_t(a')/β]}$  = e^0.6 = 1.822

**Step 3:**
Σ = e^1.6 + e^0.6 = 4.953 + 1.822 = 6.775

**Step 4:**
P(choosing A) = 4.953/6.775 = 0.731 (73.1%)
P(choosing A') = 1.822/6.775 = 0.269 (26.9%)

**Explanation:**
Even though we've learned that A is better option, we still have 26.9% chance of choosing A' (non A option or B option).
This exploration helps us continue learning in case reward probabilities change.

**Understanding Softmax Function:**
This function solves a key problem in modeling behavior. Real humans and animals don't always choose the objectively best option. Sometimes we explore, make mistakes or even act inconsistently. Softmax function captures this probabilistic choice behavior of choices

**Script: (RStudio)**
[[Softmax Function Script]]

$$P(a)_{j(i)}= \frac {exp^\frac{V_{j(i)}}{β_j}} {∑_i exp^\frac{V_{j(i)}}{β_j}}$$

$$P(V)=\frac {exp(V*β)} {exp(1*β) + exp(β*V)}$$