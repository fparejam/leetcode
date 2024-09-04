# Intuition
To find the `k` most frequent elements in an array, a common approach is to count the occurrences of each element and then identify the elements with the highest counts.

## First approach
First, use a dictionary to count the occurrences of each number in the array. Then, sort the dictionary items by frequency and extract the `k` numbers with the highest frequency.

## Complexity
- Time complexity: $$O(N \log N)$$, where `N` is the number of unique elements. The most time-consuming operation is sorting the dictionary items.
- Space complexity: $$O(N)$$, as we store each unique number and its count in the dictionary.

## Code
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
```

----
# Improved Solution
## Intuition

The original solution is effective but can be optimized by avoiding the sorting step, which is O(Nlog⁡N)O(N \log N)O(NlogN). Instead, we can use a bucket sort-like approach to group 
numbers by their frequency, resulting in a linear time complexity.

## Approach

1.  **Count Occurrences:** Use a dictionary to count the occurrences of each number.
2.  **Bucket System:** Create a list of empty lists (buckets) where each index represents a frequency count.
3.  **Fill Buckets:** Place each number into the bucket corresponding to its frequency.
4.  **Extract Top `k` Elements:** Starting from the highest frequency bucket, collect numbers until we have the top `k` frequent elements.

## Complexity

-   **Time complexity:** O(N)O(N)O(N), where `N` is the number of elements in the array.
-   **Space complexity:** O(N)O(N)O(N), for storing the frequency dictionary and bucket system.

## Code

```python
class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        #First create the dict of the available numbers and its ocurrences
        dict_number_ocurrences = {}
        for number in nums:
            if number not in dict_number_ocurrences:
                dict_number_ocurrences[number] = 1
            else:
                dict_number_ocurrences[number] += 1

        #Create a bucket system:
        bucket_system = [[] for _ in range(len(nums) + 1)]

        #Fill in the bucket system
        for num, freq in dict_number_ocurrences.items():
            bucket_system[freq].append(num)
        
        #Get the k elements from the bucket
        top_k_frequent = []
        #Start on the end
        #Stop on 0 (no elements should be in bucket with 0 ocurrences)
        #Increment -1
        for i in range(len(bucket_system)-1, 0, -1):
            for number in bucket_system[i]:
                top_k_frequent.append(number)
                if len(top_k_frequent) == k:
                    return top_k_frequent
```

## Improvements

The improved solution reduces the time complexity to O(N) by using a bucket sort-like approach instead of sorting, making it more efficient, especially for large datasets. Another 
approach would be using heaps, but this solution feels more intuitive to me :) 

