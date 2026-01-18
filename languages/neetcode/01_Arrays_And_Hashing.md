## 1. Contains Duplicate (Easy)

[LeetCode URL](https://neetcode.io/problems/duplicate-integer/question?list=neetcode150)

```cs
public class Solution {
    public bool ContainsDuplicate(int[] nums) {

        // Create a set
        var set = new HashSet<int>();

        // Iterate each item and add to set
        foreach(int num in nums){

            // If an item already exists in set
            // that is a duplicate
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
