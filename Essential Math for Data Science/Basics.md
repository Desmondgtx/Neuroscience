
## Functions:
Expressiones that defines relationship between two or more variables
Takes *input* (domain or independent variables) and gives an *output (range or dependent variable)*
- Domain: The domain of a function is the set of all possible input values
- Range: The range of a function is the set of all possible output values

A function is a mapping and must be 1:1 (like a Python dictionary: for each key we have a value)

- Example:
![[Captura de pantalla 2026-04-08 172601.png|545]]

"Diagrama Sagital"
- Just R1, R3 and R6 are valid functions
![[Captura de pantalla 2026-04-08 172219.png|546]]


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
Examples:
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
![[Captura de pantalla 2026-04-08 173944.png|476]]


## Euler's number
$E = 1+(1/n)^n$


## Limits
What value keeps approaching if the *input variable* increase or decrease
*It does NOT matter what happens on the exact point, but what happen CLOSE to the point*

- Example
	- $\lim_{x \to \infty} 1/x = 0$
	- ![[Captura de pantalla 2026-04-08 174346.png|311]]
	- Python Code
```Python
from sympy import * 

x = symbols('x') 
f = 1 / x 
result = limit(f, x, oo) 

print(result) # 0
```

Limits allows us: 
- Define derivatives
- Derive differentiation rules

Understanding > Memorization

Euler's Number
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
The limit is the value that is *being approach* not the actual value

Example
- *Valid Function*

![[Captura de pantalla 2026-04-10 104500.png|363]]
- $f(-1) = 0$

- *Invalid function*
![[Captura de pantalla 2026-04-10 104509.png|358]]
- limit DNE (does not exist)
- $\lim_{x \to a^-} fx = L_1 \neq \lim_{x \to a^+} fx = L_2$


## Derivatives
A derivative tells the slope of a function
Useul to measure the rate of change in a function

When the slope is 0 we are at the min o the max of a funcion
- Useful in linear or logistic regressions and neural networks

- Example
![[Captura de pantalla 2026-04-11 213301.png|446]]
- You can calculate the slope $m$ between two points using the formula
	- $m = \frac{y_2-y_1}{x_2-x_1}$
	- $m = \frac{4.41-4.0}{2.1-2.0}$
	- $m = 4.1$
- You can make the two points even closer like $x = 2.00001$
	- $f(2.00001) = 4.00004$

A derivative calculator in Python
```Python
def derivative_x(f, x, step_size):
    m = (f(x + step_size)- f(x))/((x + step_size) - x)
    return m
    
def my_function(x):
    return x**2

slope_at_2 = derivative_x(my_function, 2, .00001)
print(slope_at_2) # 4.000010000000827
```

When you encounter an exponential function like $f(x) = x^2$ the derivative function will make the exponen a multiplier and then decrement the exponent by 1, living us with the derivative $\frac{d}{dx} x^2 = 2x$. 
Slope at x = 2:
- $f(x) = x^2$
- $\frac{d}{dx}f(x) = \frac{x}{dx}x^2 = 2x$
- $\frac{d}{dx}f(2) = 2(2) = 4$

- Python example:
```Python
# Calculating a derivative in Sympy
x = symbols('x')

def f(x):
    return x**2

def dx_f(x):
    return 2*x

slope_at_2 = dx_f(2.0)
print(slope_at_2) # 4.0

# EXTRA PLOT
f = x**2
plot(f)

```


## Partial Derivatives
Rather than finding the slope on a one-dimensional function, we have slopes with respect to multiple variables in several directions.
For each given variable derivative, we assume he other variables re held constant

Let's take the function $f(x,y) = 2x^3+3y^3$. The $x$ and $y$ variable each get their own derivatives $\frac{d}{dx}$ and $\frac{d}{dy}$. These represent the slope values with respecto to each variable on a multidimensional survace.
We call these "slopes" *gradients*

To calculate this:
- $f(x,y) = 2x^3 + 3y^3$
- $\frac{d}{dx} 2x^3 +3y^3 = 6x^2$
- $\frac{d}{dy} 2x^3 + 3y^3 = 9y^2$

Python Example:
```Python
# Calculating partial derivatives

x,y = symbols('x y')

f = 2*x**3 + 2*y**3
dx_f = diff(f,x)
dy_f = diff(f,y)

print(dx_f) # 6*x**2
print(dy_f) # 9*y**2

# Plot
plot3d(f)
```
![[Captura de pantalla 2026-04-11 221004.png|500]]

### Limits on derivatives
 Limit to see what that slope approaches to a function
$f(x) = x^2$
$lim_{x \to 0} \frac{(x+s)^2-x^2}{(x+s)-x}$

slope where $x = 2$
$\lim_{x \to 0} \frac{(2+s)^2-2^2}{(2+s)-2} = 4$

Python code:
```Python
# Using limits to calculate a slope
x, s = symbols('x s')

f = x**2
slope_f = (f.subs(x,x+s)-f)/((x+s)-x)
slope_2 = slope_f.subs(x,2)
result = limit(slope_2,s,0)

print(result) # 4

# Without assign value to step size S
x, s = symbols('x s')

f = x**2
slope_f = (f.subs(x,x+s)-f)/((x+s)-x)
result = limit(slope_f,s,0)

print(result) # 2*x
```


## The Chain Rule
Suppose that we are given two functions:
$y = x^2 +1$
$z = y^3-2$

This two functions are linked, because the Y is the output variable in the first function bur is the input variable in the second functions, so we can substitute the second function like
$z = (x^2 + 1)^3 -2$

So, what is the derivative for $z$ with respecto to $x$?
```Python
# Finding the derivative of z with respect to x
x = symbols('x')

z = (x**2+1)**3 -2
dz_dx = diff(z,x)

print(dz_dx) # 6*x*(x**2 + 1)**2
```
The derivative for z with respecto to x is $6x(x^2+1)^2$
- $\frac{dz}{dx}((x^2+1)^3-2)$
- $= 6x(x+1)^2$

*Different Approach:*
Multiply the dervatives of $y$ and $z$ functions separately
$\frac{dy}{dx}(x^2+1)=2x$
$\frac{dz}{dy}(y^3-2) = 3y^2$
$\frac{dz}{dx} = (2x)(3y^2) = 6xy^2$

Replacing $y = x^2 +1$
$\frac{dz}{dx} = 6xy^2 = 6x(x^2+1)^2$

*The chain rule* dictates that for a concatenate functions we can find the derivate of the second function to the first input variable by multiplying the two derivatives together:
$$\frac{dz}{dx} = \frac{dz}{dy} * \frac{dy}{dz}$$
The chain rule is a key part of training a neural network with the proper wights and biases.


## Integrals
The opposite of a derivatve is an *integral*, wich finds the are under the curve (AUC) for a given range

Riemann Sums:
$f(x) = x^2+1$
Find the AUC between 0 and 1
![[Captura de pantalla 2026-04-12 141533.png|461]]

We can divide the are into rectangles, wich give us a good approximation of the AUC
(The are of a rectangle is $A = length * width$)
![[Captura de pantalla 2026-04-12 141541.png|461]]

Python Code:
```Python
# Integral approximation in Python
def approximate_integral(a, b, n, f):
    delta_x = (b-a)/n
    total_sum = 0
    
    for i in range(1, n+1):
        midpoint = 0.5*(2 * a + delta_x * (2*i-1))
        total_sum += f(midpoint)
        
    return total_sum * delta_x

def my_function(x):
    return x**2+1

area = approximate_integral(a=0, b=1, n=5, f=my_function) # 5 rectangles (n)
area_2 = approximate_integral(a=0, b=1, n=1000, f=my_function) # 1000 rectangles

print(area) # 1.33
print(area_2) # 1.333333250000001
```
As we increase the number of rectangles, the approximation starts to reach its limit at smaller decimals

Direct Approach
```Python
x = symbols('x')

f = x**2 + 1
area = integrate(f, (x, 0, 1))

print(area) # 4/3
```

### Calculating Integrals with Limits
Python Code:
```Python
x, i, n = symbols('x i n')

f = x**2 + 1
lower, upper = 0, 1

delta_x = ((upper - lower) / n)
x_i = (lower + delta_x * i)
fx_i = f.subs(x, x_i)

# Iterate all "n rectangles and sum areas
n_rectangles = Sum(delta_x * fx_i, (i, 1, n)).doit() 
area = limit(n_rectangles, n, oo) # n towards infinity

print(area) # 4/3
```