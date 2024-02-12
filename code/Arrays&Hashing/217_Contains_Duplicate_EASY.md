# Intuition
Initially, the problem seems straightforward - identifying if there are duplicates in a list. My first thought was to use a data structure that can automatically handle duplicates, 
such as a set, and compare it with the original list.

# Approach
The approach is quite simple. Convert the list of numbers into a set, which automatically removes any duplicates. Then, compare the length of the original list with the length of 
the set. If the lengths are different, it means there were duplicates in the original list, since the set would be smaller.

# Complexity
- Time complexity:
The time complexity is O(n), where n is the number of elements in the list. This is because converting a list to a set requires checking each element in the list once.

- Space complexity:
The space complexity is also O(n), as in the worst case (no duplicates), the set will contain as many elements as the original list.

# Code
```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        return len(nums) != len(set(nums))

