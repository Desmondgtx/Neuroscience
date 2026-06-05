
[[General Concepts]]

A **linked list** is a linear data structure consisting of a sequence of elements called **nodes**, where each node contains data and a **pointer (or reference)** to the next node in the sequence

![[Linked List.png]]
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
![[Linked List single Node.png]]

### Example code:
```python
class Node: 
	def __init__(self, value): 
		self.value = value # value of the node
		self.next = None  # pointer

# Conceptually equivalent to: 
{'value': 4, 'next': None}

# Call the function
# Create a single node 
my_node = Node(4) 
print(my_node.value) # → 4 
print(my_node.next) # → None 

# Create and manually link two nodes 
node1 = Node(4) 
node2 = Node(7) 
node1.next = node2 

print(node1.next.value) # → 7
```



## Methods
### Constructor
Code:
```python
class LinkedList:
	def __init__(self, value):
		new_node = Node(value) # create new node
		self.head = new_node
		self.tail = new_node
		self.length += 1
		
# Calling the LL class
my_linked_list = LinkedList(4)
print(my_linked_list.head.value)
```

### Print List
O(n)
Code:
```python
class LinkedList:
	def __init__(self, value):
		new_node = Node(value) # create new node
		self.head = new_node
		self.tail = new_node
		self.length += 1
		
	def print_list(self): # Function that print list
		temp = self.head
		while temp is not None:
			print(temp.value)
			temp = temp.next
```

### Append
O(1)
Code:
```python
class LinkedList:
	def __init__(self, value):
		new_node = Node(value) # create new node
		self.head = new_node
		self.tail = new_node
		self.length += 1
		
	def append(self, value) # Append new node to the tail of the LL
		new_node = Node(value)
		if self.head is None: # if LL is empty
			self.head = new_node
			self.tail = new_node
		else:
			self.tail.next = new_node
			self.tail = new_node
		
		self.length += 1
		return True
```

### Pop
O(n)
3 use cases:
- Long Linked List
- 1 element LL
- 0 element LL
Code:
```python
class LinkedList:
	def __init__(self, value):
		new_node = Node(value) # create new node
		self.head = new_node
		self.tail = new_node
		self.length += 1
		
	def pop(self):
		# Empty LL case
		if self.length == 0:
			return None
		
		# Two or more nodes case
		temp = self.head # Initialize variables
		pre = self.head
		while(temp.next):
			pre = temp
			temp = temp.next
		self.tail = pre # Remove last node
		self.tail.next = None # Remove last pointer
		self.length -= 1
		
		# Just one variable case
		if self.length == 0:
			self.head = None # Empty variables
			self.tail = None
		
		return temp
```

### Prepend
O(1)
- New node = Head of LL
- 2 cases:
	- Existing elements on the LL
	- No elements on the LL
Code:
```python
class LinkedList:
	def __init__(self, value):
		new_node = Node(value) # create new node
		self.head = new_node
		self.tail = new_node
		self.length += 1
		
		def prepend(self, value):
		new_node = Node(value)
		
		# No elements scenario
		if self.length == 0:
			self.head = new_node
			self.tail = new_node
		# Existing elements scenario
		else:
			new_node.next = self.head
			self.head = new_node
		self.length += 1
		
		return True
```

### Pop First
O(1)
- 3 Cases:
	- 0 elements
	- 1 element
	- 2 or more elements
Code:
```python
class LinkedList:
	def __init__(self, value):
		new_node = Node(value) # create new node
		self.head = new_node
		self.tail = new_node
		self.length += 1
		
		def pop_first(self):
			if self.length == 0:
				return None
				
		temp = self.head
		self.head = self.head.next
		temp.next = None
		self.length -= 1
		
		if self.length == 0:
			self.tail = None
		
		return temp.value
```

### Get
O(n)
Search by index
Code:
```python
class LinkedList:
	def __init__(self, value):
		new_node = Node(value) # create new node
		self.head = new_node
		self.tail = new_node
		self.length += 1
		
	def get(self, index):
		if index < 0 or index >= self.length:
			return None # Index out of range
			
		temp = self.head
		for _ in range(index):
			temp = temp.next
		return temp.value
```

### Set
O(n)
Found by index
Change value (replace)
Code:
```python
class LinkedList:
	def __init__(self, value):
		new_node = Node(value) # create new node
		self.head = new_node
		self.tail = new_node
		self.length += 1
		
	def set_value(self, index, value):
		temp = self.get(index)
		if temp:
			temp.value = value
			return True
		return False
```
### Insert
O(n)
Insert by index (no replace)
Code:
```python
class LinkedList:
	def __init__(self, value):
		new_node = Node(value) # create new node
		self.head = new_node
		self.tail = new_node
		self.length += 1
		
	def insert(self, index, value):
		if index < 0 or index > self.length:
			return False # Out of range
		
		#Prepend functions
		if index == 0:
			return self.prepend(value)
			
		# Append function
		if index == self.length: 
			return self.append(value)
		
		new_node = Node(value) # Create Node
		temp = self.get(index-1) # Previous Node
		new_node.next = temp.next # New Node pointer
		temp.next = new_node # Previous pointer
		self.length += 1
		return True
		
linked_list.insert(1,1)
# Variable Method index and value
```

### Remove
O(n)
Remove value by index
Code:
```python
class LinkedList:
	def __init__(self, value):
		new_node = Node(value) # create new node
		self.head = new_node
		self.tail = new_node
		self.length += 1
		
	def remove(self, index):
		if index < 0 or index >= self.length:
			return None # Out of range
		if index == 0:
			return self.pop_first()
		if index == self.length:
			return self.pop()
		
		prev = self.get(index-1)
		temp = prev.next # Remove Node
		prev.next = temp.next
		temp.next = None # Delete Node
		self.length -= 1
		return temp
```

### Reverse
Common interview question
Reverse the entire Linked List
Switch head and tail variables
Reverse pointers
Code:
```python
class LinkedList:
	def __init__(self, value):
		new_node = Node(value) # create new node
		self.head = new_node
		self.tail = new_node
		self.length += 1
		
	def reverse(self):
		temp = self.head
		self.head = self.tail # Switching head and tail
		self.tail = temp
		
		after = temp.next # Create variables
		before = None
		for _ in range(self.length):
			after = temp.next
			temp.next = before # Reverse pointer
			before = temp # Advance variables
			temp = after
			
linked_list.reverse()
# Variable Function Instantiate
```



## Exercises
[[Linked List Problems]]
[[Linked List LeetCode]]
