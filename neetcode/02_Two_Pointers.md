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

## 2. [Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/) (Medium)

_Time Complexity_: O(N)

_Space Complexity_: O(1)

```cs
public class Solution {
    public int[] TwoSum(int[] numbers, int target) {
        var result = new int[2];

        // Create two pointers
        int left = 0;
        int right = numbers.Length - 1;

        while(left < right){

            // Get sum of elements at our two pointers
            int sum = numbers[left] + numbers[right];

            // If sum = target, return
            if(sum == target){
                return [left+1, right+1];
            }
            // If sum < target, move left pointer
            else if(sum < target){
                left++;
            }
            // If sum > target, move right pointer
            else if(sum > target){
                right--;
            }
        }
        return result;
    }
}

```
