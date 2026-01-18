## 1. [Contains Duplicate](https://neetcode.io/problems/duplicate-integer/question?list=neetcode150) (Easy)

**Time Complexity**: O(N)

**Space Complexity**: O(N)

```cs
public class Solution {
    public bool ContainsDuplicate(int[] nums) {

        // Create a set
        var set = new HashSet<int>();

        // Iterate each item and add to set
        foreach(int num in nums){

            // If an item already exists in set, that is a duplicate
            if(set.Contains(num)){
                return true;
            }
            else{
                set.Add(num);
            }
        }

        return false;
    }
}
```

```cs
public class Solution {
    public bool ContainsDuplicate(int[] nums) {

        // Create a set using input array
        var set = new HashSet<int>(nums);

        // Check if count is equal
        return set.Count == nums.Length ? false : true;
    }
}
```

## 2. [Valid Anagram](https://leetcode.com/problems/valid-anagram) (Easy)

**Time Complexity**: O(N + M)

**Space Complexity**: O(1)

```cs
public class Solution {
    public bool IsAnagram(string s, string t) {

        // Base Case: Strings are not equal
        if(s.Length != t.Length){
            return false;
        }

        // Create an array to store count of each character
        var charCountArray = new int[26];

        for(int i=0; i<s.Length; i++){

            int sourceCharIndex = s[i] - 'a';
            int targetCharIndex = t[i] - 'a';

            // Increment count of char
            charCountArray[sourceCharIndex] += 1;

            // Decrement count of char
            charCountArray[targetCharIndex] -= 1;
        }

        // If all characters are equal, then this array will have all 0s
        foreach(int i in charCountArray){
            if(i != 0){
                return false;
            }
        }

        return true;
    }
}
```

## 3. [Two Sum](https://leetcode.com/problems/two-sum) (Easy)

**Time Complexity**: O(N)

**Space Complexity**: O(N)

```cs
public class Solution {
    public int[] TwoSum(int[] nums, int target) {

        var result = new int[2];

        // Store visited number with it's index
        var map = new Dictionary<int, int>();

        for(int i=0; i<nums.Length; i++){

            int currentNumber = nums[i];
            int otherNumber = target - currentNumber;

            // Check if other number already exists
            if(map.ContainsKey(otherNumber)){
                return [i, map[otherNumber]];
            }
            else{
                map.TryAdd(currentNumber, i);
            }
        }
        return result;
    }
}
```
