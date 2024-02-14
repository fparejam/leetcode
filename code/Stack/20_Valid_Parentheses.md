# Intuition
To determine if a string of brackets is valid, each closing bracket must match the last unmatched opening bracket.

# Approach
Use a stack to track opening brackets. For each character in the string, if it's an opening bracket, push it to the stack. If it's a closing bracket, check against the top of the 
stack. The string is valid if all brackets are matched correctly and the stack is empty at the end.

# Complexity
- Time complexity: $$O(n)$$, where `n` is the length of the string, as we traverse it once.
- Space complexity: $$O(n)$$ in the worst case (all opening brackets), as we use a stack to store them.

# Code
```python
class Solution:
    def isValid(self, s: str) -> bool:
        closingToOpenDict = {")": "(", "]": "[", "}": "{"}
        stack = []

        for c in s:
            if c not in closingToOpenDict:
                stack.append(c)
                continue
            if not stack or stack[-1] != closingToOpenDict[c]:
                return False
            stack.pop()

        return not stack

