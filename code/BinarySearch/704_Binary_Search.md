# Intuition
Given a sorted array, the fastest way to find an element is through binary search, which repeatedly halves the search space.

# Approach
Use binary search: Start with pointers at both ends of the array. Repeatedly check the middle element. If it's the target, return its index. If it's greater, search the left half; 
if less, search the right half. Continue until the target is found or the pointers overlap.

# Complexity
- Time complexity: $$O(\log n)$$, as each step halves the array's search space.
- Space complexity: $$O(1)$$, as it only uses a few variables for indexing, irrespective of the array size.

# Code
```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        l, r = 0, len(nums) - 1

        while l <= r:
            mid = (l + r) // 2
            if nums[mid] == target:
                return mid
            elif nums[mid] < target:
                l = mid + 1
            else:
                r = mid - 1

        return -1

