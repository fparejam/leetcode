# Intuition
Anagrams are words formed by rearranging the letters of another word. By sorting the characters in each word, we can easily identify words that are anagrams of each other as they 
will have the same sorted character sequence.

# Approach
Create a dictionary to group words. For each word in the list, sort its characters and use this sorted tuple as a key in the dictionary. This way, all anagrams will share the same 
key. Append each word to the corresponding list in the dictionary. Finally, return the dictionary values, which represent groups of anagrams.

# Complexity
- Time complexity: $$O(nk \log k)$$, where `n` is the number of strings and `k` is the maximum length of a string. Each string is sorted individually.
- Space complexity: $$O(nk)$$, as we store all strings in the dictionary.

# Code
```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        anagrams = {}
        for s in strs:
            key = tuple(sorted(s))
            if key not in anagrams:
                anagrams[key] = []
            anagrams[key].append(s)
        return list(anagrams.values())

