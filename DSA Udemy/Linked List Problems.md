
[[Linked List]]
[[Linked List LeetCode]]

# [000] Problem Title

## Problem

## Pseudo Code

## Example:
Input:  
Output:

## Hints

## Solution
```python
# code here
```

## Conclusion
- What did this problem teach me?
- Edge cases to remember
- Common mistakes



# [001] Find Middle Node

## Problem
Implement the **find_middle_node** method for the LinkedList class.  
  
**Note: this LinkedList implementation does not have a lengt member variable.**  
  
If the linked list has an even number of nodes, return the first node of the second half of the list.  
  
Keep in mind the following requirements:

- The method should use a two-pointer approach, where one pointer (slow) moves one node at a time and the other pointer (fast) moves two nodes at a time.
    
- When the fast pointer reaches the end of the list or has no next node, the slow pointer should be at the middle node of the list.
    
- The method should return the middle node when the number of nodes is odd or the first node of the second half of the list if the list has an even number of nodes.
    
- The method should only traverse the linked list once.  In other words, you can only use one loop.

## Pseudo Code:
INITIALIZE slow and fast pointers to head of the linked list

WHILE fast is not None and fast.next is not None: MOVE slow pointer one step (slow = slow.next) MOVE fast pointer two steps (fast = fast.next.next)

RETURN slow pointer (middle node of the linked list)

## Solution
```python
class Node:
    def __init__(self, value):
        self.value = value
        self.next = None
        

class LinkedList:
    def __init__(self, value):
        new_node = Node(value)
        self.head = new_node
        self.tail = new_node
        
    def append(self, value):
        new_node = Node(value)
        if self.head == None:
            self.head = new_node
            self.tail = new_node
        else:
            self.tail.next = new_node
            self.tail = new_node
        return True
        
    def find_middle_node(self):
        slow = self.head
        fast = self.head
        while fast is not None and fast.next is not None:
            slow = slow.next
            fast = fast.next.next
        return slow

my_linked_list = LinkedList(1)
my_linked_list.append(2)
my_linked_list.append(3)
my_linked_list.append(4)
my_linked_list.append(5)

print( my_linked_list.find_middle_node().value )
```

## Conclusion
The `find_middle_node` method efficiently locates the middle of a linked list by using a two-pointer technique. The slow pointer moves at half the speed of the fast pointer. By the time the fast pointer has traveled the full length of the list, the slow pointer has traveled half the length, landing it in the middle. In our example, the middle of `1 → 2 → 3 → 4 → 5` is node `3`, and the method will return this node.



# [002] Has Loop

## Problem
Write a method called **has_loop** that is part of the linked list class.  
  
The method should be able to detect if there is a cycle or loop present in the linked list.  
  
You are required to use Floyd's cycle-finding algorithm (also known as the "tortoise and the hare" algorithm) to detect the loop.  
  
This algorithm uses two pointers: a slow pointer and a fast pointer. The slow pointer moves one step at a time, while the fast pointer moves two steps at a time. If there is a loop in the linked list, the two pointers will eventually meet at some point. If there is no loop, the fast pointer will reach the end of the list.  
  
The method should follow these guidelines:

1. Create two pointers, `low` and `fast`, both initially pointing to the head of the linked list.
    
2. Traverse the list with the `slow` pointer moving one step at a time, while the `fast` pointer moves two steps at a time.
    
3. If there is a loop in the list, the `fast` pointer will eventually meet the `slow` pointer. If this occurs, the method should return `True`.
    
4. If the `fast` pointer reaches the end of the list or encounters a `None` value, it means there is no loop in the list. In this case, the method should return `False`.

If your Linked List contains a loop, it indicates a flaw in its implementation. This situation can manifest in several ways:
1) 
![](https://img-c.udemycdn.com/redactor/raw/coding_exercise_instructions/2023-09-23_16-42-34-1b7d5fde027727870dad175c13232bc8.png)
2) 
![430](https://img-c.udemycdn.com/redactor/raw/coding_exercise_instructions/2023-09-23_16-42-34-94c6db037cd4e8ef109113cd2f66a6a3.png)
3) 
![](https://img-c.udemycdn.com/redactor/raw/coding_exercise_instructions/2024-02-05_17-26-21-194963fe94c09e3c42823633a2898baf.png)

## Pseudo Code
Initialize slow and fast pointers to head of the list

while fast is not None and fast.next is not None:
	move slow pointer one step forward
	move fast pointer two steps forward
	if slow and fast pointers are equal:
	        return True (loop found)

return False (loop not found)

## Solution
```python
class Node:
    def __init__(self, value):
        self.value = value
        self.next = None
        
class LinkedList:
    def __init__(self, value):
        new_node = Node(value)
        self.head = new_node
        self.tail = new_node
        
    def append(self, value):
        new_node = Node(value)
        if self.head == None:
            self.head = new_node
            self.tail = new_node
        else:
            self.tail.next = new_node
            self.tail = new_node
        return True
        
    def has_loop(self):
        slow = self.head
        fast = self.head
        while fast is not None and fast.next is not None:
            slow = slow.next
            fast = fast.next.next
            if fast == slow:
	            return True
	        
	    return False

my_linked_list = LinkedList(1)
my_linked_list.append(2)
my_linked_list.append(3)
my_linked_list.append(4)
my_linked_list.append(5)

print(my_linked_list.has_loop())
```

## Conclusion
The `has_loop` method efficiently determines if a linked list contains a cycle or loop. By advancing one pointer at double the speed of the other, and checking if they ever meet, we can identify loops without needing to use any additional memory or mark visited nodes. If they meet, there's a loop. If they don't, the list has no loops.



# [003] Find Kth Node from End

## Problem
Implement the `find_kth_from_end` function, which takes the LinkedList (ll) and an integer k as input, and returns the k-th node from the end of the linked list **WITHOUT USING LENGTH**.

**NOTE: This is a SEPARATE FUNCTION that is NOT a method within the LinkedList class.  This means you need to indent the function all the way to the LEFT.** 

Given this LinkedList:  
  
`1 -> 2 -> 3 -> 4 -> 5`  
  
If `k=1` then return the first node from the end (the last node) which contains the value of `5`.  
  
If `k=2` then return the second node from the end which contains the value of `4`, etc.  
  
If the index is out of bounds, the program should return `None`.  

The find_kth_from_end function should follow these requirements:

1. The function should utilize two pointers, slow and fast, initialized to the head of the linked list.
    
2. The fast pointer should move k nodes ahead in the list.
    
3. If the fast pointer becomes None before moving k nodes, the function should return None, as the list is shorter than k nodes.
    
4. The slow and fast pointers should then move forward in the list at the same time until the fast pointer reaches the end of the list.
    
5. The function should return the slow pointer, which will be at the k-th position from the end of the list.

## Pseudo Code

initialize slow and fast pointers to the head of the linked list

for i in range k:
    if fast pointer is None:
        return None (list is shorter than k)
    move fast pointer to the next node

while fast pointer is not None:
    move slow pointer to the next node
    move fast pointer to the next node

return the slow pointer (k-th node from the end)

## Solution
```python
class Node:
    def __init__(self, value):
        self.value = value
        self.next = None
        
class LinkedList:
    def __init__(self, value):
        new_node = Node(value)
        self.head = new_node
        self.tail = new_node
        
    def append(self, value):
        new_node = Node(value)
        if self.head == None:
            self.head = new_node
            self.tail = new_node
        else:
            self.tail.next = new_node
            self.tail = new_node
        return True
        
def find_kth_from_end(linked_list, k):
	slow = linked_list.head
	fast = linked_list.head
	
	for _ in range(index):
		if fast is None:
			return None
		fast = fast.next
		
	while fast is not None:
		slow = slow.next
		fast = fast.next
			
	return slow


my_linked_list = LinkedList(1)
my_linked_list.append(2)
my_linked_list.append(3)
my_linked_list.append(4)
my_linked_list.append(5)

k = 2
result = find_kth_from_end(my_linked_list, k)
print(result.value)  # Output: 4
```

## Conclusion
The `find_kth_from_end` function uses the two-pointer technique to efficiently find the kth node from the end of a linked list. By first positioning the fast pointer `k` nodes ahead of the slow pointer and then moving both pointers at the same speed, we ensure that when the fast pointer reaches the end, the slow pointer is at the desired kth node from the end. In our example, the function would return node `6` as the 3rd node from the end.



# [004] Remove Duplicates

## Problem
You are given a singly linked list that contains integer values, where some of these values may be duplicated.  
  
**Note: this linked list class does NOT have a tail which will make this method easier to implement.**  
  
Your task is to implement a method called **remove_duplicates()** within the LinkedList class that removes all duplicate values from the list.  
  
Your method should not create a new list, but rather modify the existing list in-place, preserving the relative order of the nodes.  
  
You can implement the **remove_duplicates()** method in two different ways:

1. Using a Set - This approach will have a time complexity of O(n), where n is the number of nodes in the linked list. You are allowed to use the provided Set data structure in your implementation.
    
2. Without using a Set - This approach will have a time complexity of O(n^2), where n is the number of nodes in the linked list. You are not allowed to use any additional data structures for this implementation.

## Pseudo Code
method remove_duplicates():
    // Initialize an empty set to store unique values
    create an empty set called values
 
   // Initialize two pointers, previous and current
    set previous to None
    set current to head of the list
    
   // Iterate through the list
    while current is not None:
        // If the current node's value is already in the set, remove the duplicate node
        if current.value is in values:
            set previous.next to current.next
            decrement list length by 1
        // Else, add the current node's value to the set and update previous
        else:
            add current.value to values
            set previous to current
        // Move to the next node
        set current to current.next

## Example:
Input:
LinkedList: 1 -> 2 -> 3 -> 1 -> 4 -> 2 -> 5

Output:
LinkedList: 1 -> 2 -> 3 -> 4 -> 5

## Solution
```python
class Node:
    def __init__(self, value):
        self.value = value
        self.next = None
        
class LinkedList:
    def __init__(self, value):
        new_node = Node(value)
        self.head = new_node
        self.tail = new_node
        
    def append(self, value):
        new_node = Node(value)
        if self.head == None:
            self.head = new_node
            self.tail = new_node
        else:
            self.tail.next = new_node
            self.tail = new_node
        return True
        
def remove_duplicates(self):


my_linked_list = LinkedList(1)
my_linked_list.append(2)
my_linked_list.append(3)
my_linked_list.append(4)
my_linked_list.append(5)
```

## Conclusion
- What did this problem teach me?
- Edge cases to remember
- Common mistakes



# [005] Binary to Decimals

## Problem
Your task is to implement the `binary_to_decimal` method for the LinkedList class. This method should convert a binary number, represented as a linked list, to its decimal equivalent.

In this context, a binary number is a sequence of 0s and 1s. The LinkedList class represents this binary number such that each node in the linked list contains a single digit (0 or 1) of the binary number, and the whole number is formed by traversing the linked list from the head to the end.  
  
The `binary_to_decimal` method should start from the head of the linked list and use each node's value to calculate the corresponding decimal number. The formula to convert a binary number to decimal is as follows:  
  
To put it in simple terms, each digit of the binary number is multiplied by 2 raised to the power equivalent to the position of the digit, counting from right to left starting from 0, and all the results are summed together to get the decimal number.  
  
The `binary_to_decimal` method should return this calculated decimal number.

## Pseudo Code

## Example:
Consider the binary number 101. If this number is represented as a linked list, the head of the linked list will contain the digit 1, the next node will contain 0, and the last node will contain 1. When we apply the `binary_to_decimal` method on this linked list, the method should return the number 5, which is the decimal equivalent of binary 101.  
  
Similarly, for a linked list representing the binary number 1101, the `binary_to_decimal` method should return the number 13.


## Hints

## Solution
```python
# code here
```

## Conclusion
- What did this problem teach me?
- Edge cases to remember
- Common mistakes



# [006] Partition List

## Problem
**⚠️ CAUTION: Advanced Challenge Ahead!**

This Linked List problem is significantly more challenging than the ones we've tackled so far. It's common for students at this stage to find this exercise demanding, so don't worry if you're not ready to tackle it yet. It's perfectly okay to set it aside and revisit it later when you feel more confident.  
  
If you decide to take on this challenge, I strongly advise using a hands-on approach: grab a piece of paper and visually map out each step.  
  
This problem requires a clear understanding of how elements in a Linked List interact and move. By now, you've observed numerous Linked List animations in the course, which have prepared you for this moment.  
  
This exercise will be a true test of your ability to apply those concepts practically. Remember, patience and persistence are key here!  
  
**Now, here is the exercise:**  

Implement the **partition_list** member function for the LinkedList class, which partitions the list such that all nodes with values less than x come before nodes with values greater than or equal to x.  
  
**Note:  This linked list class does NOT have a tail which will make this method easier to implement.**  
  
The original relative order of the nodes should be preserved.

**Details:**

The function partition_list takes an integer x as a parameter and modifies the current linked list in place according to the specified criteria. If the linked list is empty (i.e., head is null), the function should return immediately without making any changes.

## Pseudo Code

## Example:
1) 
**Input:**
Linked List: `3 -> 8 -> 5 -> 10 -> 2 -> 1` x: `5`

**Process:**
- Values less than 5: `3`, `2`, `1`
- Values greater than or equal to 5: `8`, `5`, `10`

**Output:**
Linked List: `3 -> 2 -> 1 -> 8 -> 5 -> 10`

2) 
**Input:**
Linked List: `1 -> 4 -> 3 -> 2 -> 5 -> 2` x: `3`

**Process:**
- Values less than 3: `1`, `2`, `2`
- Values greater than or equal to 3: `4`, `3`, `5`

**Output:**
Linked List: `1 -> 2 -> 2 -> 4 -> 3 -> 5`

## Hints
- While traversing the linked list, maintain two separate chains: one for values less than `x` and one for values greater than or equal to `x`.
    
- Use dummy nodes to simplify the handling of the heads of these chains.
    
- After processing the entire list, connect the two chains to get the desired arrangement.

## Notes:
**Note:**

The solution must maintain the relative order of nodes. For instance, in the first example, even though `8` appears before `5` in the original list, the partitioned list must still have `8` before `5` as their relative order remains unchanged.  
  
**Note:**

You must solve the problem **WITHOUT MODIFYING THE VALUES** in the list's nodes (i.e., only the nodes' `next` pointers may be changed.)

## Solution
```python
# code here
```

## Conclusion
- What did this problem teach me?
- Edge cases to remember
- Common mistakes



# [007] Reverse Between

## Problem
**⚠️ Advanced Challenge Alert: Linked List Mastery!  
  
**Welcome to what many consider the pinnacle of Linked List challenges in this course! This exercise is not just a test of your coding skills, but also a measure of your problem-solving ability and understanding of complex data structures.  
  
**Here's how you can tackle it:**

1. **Visualize the Problem:** Before diving into coding, grab a pen and paper. Sketch out the linked list and visualize each step of the process. This approach isn't just for beginners; it's exactly how seasoned developers plan their attack on complex problems.
    
2. **Seek Understanding Over Speed:** Take your time to really grasp each part of the problem. The goal here is deep understanding, not just a quick solution. If you find yourself stuck, that's a part of the learning process.
    
3. **It's Okay to Take a Break:** Feel free to step away from this challenge and return later. This course is designed to equip you with a growing set of skills, and sometimes, a bit of distance can bring new insights.
    
4. **Approach Like a Pro:** Remember, facing a challenging problem is what being a professional developer is all about. Use this exercise to think, plan, and code like a pro.    

**Now, let's dive into the exercise:**  

You are given a singly linked list and two integers `start_index` and `end_index`.  
  
Your task is to write a method `reverse_between` within the `LinkedList` class that reverses the nodes of the linked list from `start_index` to  `end_index` (inclusive using 0-based indexing) in one pass and in-place.  
  
**Note:** **the Linked List does not have a** `tail` **which will make the implementation easier.  
  
Assumption**: You can assume that `start_index` and `end_index` are **not** out of bounds.

## Pseudo Code

## Example:
**Input**
- The method `reverse_between` takes two integer inputs `start_index` and `end_index`.
- The method will only be passed valid indexes (you do not need to test whether the indexes are out of bounds)

**Output**
- The method should modify the linked list in-place by reversing the nodes from `start_index` to  `end_index`.
- If the linked list is empty or has only one node, the method should return `None`.

**Example**
Suppose the linked list is `1 -> 2 -> 3 -> 4 -> 5`, and `start_index = 2` and `end_index = 4`. Then, the method should modify the linked list to `1 -> 2 -> 5 -> 4 -> 3`

## Hints
The algorithm should run in one pass and in-place, with a time complexity of O(n) and a space complexity of O(1).

## Solution
```python
# code here
```

## Conclusion
- What did this problem teach me?
- Edge cases to remember
- Common mistakes



# [008] Swap Nodes in Pairs

## Problem
Write a method called `swap_pairs` inside the `LinkedList` class.  
  
This method should swap every two adjacent nodes in the linked list **by adjusting the pointers**, not the node values.  
  
You must modify the list in-place and update the head accordingly.  
  
If the list has an odd number of nodes, the final node remains in its original position.  
  
You should use a dummy node to simplify the pointer adjustments.  
  
For example, if the list is `1 -> 2 -> 3 -> 4`, the method should transform it to `2 -> 1 -> 4 -> 3`. 
  
If the list has an odd number of nodes, the last node remains in place (e.g., `1 -> 2 -> 3` becomes `2 -> 1 -> 3`).

## Pseudo Code

## Example:
**Input**:
- The method operates on the linked list via self.head, which points to the first node or is None for an empty list.    
- Each node has an integer value and a next pointer to the next node or None.

**Output**:
- No return value (None); the method modifies the linked list in place.    
- The self.head attribute must be updated to point to the head of the modified list after swapping.

**Examples**:
1. **Example 1**:
    - Input List: 1 -> 2 -> 3 -> 4
    - Output List: 2 -> 1 -> 4 -> 3
    - Explanation: Swap the first pair (1, 2) to get 2 -> 1 -> 3 -> 4, then swap the second pair (3, 4) to get 2 -> 1 -> 4 -> 3.

2. **Example 2**:    
    - Input List: 1 -> 2 -> 3
    - Output List: 2 -> 1 -> 3
    - Explanation: Swap the first pair (1, 2) to get 2 -> 1 -> 3. The last node (3) has no pair, so it stays in place.

3. **Example 3**:    
    - Input List: 1
    - Output List: 1
    - Explanation: A single node has no pair to swap, so the list remains unchanged.

4. **Example 4**:    
    - Input List: [] (empty list)
    - Output List: []
    - Explanation: An empty list has no nodes to swap, so it remains empty.

5. **Example 5**:    
    - Input List: 1 -> 2
    - Output List: 2 -> 1
    - Explanation: Swap the only pair (1, 2) to get 2 -> 1.

## Hints
- Ensure self.head is correctly updated to point to the new first node after all swaps.
    
- Handle edge cases like empty lists, single nodes, and lists with odd or even node counts.
    
- Consider using a dummy node to simplify swapping the head node.

## Solution
```python
# code here
```

## Conclusion
- What did this problem teach me?
- Edge cases to remember
- Common mistakes
