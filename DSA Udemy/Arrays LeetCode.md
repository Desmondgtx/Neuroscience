
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



# [001] Contains Duplicate

## Problem
Given an integer array `nums`, return `True` if any value appears **more than once** in the array, otherwise return `False`.

## Example:
**Example 1:**
```java
Input: nums = [1, 2, 3, 3]

Output: True
```

**Example 2:**
```java
Input: nums = [1, 2, 3, 4]

Output: False
```

## Hints
A brute force solution would be to check every element against every other element in the array. This would be an `O(n^2)` solution.

## Solution
```python
class Solution:
    def hasDuplicate(self, nums: List[int]) -> bool:
        for i in range(len(nums)):
            for j in range(i + 1, len(nums)):
                if nums[i] == nums[j]:
                    return True
        return False
```



# [002] Problem Title

## Problem
Given an array of integers `nums` and an integer `target`, return the indices `i` and `j` such that `nums[i] + nums[j] == target` and `i != j`.

You may assume that _every_ input has exactly one pair of indices `i` and `j` that satisfy the condition.

Return the answer with the smaller index first.


## Example:
**Example 1:**
```java
Input: 
nums = [3,4,5,6], target = 7

Output: [0,1]
```
Explanation: `nums[0] + nums[1] == 7`, so we return `[0, 1]`.

**Example 2:**
```java
Input: nums = [4,5,6], target = 10

Output: [0,2]
```

**Example 3:**
```java
Input: nums = [5,5], target = 10

Output: [0,1]
```

## Hints
A brute force solution would be to check every pair of numbers in the array. This would be an `O(n^2)` solution.

## Solution
```python
# code here
```
