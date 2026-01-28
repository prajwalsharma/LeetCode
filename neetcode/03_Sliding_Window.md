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

## 3. [Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement) (Medium)

**Space Complexity: O(N)**

**Time Complexity: O(1)**

```cs
public class Solution {
    public int CharacterReplacement(string s, int k) {

        int result = 0;

        // Track frequency of each char
        var map = new Dictionary<char,int>();

        // Start point of our window
        int left = 0;

        // Freq of char with max frequency so far
        int max = 0;

        for(int right=0; right<s.Length; right++){

            char ch = s[right];

            // Add/Update frequency of current char
            if(map.ContainsKey(ch)){
                map[ch] += 1;
            }
            else{
                map.Add(ch, 1);
            }

            // Check if current char is the one with max frequency
            max = Math.Max(max, map[ch]);

            // Get the length of our current window
            int currentWindowLength = right - left + 1;

            // Get the number of characters with low frequency
            int charToReplace = currentWindowLength - max;

            // Check if all those characters can be replaced in under K times
            if(charToReplace <= k){

                // This window is a potential solution
                result = Math.Max(result, currentWindowLength);
            }
            // This window is not a potential solution
            else{
                // Remove the starting character from current window
                char toRemove = s[left];
                map[toRemove] -= 1;

                // Shift the window
                left++;
            }
        }
        return result;

    }
}

// Time Complexity: O(N)
// Space Complexity: O(1)
```
