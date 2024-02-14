# Intuition
Given an array representing heights of lines, the goal is to find two lines that form the container holding the most water. The key is to maximize the area, which depends on the 
distance between lines and the height of the shorter line.

# Approach
Use a two-pointer approach, starting at the extremes of the array. Calculate the area formed between the lines at the pointers, and update the maximum area found. Move the pointer 
at the shorter line inward, as this might lead to a larger area.

# Complexity
- Time complexity: $$O(n)$$, as we traverse the array only once.
- Space complexity: $$O(1)$$, as only constant extra space is used.

# Code
```python
class Solution:
    def maxArea(self, height: List[int]) -> int:
        max_water = 0
        left, right = 0, len(height) - 1

        while left < right:
            width = right - left
            current_water = min(height[left], height[right]) * width
            max_water = max(max_water, current_water)

            if height[left] < height[right]:
                left += 1
            else:
                right -= 1

        return max_water

