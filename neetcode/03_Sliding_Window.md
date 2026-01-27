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

## 2. [Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters) (Medium)

**Time Complexity: O(N)**

**Space Complexity: O(N)**

```cs
public class Solution {
    public int LengthOfLongestSubstring(string s) {

        int result = 0;

        // Track index of last duplicate character
        int indexOfLastDuplicate = 0;

        // To: Track duplicate characters
        // To: Maintain sliding window of non repeating characters
        var set = new HashSet<char>();

        for(int i=0; i<s.Length; i++){

            char ch = s[i];

            // If character is duplicate
            if(set.Contains(ch)){

                // Remove all visited characters from set
                // until the duplicate is removed
                while(set.Contains(ch)){
                    char charAtIndex = s[indexOfLastDuplicate];
                    set.Remove(charAtIndex);
                    indexOfLastDuplicate++;
                }
            }

            // Add current character to set
            set.Add(ch);

            // Check if current window size is largest
            result = Math.Max(result, set.Count);
        }
        return result;
    }
}

// Time Complexity: O(N)
// Space Complexity: O(N)
```
