# Intuition
When faced with the two sum problem, my initial thought was to find an efficient way to track the indices of the numbers that sum up to the target. A brute force approach would 
involve checking each pair of numbers, but that would be inefficient. To optimize, I considered using a hash map to store and quickly access the indices of previous numbers.

# Approach
The approach involves using a hash map (`dictValueIndex`) to store each number's index as we iterate through the list. For each number, we check if the complement (target - current 
number) exists in the hash map. If it does, we have found the two numbers that sum up to the target, and we return their indices. If not, we add the current number and its index to 
the hash map. This way, we only need to pass through the list once.

# Complexity
- Time complexity:
The time complexity is O(n), where n is the number of elements in the list. This is because we traverse the list only once, and hash map operations (insertion and lookup) are O(1) 
on average.

- Space complexity:
The space complexity is also O(n), as in the worst case, we might need to store each element of the list in the hash map (when there is no valid pair until the last element).

# Code
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        if len(nums) == 2:
            return [0, 1]

        dictValueIndex = {}
        
        for index, num in enumerate(nums):
            if (target - num) in dictValueIndex:
                return [index, dictValueIndex[target - num]]
            dictValueIndex[num] = index

