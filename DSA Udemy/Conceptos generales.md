
## Definitions
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


## Data Structures
- Arrays
- Lists
- Tuples
- Dictionaries
Uses {}
2 parameters: 'Key' and 'value'
Example:
{nombre: "Diego",
 apellido: "Garrido"}



- Linked Lists
- Trees
- Graphs
- Stacks
- Queues
- Hash Tables / Hash Maps
- Hash Sets
Generate a Dictionarie or Hash set
	{} = Dictionarie or Hash Map
	() = Hash Set
Run through array and append values 

```Python
for n in nums:
	if num in set:
		return True
	set.add(n) # add n to the set
return false
```


## Algorithms

### Nested Loops:
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


### Sliding Window
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
























[[Linked List]]

[[Problemas DSA]]