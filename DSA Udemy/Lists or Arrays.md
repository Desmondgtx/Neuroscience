
[[General Concepts]]

An **array** is a linear data structure that stores elements in **contiguous memory locations**, allowing **random access by index** in O(1) time.

In Python, the closest built-in equivalent is the **`list`** type, which is technically a **dynamic array** (resizes automatically). In DSA/LeetCode context, `list` is what we use whenever a problem says "array".


## List vs Numpy

|Operación|`list` (DSA)|`numpy.array`|
|---|---|---|
|Append|`arr.append(x)` — O(1)|`np.append(arr, x)` — O(n), crea nuevo array|
|Insert|`arr.insert(i, x)`|`np.insert(arr, i, x)` — crea nuevo array|
|Pop|`arr.pop()`|No existe; usas slicing o `np.delete`|
|Remove|`arr.remove(x)`|No existe|
|Sort|`arr.sort()` in-place|`arr.sort()` o `np.sort(arr)`|
|Suma elemento a elemento|bucle / list comprehension|`arr1 + arr2` (vectorizado) ⚡|
|`arr * 2`|duplica el array `[1,2] * 2 = [1,2,1,2]`|multiplica cada elemento `[1,2]*2 = [2,4]`|
|Tipo de datos|Heterogéneo (puede mezclar tipos)|Homogéneo (todos del mismo tipo)|
|Tamaño|Dinámico (crece automático)|Fijo (redimensionar = crear nuevo)|


## Big O of Common Operations

| Operation        | Big O      | Notes                                                   |
| ---------------- | ---------- | ------------------------------------------------------- |
| Access by index  | O(1)       | Direct memory access                                    |
| Search by value  | O(n)       | Linear scan                                             |
| Append           | O(1)*      | Amortized — occasional resize is O(n)                   |
| Pop from end     | O(1)       |                                                         |
| Insert at start  | O(n)       | Shifts all elements right                               |
| Insert at middle | O(n)       | Shifts elements after index `i`                         |
| Pop from start   | O(n)       | Shifts all elements left → use `deque` if you need O(1) |
| Pop from middle  | O(n)       |                                                         |
| Remove by value  | O(n)       | Finds + shifts                                          |
| Length           | O(1)       | Stored as attribute                                     |
| Slicing          | O(b-a)     | Creates a new list                                      |
| Concatenation    | O(n + m)   | Creates a new list                                      |
| Sort             | O(n log n) | Timsort                                                 |
| Reverse          | O(n)       |                                                         |
| Min / Max / Sum  | O(n)       |                                                         |

> [!tip] Amortized O(1) for append Python lists over-allocate memory. When full, they double the capacity (O(n) copy). But this happens rarely, so the **average** cost per append is O(1).

## Creating Arrays

```python
# Empty list
arr = []
arr = list()

# With values
arr = [1, 2, 3, 4, 5]

# Repeated values (very useful in DSA for initializing)
zeros = [0] * 5            # [0, 0, 0, 0, 0]
grid = [[0] * 3 for _ in range(3)]  # 3x3 matrix of zeros

# From a range
arr = list(range(5))       # [0, 1, 2, 3, 4]
arr = list(range(2, 10, 2)) # [2, 4, 6, 8]

# From a string
chars = list("hello")      # ['h', 'e', 'l', 'l', 'o']
```

> [!warning] The 2D list trap Do NOT use `[[0] * 3] * 3` to create a 2D matrix. This creates **3 references to the same inner list** — modifying one modifies all. Always use a list comprehension: `[[0] * 3 for _ in range(3)]`



## Methods

### Append
O(1)
Adds an element to the **end**.
Code:
```python
arr = [1, 2, 3]
arr.append(4)        # [1, 2, 3, 4]
```

### Extend
O(k) where k is length of the iterable 
Adds **multiple elements** from an iterable.
Code:
```python
arr = [1, 2, 3]
arr.extend([4, 5])   # [1, 2, 3, 4, 5]
# Different from append:
arr.append([4, 5])   # [1, 2, 3, [4, 5]]  ← nested!
```

### Insert
O(n) 
Insert at a specific index (shifts elements right).
Code:
```python
arr = [1, 2, 4]
arr.insert(2, 3)     # [1, 2, 3, 4]
arr.insert(0, 0)     # [0, 1, 2, 3, 4]  ← O(n), expensive
```

### Pop
O(1) from end, O(n) from middle/start 
Removes and **returns** an element by index (default: last).
Code:
```python
arr = [1, 2, 3, 4]
last = arr.pop()     # returns 4, arr = [1, 2, 3]
first = arr.pop(0)   # returns 1, arr = [2, 3]  ← O(n)
```

### Remove
O(n) 
Removes the **first occurrence** of a value (raises `ValueError` if not found).
Code:
```python
arr = [1, 2, 3, 2]
arr.remove(2)        # [1, 3, 2]  ← only removes first 2
```

### Index
O(n) 
Returns the index of the **first occurrence** of a value.
Code:
```python
arr = [10, 20, 30, 20]
arr.index(20)        # 1
arr.index(99)        # ValueError
```

### Count
O(n) 
Counts occurrences of a value.
Code:
```python
arr = [1, 2, 2, 3, 2]
arr.count(2)         # 3
```

### Sort
O(n log n)
Code:
```python
arr = [3, 1, 4, 1, 5, 9, 2]
arr.sort()              # [1, 1, 2, 3, 4, 5, 9]
arr.sort(reverse=True)  # [9, 5, 4, 3, 2, 1, 1]
arr.sort(key=abs)       # sort by absolute value
```

### Sorted
O(n log n)
Returns a **new** list (doesn't modify original).
Code:
```python
arr = [3, 1, 2]
new_arr = sorted(arr)   # new_arr = [1, 2, 3], arr unchanged
```

### Reverse
O(n)
Code:
```python
arr = [1, 2, 3]
arr.reverse()        # [3, 2, 1]
```

### Clear
O(n)
Clear and delete every value of the array
Code:
```python
arr = [1, 2, 3]
arr.clear()          # []
```

### Copy
O(n) 
Shallow copy
Code:
```python
arr = [1, 2, 3]
new_arr = arr.copy()
new_arr = arr[:]     # same thing, slicing
new_arr = list(arr)  # same thing, constructor
```

## Slicing
Slicing creates a **new list** (does not modify original). 
Syntax: `arr[start:stop:step]` — `start` inclusive, `stop` exclusive.
Code:
```python
arr = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

arr[2:5]      # [2, 3, 4]
arr[:3]       # [0, 1, 2]    — from start
arr[7:]       # [7, 8, 9]    — to end
arr[:]        # full copy
arr[::2]      # [0, 2, 4, 6, 8]  — every 2nd element
arr[::-1]     # [9, 8, ..., 0]   — reversed
arr[-3:]      # [7, 8, 9]    — last 3
arr[:-2]      # [0, 1, ..., 7]   — all except last 2
```



## List Comprehensions
Concise way to build lists. Common in DSA.

```python
# Squares
squares = [x**2 for x in range(5)]       # [0, 1, 4, 9, 16]

# With condition (filter)
evens = [x for x in range(10) if x % 2 == 0]  # [0, 2, 4, 6, 8]

# Transform with condition
result = [x if x > 0 else 0 for x in [-1, 2, -3, 4]]  # [0, 2, 0, 4]

# 2D matrix
matrix = [[i*j for j in range(3)] for i in range(3)]
```

## Useful Built-in Functions

|Function|What it does|Big O|
|---|---|---|
|`len(arr)`|Length of the array|O(1)|
|`sum(arr)`|Sum of all elements|O(n)|
|`max(arr)`|Maximum value|O(n)|
|`min(arr)`|Minimum value|O(n)|
|`sorted(arr)`|Returns sorted **new** list|O(n log n)|
|`reversed(arr)`|Returns an iterator (use `list()` to materialize)|O(1) (lazy)|
|`enumerate(arr)`|Returns `(index, value)` pairs|O(1) (lazy)|
|`zip(a, b)`|Pairs up elements from two iterables|O(1) (lazy)|
|`any(arr)`|True if any element is truthy|O(n)|
|`all(arr)`|True if all elements are truthy|O(n)|
|`map(fn, arr)`|Applies fn to each element|O(1) (lazy)|
|`filter(fn, arr)`|Keeps elements where fn returns True|O(1) (lazy)|

```python
# enumerate — very common in DSA
for i, val in enumerate([10, 20, 30]):
    print(i, val)  # 0 10 / 1 20 / 2 30

# zip — pair iteration
for a, b in zip([1, 2, 3], ['a', 'b', 'c']):
    print(a, b)
```

## Common DSA Patterns with Arrays

### Two Pointers

Two indices that move through the array (often from opposite ends or same end at different speeds).

```python
# Example: check if array is a palindrome
def is_palindrome(arr):
    left, right = 0, len(arr) - 1
    while left < right:
        if arr[left] != arr[right]:
            return False
        left += 1
        right -= 1
    return True
```

### Sliding Window

See [[General Concepts]] — already covered in detail.

### Prefix Sum

Precompute cumulative sums for O(1) range queries.

```python
arr = [1, 2, 3, 4, 5]
prefix = [0]
for x in arr:
    prefix.append(prefix[-1] + x)
# prefix = [0, 1, 3, 6, 10, 15]
# Sum of arr[i:j] = prefix[j] - prefix[i]
```

### In-place Modification

Modify the array without using extra space — often required for O(1) space complexity.

```python
# Reverse in place
def reverse(arr):
    left, right = 0, len(arr) - 1
    while left < right:
        arr[left], arr[right] = arr[right], arr[left]
        left += 1
        right -= 1
```

> [!tip] Pythonic swap `a, b = b, a` — no temp variable needed. Very common in DSA.

## Common Pitfalls

> [!warning] Modifying a list while iterating Don't add/remove elements from a list during a `for` loop — it causes skipped elements or `IndexError`.
> 
> ```python
> # ❌ Bad
> for x in arr:
>     if x % 2 == 0:
>         arr.remove(x)
> 
> # ✅ Good — iterate over a copy, or build a new list
> arr = [x for x in arr if x % 2 != 0]
> ```

> [!warning] `is` vs `==` `==` compares **values**. `is` compares **memory identity**.
> 
> ```python
> a = [1, 2, 3]
> b = [1, 2, 3]
> a == b   # True (same values)
> a is b   # False (different objects in memory)
> ```

> [!warning] Mutable default arguments
> 
> ```python
> # ❌ Bug: the default list is shared across all calls
> def add_item(item, arr=[]):
>     arr.append(item)
>     return arr
> 
> # ✅ Use None as default
> def add_item(item, arr=None):
>     if arr is None:
>         arr = []
>     arr.append(item)
>     return arr
> ```

> [!warning] Shallow vs deep copy `arr.copy()` and `arr[:]` create a **shallow copy** — nested objects are still shared.
> 
> ```python
> import copy
> deep = copy.deepcopy(arr)  # for nested structures
> ```



## Exercises

[[Arrays Problems]]

