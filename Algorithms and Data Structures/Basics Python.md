
### Basics
 - Sequence: Performing operations one at a time in a specified order
 - Selection: Using conditional statements such as IF to select which operations to execute
 - Iteration: Repeating some operations using loops or recursion
In any programming language, there are usually several mechanisms for selection and iteration, while sequencing is just the default behavior.

**Operations:**
x = x + 1 es equivalente a x += 1
Funciona igual con -=, *=, /=

### Variables Types

**Atomic types:**
- Integers = Integer numbers
- Floats = Decimal numbers
- Booleans = 1 - 0, T - F

An object have three things: Identity, Type and Value
To check variable type you can use type()

### Collections

**Sequential Collections:** Lists, Tuples and Strings
**Nonsequential Collections:** Dictionaries and Sets
#### String
Collection of  letters or characters, you can concatenate strings to create larger strings.
``` Python
s = 'Hello, '
t = 'World!'
u = s + t
print(u) # Hello, World!
```

#### Lists
Collection of objects of different types. Lists are indicated by  square brackets "[]".
``` Python
# Create a List
L = [1, 2, 3, 4, 5, 6]

# Append an item to the end of the list
L.append(100) 

# Access item by their index
print('The X item of the list is: ', L[x]) 

# Overwrite values in a list
L[2] = 'skip'
L[-2] = 99
print(L) # L = [1, "skip", 3, 4, 5, 99, 100]
```

#### Tuples
Ordered sequences of INMUTABLE objects, you CAN NOT change items after you create a tuple. It uses parenthesis "()"
``` Python
# Create a tuple
T = (1, 2, 'skip a few', 99, 100)
```

#### Dictionaries
Every element has two parts, a KEY and a VALUE (key-value pairs), uses curly braces "{}"
Dictionaries are also known as "maps", "mapping" or even "hash tables"
``` Python
# Create a Dictionary
d = dict()
d[5] = 'five'
d[2] = 'two'
d['pi'] = 3.141592

# Print list
print(d)
{5: 'five', 2: 'two', 'pi': 3.141592}

# Print an element
print(d['pi'])
3.141592
```

#### Sets
Correspond to our notion of sets in math. Collections WTH NO duplicates. Uses curly braces "{}"
If you want an empty set, you would write "set()"
``` Python
# Create a Set
s = {2,1}

# Add new values
s.add(3)
s.add(2) # It wont generate a second value "2"

# Print Set
print(s)
{1, 2, 3}
``` 

#### Common things to do on collections

- Length of collections: len(a)
- Slicing (only on Sequential Collections): a[x:y]
- Iterating over a collection:
``` Python 
# Creating Collections
mystring = 'abracadabra'
mylist = [1, 3, 5]
mytuple = (1, 2, 'skip', 99, 100)
mydict = {'a': 96, 'b': 97, 'c': 98}
myset = {'a', 'b', 'c'}

# Iterating with a For Loop
for character in mystring: # Strings
	print(character)

for item in mylist: # List
	print(item)

for item in mytuple: # Tuples
	print(item)

for key in mydict: # Dictionaries
	print(key)

for key, value in mydict.items(): # Dictionaries
	print(key, value)

for value in mydict.values(): # Dictionaries
	print(values)

for element in myset: # Sets
	print(element)

# Iterating over a range (to represent a sequence of numbers or values):
for i in range(10):
	j = 10 * i + 1
	print(j, end=' ')
```

### Control Flow

Basics forms of control flow are if statements, while loops, try blocks and function calls.

``` Python
# If Statement: "if" statements evaluates an experssion as a bollean. If the predicate is True, then a block of code is executed, this is the SELECTION part

# Else Statement: An "if" statement can include an "else" clause, this allows a second block of code executes if the predicates is False
if False:
	print("This is bad.")
else:
	print("This will print.")
# This will print.


# While Loop: Also has predicate, will evaluate the predicate, if it is True, then a block of code will execute and repeat. The repetition continues until the predicate evaluate to False or until the code reaches a "break" statement.
x = 1
while x < 128:
	print(x, end=' ')
	x *= 2
# 1 2 4 8 16 32 64


# Try Block: Is the wayto catch and recover from errors while a program is running. You can catch an error unsing "exception" and handle it.

x = "string"
try:
	f = float(x)
except ValueError:
	print("You can not do that!")
# You can not do that!


# Function: You can define a dunction with "def" keyword. The "parameters" for the function are listed in parenthesis. 
# The "return" statement causes the control flow to revert back to where the function was called and determines the value of the function
def foo(x, y):
	return 8 * x + y
print(foo(2, 1)) # 17
print(foo("Na", "batman")) #NaNaNaNaNaNaNaNa batman

```

### Modules and Imports

A single .py file is called a "module". You can import one module into another script using the "import" keyword.

``` Python
# File: twofunctions.py
def f(x):
	return 2 * x + 3

def g(x):
	return x ** 2 - 1

# File: theimporter.py
import twofunctions

def f(x):
	return x - 1

print(twofunctions.f(1)) # 5
print(f(1)) # 0
print(twofunctions.g(4)) # 15


# You can import just a particular name or collection of names from a module
from modulename import thethingyouwant

# You can import all he names from the module into the current namespace
from modulename import *

# You can rename a module after importing it
import numpy as np
np.array == numpy.array

```


Chapter 3: [[OOP]]