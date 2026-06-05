
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



# [002] Problem Title

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
