# Intuition
Leverage the matrix's sorted properties to apply binary search, treating it like a 1D sorted array.

# Approach
Conduct binary search. Convert the 1D mid index to 2D using `mid // n` for row and `mid % n` for column (where `n` is the number of columns), allowing direct access to matrix 
elements. Adjust the search range based on the target comparison.

# Complexity
- Time complexity: $$O(\log(m * n))$$, due to binary search across the total number of elements.
- Space complexity: $$O(1)$$, as no extra space scaling with matrix size is used.

# Code
```python
class Solution:
    def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
        m, n = len(matrix), len(matrix[0])
        left, right = 0, m * n - 1

        while left <= right:
            mid = (left + right) // 2
            mid_value = matrix[mid // n][mid % n]  # Convert 1D index to 2D matrix coordinates

            if mid_value == target:
                return True
            elif mid_value < target:
                left = mid + 1
            else:
                right = mid - 1

        return False

