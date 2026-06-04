
# Definitions
- Algorithms:
	- Steps of the algorithm needs to be in a specific order
	- Steps needs to be distinct
	- Algorithms should produce a result or output
	- Must be complete in a finite numbers of step and finite amount of time
- Big O: 
	- Theoretical definition of the complexity of an algorithm as a function of its size
- O(n):
	- A function of the size
- Data structure
	- A way to store data
	- It's the collection of calues and the format they are stored in
	- The relationship between the values in the collection as well as the operations applied on the data sotred in the structure


# Data Structures
[[Basics Python]]

## Built-in Types

### Lists
Ordered, mutable, allows duplicates

Example code:
```python
my_list = []            # Empty
my_list = [1, 2, 3]     # With values
my_list = list()        # Using constructor
```

### Tuple
Ordered, **immutable**, allows duplicates.

Example code:
```python
my_tuple = ()           # Empty
my_tuple = (1, 2, 3)    # With values
my_tuple = tuple()      # Using constructor
```

### Dictionary (Hash Map)
Key-value pairs. Keys must be unique and hashable. Ordered by insertion (Python 3.7+).

Example code:
```python
# Empty
my_dict = {}  

# With values
my_dict = {"nombre": "Diego", "apellido": "Garrido"}  

# Using constructor
my_dict = dict()

my_dict["nombre"]  # → "Diego"
```

### Set (Hash Set)
Unordered, mutable, **no duplicates**. Backed by a hash table

Example code:
```python
my_set = set()       # Empty ← must use set()
my_set = {1, 2, 3}   # with values (curly braces work only when non-empty)
```

> [!warning] Common confusion
> `{}`  → empty **dict**, NOT a set  
> `()`  → empty **tuple**, NOT a set  
> `set()` → empty **set** ✔



## Implemented Structures

> [!note]
> These are not built into Python. In DSA/LeetCode context, simpler types are used to replicate their behavior.

### Array
Python has no native fixed array. In LeetCode/NeetCode, **`list` is used as an array**.  
For typed arrays (rare in DSA), use the `array` module.

Example code:
```python
nums = [1, 2, 3, 4]   # standard in DSA practice

import array
typed = array.array('i', [1, 2, 3])  # 'i' = signed int
```

### Stack
LIFO — Last In, First Out. Implemented with `list`.

Example code:
```python
stack = []
stack.append(x)  # push  → O(1)
stack.pop()      # pop   → O(1)
stack[-1]        # peek  → O(1)
```

### Queue
FIFO — First In, First Out. Use `collections.deque` (not `list`, since `list.pop(0)` is O(n)).

Example code:
```python
from collections import deque
queue = deque()
queue.append(x)   # enqueue → O(1)
queue.popleft()   # dequeue → O(1)
```

### Linked List
[[Linked List]]
Example code:
```python
class Node:
    def __init__(self, val):
        self.val = val
        self.next = None  # pointer to next node

head = Node(1)
head.next = Node(2)
```

### Tree (Binary Tree)
Example code:
```python
class TreeNode:
    def __init__(self, val):
        self.val = val
        self.left = None
        self.right = None
```

### Graph
Typically represented as an **adjacency list** using a dict.

Example code:
```python
graph = {
    0: [1, 2],
    1: [0, 3],
    2: [0],
    3: [1]
}

# Or with defaultdict (no KeyError if node doesn't exist)
from collections import defaultdict
graph = defaultdict(list)
graph[0].append(1)
```



# Algorithms

## Nested Loops:
A pattern using two loops to iterate over all unique pairs in a sequence. The inner loop always starts one position ahead (`i+1`), avoiding self-pairs and duplicates. 
- **Use cases:** comparing pairs, brute-force search, combinatorics problems. 
- **Time complexity:** O(n²)

Example:
```Python
for i in range(len(nums)):
	# for j in range(len(nums)) #NO
	for j in range(i+1, len(nums))
```

	i=0 →  [i]  [j]  [ ]  [ ]
	i=0 →  [i]  [ ]  [j]  [ ]
	i=0 →  [i]  [ ]  [ ]  [j]
	i=1 →  [ ]  [i]  [j]  [ ]
	i=1 →  [ ]  [i]  [ ]  [j]
	i=2 →  [ ]  [ ]  [i]  [j]

Why "for j in range(len(nums))" does'nt work? 
- Avoids self-pairs: (i == j) → comparing element with itself 
- Avoids duplicate pairs: (0,1) and (1,0) would both appear


## Sliding Window
A technique using two pointers (`left`, `right`) that define a contiguous window
over a sequence. The window **expands** by advancing `right`, and **shrinks** by
advancing `left`. Both pointers only move forward
- **Time Complexity:** O(n).
- Key property: window size is adjustable (variable or fixed).
- Use cases
	- Longest/shortest subarray satisfying a condition (sum, unique elements, etc.)
	- Maximum or minimum within a fixed-size window
	- Substring problems (no repeating chars, anagram detection)

Example:
```python
left = 0
for right in range(len(nums)):
    while window_is_invalid:
        left += 1
```

	Expand →  [i]  [j]  [ ]  [ ]
	Expand →  [i]  [ ]  [j]  [ ]
	Shrink →  [ ]  [i]  [j]  [ ]
	Expand →  [ ]  [i]  [ ]  [j]
	Shrink →  [ ]  [ ]  [i]  [j]

Both pointers only move **rightward** — each element enters and exits the windowat most once. This is what makes it O(n) vs O(n²) for nested loops.



# Classes in Python


```python
# 1)
class Cookie: # Define class
	def __init__(self, color) # Initialize class
		self.color = color # Initialize attributes
	
	def get_color(self) # Method
		return self.color
		

# 2)	
cookie_one = Cookie('green')
# Cookie = class
# 'green' = method

# 3)
print(cookie_one.get_color())
# cookie_one = variable
# get_color = method
# () = Initialize method
```

1) Define classes, attributes and methods
2) Define variables and apply methods
3) Print variables and initialize methods



# Pointers

```python
num1 = 11
num2 = num1

id(num1) = 140727958956656
id(num2) = 140727958956656 # Points to the exact same variable
# Same memory address
# id = Addres in memory
```

## Dictionaries

``` python
dict1 = {'value': 11}
dict2 = dict1
# same memory address

dict2['value'] = 22
# Transorm BOTH variables dict1 & dict2

dict3={'value':33}

dict1 = dict3
dict2 = dict3
# Now dict1, dict2 and dict3 points to {'value':33}

# {'value': 11} & {'value': 22} goes to garbage collection
```



Next Chapter: [[Big O Notation]]



