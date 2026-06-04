
###  One loop: 
- O(n)

Example code:
```python
for i in range (n)

def print_items(n):
	for i in range(n):
		print(i)
		
print_items(10) # 0 1 2 3 4 5 6 7 8 9
```


### Drop Constants
O(n) + O(n) = O(2n) = O(n)

Example code:
```python
def print_items(n):
	for i in range(n):
		print(i)
	
	for j in range(n):
		print(j)
		
print_items(10)
# 0 1 2 3 4 5 6 7 8 9
# 0 1 2 3 4 5 6 7 8 9
```


### Nested Loops
- O(n²)

Example code:
```python
for i in range (n)
	for j in range(i+1, n)
	
def print_items(n):
	for i in range(n):
		for j in range(n):
			print(i, j)
		
print_items(10)
# 00
# 01
# 02 ...
```


### Drop non dominants functions or loops
- O(n²) + O(n) = O(n² + n) = O(n²)

Example code:
```python
def print_items(n): 
	for i in range(n):
		for j in range(n):
			print(i, j)
		# Loop 1 = Nested loop O(n²)
		
	for k in range(n):
		print(k) 
		# Loop 2: Dropped from the equation
		

print_items(10)
# 00
# 01
# 02 ... 
# 0 1 2 3 4 5 6 7 8 9
```


### Drop repetitions
- O(1)

Example code:
```python
def add_items(n):
	return n + n + n ...
```
### Cuting arryas in a half
- O(log n)

### Different Terms
- O(a + b)

Example code:
```python
def add_items(a, b):
	for i in range(a):
		print(i)
		
	for j in range(b):
		print(j)
```

- O(a * b)

Example code:
```python
def add_items(a, b):
	for i in range(a):
		for j in range(b):
			print(i, j)
```



# Big-O Cheatsheet

## Big-O Complexity Chart

![[2026-06-03_21-57-43_region.png]]

## Common Data Structure Operations

![[2026-06-03_21-56-51_region.png]]

## Array Sorting Algorithms

![[2026-06-03_21-57-11_region.png]]


Next Chapter: [[Linked List]]