# Intuition
To determine if a string is a palindrome, focus on alphanumeric characters, ignoring cases and non-alphanumeric characters.

# Approach
Use two pointers, starting at the ends of the string. Skip non-alphanumeric characters and compare the alphanumeric ones from each end. If at any point they don't match, it's not a 
palindrome.

# Complexity
- Time complexity: $$O(n)$$, as each character is checked at most once.
- Space complexity: $$O(1)$$, only two pointers used, independent of string length.

# Code
```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        l, r = 0, len(s) - 1
        while l < r:
            while l < r and not s[l].isalnum():
                l += 1
            while r > l and not s[r].isalnum():
                r -= 1
            if s[l].lower() != s[r].lower():
                return False
            l, r = l + 1, r - 1
        return True

