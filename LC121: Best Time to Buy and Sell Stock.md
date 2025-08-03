## Leetcode 121: Best Time to Buy and Sell Stock

### Concept
You are given an array where the `i`-th element represents the price of a stock on day `i`. You need to find the maximum profit that can be obtained by buying on one day and selling on another. You cannot sell before you buy.

### Key Idea
- The goal is to **buy low and sell high**. 
- Traverse through the array and track the **minimum price** seen so far. For each price, calculate the **potential profit** if you were to sell at that price, using the **min price** from previous days.
- Keep track of the **maximum profit** encountered during the traversal.
  
```
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        min_price = float('inf')
        max_profit = 0
        
        for price in prices:
            # Update the min price
            min_price = min(min_price, price)
            # Calculate the profit if selling at the current price
            profit = price - min_price
            # Update the max profit
            max_profit = max(max_profit, profit)
        
        return max_profit
```

### Approach
1. **Initialization**: Set a variable to track the minimum price (`min_price`) and a variable to track the maximum profit (`max_profit`).
2. **Iterate through the prices**:
   - For each price, calculate the **profit** by subtracting the `min_price` from the current price.
   - Update the `min_price` to the minimum of the current `min_price` and the current price.
   - Update the `max_profit` to be the maximum of the current `max_profit` and the calculated profit.
3. **Return the `max_profit`** after the loop ends.

### Edge Case Handling
- **Prices are always decreasing**: Return `0` (no profit can be made).
- **Array with less than two prices**: Return `0` (you can't buy and sell in less than two days).

### Common Examples
- **Example 1**:
  - Input: `prices = [7, 1, 5, 3, 6, 4]`
  - Output: `5`
  - Explanation: Buy at price 1 and sell at price 6, the maximum profit is 6 - 1 = 5.
  
- **Example 2**:
  - Input: `prices = [7, 6, 4, 3, 1]`
  - Output: `0`
  - Explanation: No profit can be made as prices are always decreasing.

### Time & Space Complexity
- **Time**: O(n), where `n` is the length of the array. We only make one pass through the array.
- **Space**: O(1), constant space as we only use a few variables to track the minimum price and maximum profit.

### Why This Solution Is Preferred in Interviews
- **Optimal Solution**: A single pass through the array gives an O(n) time complexity.
- **Simple and Intuitive**: The solution is easy to explain and implement.
- **Edge Case Handling**: Covers edge cases like decreasing prices and short arrays efficiently.

### Tags
- **Array**
- **Greedy**
- **Dynamic Programming**
