
## Functions:
- Expressiones that defines relationship between two or more variables
- Takes *input* (domain or independent variables) and gives an *output (range or dependent variable)*
	- Domain: The domain of a function is the set of all possible input values
	- Range: The range of a function is the set of all possible output values

- A function is a mapping and must be 1:1 (like a Python dictionary: for each key we have a value)

- Example:

![[Captura de pantalla 2026-04-08 172601.png]]

- "Diagrama Sagital"
	- Just R1, R3 and R6 are valid functions
![[Captura de pantalla 2026-04-08 172219.png]]


## Summations:
- Example:
	- Serie:
		- $\sum_{i=1}^5 2i$ = 2x1+2x2+2x3+2x4+2x5 => 2+4+6+8+10 => 30
	- Python Code:
```Python
summation = sum(2*i for i in range(1,6))
print(summation) #30
```
-  General Formula
	- $S_n = \frac{n(2a+(n.1)d)}{2}$
	- Where
		- d = Change
		- n = Number of elements
		- a = First element


## Exponents

$x^2 * x^3 = x^{2+3} = x^5$
$x^2/x^3 = x^{2-3} = x^{-1} = 1/x$

$x^{1/2} = \sqrt{x}$
$x^{1/3} = \sqrt[3]{x}$

$(x^2)^2 = x^{2*2} = x^4$
$(x^5)^3 = x^{5*3} = x^{15}$

- Example
	- $8^{2/3} = (8^{1/3})^2 = 2^2 = 4$


## Logarithms
$2^x = 8 => log_2 8 = x$


## Properties

![[Captura de pantalla 2026-04-08 173944.png]]


## Euler's number
$E = 1+(1/n)^n$


## Limits
- What value keeps approaching if the *input variable* increase or decrease
- *It does NOT matter what happens on the exact point, but what happen CLOSE to the point*

- Example
	- $\lim_{x \to \infty} 1/x = 0$
	- ![[Captura de pantalla 2026-04-08 174346.png]]
	- Python Code

```Python
from sympy import * 

x = symbols('x') 
f = 1 / x 
result = limit(f, x, oo) 

print(result) # 0
```

- Limits allows us: 
	- Define derivatives
	- Derive differentiation rules

Understanding > Memorization

- Euler's Number
	- $\lim_{x \to \infty} (1 + \frac{1}{n})^n = e = 2.71828169413...$
	- Python Code:

```Python
from sympy import * 

n = symbols('n') 
f = (1 + (1/n))**n 
result = limit(f, n, oo) 

print(result) # E 
print(result.evalf()) # 2.71828182845905
```

### Valid and Invalid Limit
- The limit is the value that is *being approach* not the actual value

Example
- *Valid Function*

![[Captura de pantalla 2026-04-10 104500.png|554]]
- $f(-1) = 0$

- *Invalid function*

![[Captura de pantalla 2026-04-10 104509.png|554]]
- limit DNE (does not exist)
- $\lim_{x \to a^-} fx = L_1 \neq \lim_{x \to a^+} fx = L_2$


## Derivatives

- A derivative tells the slope of a function
- Useul to measure the rate of change in a function

- When the slope is 0 we are at the min o the max of a funcion
	- Useful in linear or logistic regressions and neural networks

- Example
