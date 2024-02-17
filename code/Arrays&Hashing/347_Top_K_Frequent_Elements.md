# Intuition
To find the `k` most frequent elements in an array, a common approach is to count the occurrences of each element and then identify the elements with the highest counts.

# Approach
First, use a dictionary to count the occurrences of each number in the array. Then, sort the dictionary items by frequency and extract the `k` numbers with the highest frequency. 
This approach ensures we identify the most frequent elements efficiently.

# Complexity
- Time complexity: $$O(N \log N)$$, where `N` is the number of unique elements. The most time-consuming operation is sorting the dictionary items.
- Space complexity: $$O(N)$$, as we store each unique number and its count in the dictionary.

# Code
```python
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        dict_nums_occurrences = {}
        for num in nums:
            if num not in dict_nums_occurrences:
                dict_nums_occurrences[num] = 1
            else:
                dict_nums_occurrences[num] += 1
        sorted_occurrences = sorted(dict_nums_occurrences.items(), key=lambda x: x[1])        
        top_k_frequent = [item[0] for item in sorted_occurrences[-k:]]

        return top_k_frequent

