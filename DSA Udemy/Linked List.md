
[[General Concepts]]

A **linked list** is a linear data structure consisting of a sequence of elements called **nodes**, where each node contains data and a **pointer (or reference)** to the next node in the sequence

![[Pasted image 20260604171844.png]]
*Head:* First value
*Tail:* last value (Pointer points to None)

Linked Lists vs. Arrays

| Feature                  | Linked List                                 | Array                                    |
| ------------------------ | ------------------------------------------- | ---------------------------------------- |
| **Memory Allocation**    | Dynamic (allocated at runtime as needed)    | Static (fixed size allocated upfront)    |
| **Memory Layout**        | Non-contiguous (scattered in memory)        | Contiguous (sequential memory block)     |
| **Element Access**       | Sequential access (\(O(N)\) time)           | Random access via index (\(O(1)\) time)  |
| **Insertion / Deletion** | Efficient (\(O(1)\) if pointer is known)    | Inefficient (requires shifting elements) |
| **Memory Overhead**      | Higher (requires extra memory for pointers) | Lower (only stores the raw data)         |

LL are implemented as class with methods and NOT built-in function
Every value points to the next
Every value is a node

Big O:
- Append values = 0(1)
- Append first value = 0(1)
- Append middle values = O(n) # Iterate through entire list
- Remove values = O(n)
- Remove middle values = O(n)
- Search for a value = O(n)

Functions:
- Append = O(1)
- Pop = O(n)
- Prepend = O(1)
- Pop First = O(1)
- Insert = O(n)
- Remove = O(n)
- Search index = O(n)
- Search value = O(n)

## Node
![[Pasted image 20260604172850.png]]


## Example code:
```python
class Node: 
	def __init__(self, value): 
		self.value = value
		self.next = None 

# Conceptually equivalent to: 
{'value': 4, 'next': None}
```


[[DSA Problems]]