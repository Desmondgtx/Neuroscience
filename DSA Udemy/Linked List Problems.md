
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

## Notes
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

## Notes
The `**find_middle_node**` method efficiently locates the middle of a linked list by using a two-pointer technique. The slow pointer moves at half the speed of the fast pointer. By the time the fast pointer has traveled the full length of the list, the slow pointer has traveled half the length, landing it in the middle. In our example, the middle of `**1 → 2 → 3 → 4 → 5**` is node `**3**`, and the method will return this node.



# [002] Has Loop

## Problem
Write a method called **has_loop** that is part of the linked list class.  
  
The method should be able to detect if there is a cycle or loop present in the linked list.  
  
You are required to use Floyd's cycle-finding algorithm (also known as the "tortoise and the hare" algorithm) to detect the loop.  
  
This algorithm uses two pointers: a slow pointer and a fast pointer. The slow pointer moves one step at a time, while the fast pointer moves two steps at a time. If there is a loop in the linked list, the two pointers will eventually meet at some point. If there is no loop, the fast pointer will reach the end of the list.  
  
The method should follow these guidelines:

1. Create two pointers, `**slow**` and `**fast**`, both initially pointing to the head of the linked list.
    
2. Traverse the list with the `**slow**` pointer moving one step at a time, while the `**fast**` pointer moves two steps at a time.
    
3. If there is a loop in the list, the `**fast**` pointer will eventually meet the `**slow**` pointer. If this occurs, the method should return `**True**`.
    
4. If the `**fast**` pointer reaches the end of the list or encounters a `**None**` value, it means there is no loop in the list. In this case, the method should return `**False**`.

If your Linked List contains a loop, it indicates a flaw in its implementation. This situation can manifest in several ways:
1) 
![](https://img-c.udemycdn.com/redactor/raw/coding_exercise_instructions/2023-09-23_16-42-34-1b7d5fde027727870dad175c13232bc8.png)
2) 
![](https://img-c.udemycdn.com/redactor/raw/coding_exercise_instructions/2023-09-23_16-42-34-94c6db037cd4e8ef109113cd2f66a6a3.png)
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

print( my_linked_list.has_loop())
```

## Notes
The `**has_loop**` method efficiently determines if a linked list contains a cycle or loop. By advancing one pointer at double the speed of the other, and checking if they ever meet, we can identify loops without needing to use any additional memory or mark visited nodes. If they meet, there's a loop. If they don't, the list has no loops.



# [003] Find Kth Node from End

## Problem
Implement the `**find_kth_from_end**` function, which takes the LinkedList (ll) and an integer k as input, and returns the k-th node from the end of the linked list **WITHOUT USING LENGTH**.

**NOTE: This is a SEPARATE FUNCTION that is NOT a method within the LinkedList class.  This means you need to indent the function all the way to the LEFT.** 

Given this LinkedList:  
  
`**1 -> 2 -> 3 -> 4 -> 5**`  
  
If `**k=1**` then return the first node from the end (the last node) which contains the value of `**5**`.  
  
If `**k=2**` then return the second node from the end which contains the value of `**4**`, etc.  
  
If the index is out of bounds, the program should return `**None**`.  
  
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
        


my_linked_list = LinkedList(1)
my_linked_list.append(2)
my_linked_list.append(3)
my_linked_list.append(4)
my_linked_list.append(5)


```

## Notes
The `**find_kth_from_end**` function uses the two-pointer technique to efficiently find the kth node from the end of a linked list. By first positioning the fast pointer `**k**` nodes ahead of the slow pointer and then moving both pointers at the same speed, we ensure that when the fast pointer reaches the end, the slow pointer is at the desired kth node from the end. In our example, the function would return node `**6**` as the 3rd node from the end.
