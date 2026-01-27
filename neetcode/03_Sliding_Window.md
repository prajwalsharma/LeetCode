## 1. [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock) (Easy)

**Time Complexity: O(N)**

**Space Complexity: O(1)**

```cs
public class Solution {
    public int MaxProfit(int[] prices) {

        int result = 0;

        // Find largest number on right for each number
        int largestNumberOnRight = 0;

        for(int i=prices.Length-1; i>=0; i--){

            // Calculate profit: handle negatives
            int profit = Math.Max(largestNumberOnRight - prices[i], 0);

            // Check if it is max profit
            result = Math.Max(result, profit);

            // Check if current number is larger
            largestNumberOnRight = Math.Max(largestNumberOnRight, prices[i]);
        }
        return result;
    }
}

// Time Complexity: O(N)
// Space Complexity: O(1)
```
