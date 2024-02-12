# Intuition
On encountering the anagram problem, I realized that efficiently checking character counts is key. While sorting both strings is a straightforward method, it's not optimal for 
longer strings, prompting a focus on counting character frequencies.

# Approach
The solution employs two dictionaries to track character frequencies in each string. As we iterate through the strings, we update these counts. If the dictionaries match at the end, 
the strings are anagrams, having identical character frequencies.

# Complexity
- Time complexity:
This is O(n), with n being the string length, due to a single pass through each string.

- Space complexity:
It stands at O(1) or O(c), where c is the character set size, assuming a fixed set. Worst-case space usage is tied to the number of unique characters, not string length.

# Code
```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False
        
        countS, countT = {}, {}
        for i in range(len(s)):
            countS[s[i]] = 1 + countS.get(s[i], 0)
            countT[t[i]] = 1 + countT.get(t[i], 0)

        return countS == countT

