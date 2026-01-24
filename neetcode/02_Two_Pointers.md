## 1. [Valid Palindrome](https://leetcode.com/problems/valid-palindrome) (Easy)

Time Complexity: O(N)

Space Complexity: O(N)

```cs
public class Solution {
    public bool IsPalindrome(string s) {

        // Create two pointers
        int left = 0;
        int right = s.Length - 1;

        // Start comparing characters at these pointers
        while(left < right){

            // Find the alpha-numeric char from left
            while(left < right && !Char.IsLetterOrDigit(s[left])){
                left++;
            }

            // Find the alpha-numeric char from right
            while(left < right && !Char.IsLetterOrDigit(s[right])){
                right--;
            }

            // Check if both chars are equal
            if(Char.ToLower(s[left]) != Char.ToLower(s[right])){
                return false;
            }

            // Move the pointers to next chars
            left++;
            right--;
        }
        return true;
    }
}
```
