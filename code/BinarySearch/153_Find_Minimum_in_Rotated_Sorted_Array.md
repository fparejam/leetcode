# Intuition
For a rotated sorted array, the minimum element can be found where the order "breaks". This suggests using binary search to efficiently locate this point.

# Approach
Perform a modified binary search. Check if the current segment is sorted: if so, update the result with the lower bound. Otherwise, continue the search in the unsorted segment, 
updating the result with the middle element each time.

# Complexity
- Time complexity: $$O(\log n)$$, as it uses binary search to halve the search space each iteration.
- Space complexity: $$O(1)$$, only a constant amount of extra space is used.

# Code
```python
class Solution:
    def findMin(self, nums: List[int]) -> int:
        res = nums[0]
        l, r = 0, len(nums) - 1
        while l <= r:
            if nums[l] < nums[r]:
                res = min(res, nums[l])
                break
            m = (l + r) // 2
            res = min(res, nums[m])
            if nums[m] >= nums[l]:
                l = m+1
            else:
                r = m-1
        return res

