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

## 3. [3Sum](https://leetcode.com/problems/3sum/) (Medium)

Time Complexity: O(N^2)

Space Complexity: O(1)

```cs
public class Solution {
    public IList<IList<int>> ThreeSum(int[] nums) {

        var result = new List<IList<int>>();

        // Sort to skip duplicates & implement two-pointer approach
        Array.Sort(nums);

        for(int i=0; i<nums.Length; i++){

            // If num > 0, we can't achive sum = 0
            if(nums[i] > 0){
                break;
            }

            // Skip duplicates & find next number
            if(i > 0 && nums[i] == nums[i-1]){
                continue;
            }

            // Create two pointers
            int left = i+1;
            int right = nums.Length - 1;

            while(left < right){

                int sum = nums[i] + nums[left] + nums[right];

                // If triplet is found
                if(sum == 0){
                    var list = new List<int>([nums[i], nums[left], nums[right]]);
                    result.Add(list);

                    // Move the pointers to find next triplet (if any)
                    left++;
                    right--;

                    // Find next non duplicate number
                    while(left < right && nums[left] == nums[left-1]){
                        left++;
                    }

                }
                else if(sum < 0){
                    left++;
                }
                else if(sum > 0){
                    right--;
                }
            }

        }

        return result;

    }
}

// Time Complexity: O(N^2)
// Space Complexity: O(M) - Output array length
```
