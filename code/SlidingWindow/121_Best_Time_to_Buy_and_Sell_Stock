# Intuition
To maximize profit in stock trading, buy low and sell high. Identify the lowest buying price and calculate the highest profit possible from that point.

# Approach
Iterate through the stock prices. Track the lowest price seen so far and compute the profit if selling at the current price. Update the maximum profit whenever a higher profit is 
found.

# Complexity
- Time complexity: $$O(n)$$, as we traverse the list of prices once.
- Space complexity: $$O(1)$$, as only a constant amount of extra space is used.

# Code
```python
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        res = 0    
        lowest = prices[0]
        for price in prices:
            if price < lowest:
                lowest = price
            res = max(res, price - lowest)
        return res

