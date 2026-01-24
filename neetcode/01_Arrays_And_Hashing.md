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

## 4. [Group Anagrams](https://leetcode.com/problems/group-anagrams) (Medium)

**Time Complexity**: O(N \* M)

**Space Complexity**: O(N \* M)

N: Number Of strings

M: Length of each string

```cs
public class Solution {
    public IList<IList<string>> GroupAnagrams(string[] strs) {

        var result = new List<IList<string>>();

        // Create a map to store anagram groups
        var dictionary = new Dictionary<string, List<string>>();

        foreach(string s in strs){

            // Get char frequency array as a string (valid immutable key)
            string charArrayKey = GetCharArray(s);

            // Check if anagram exists in dictionary
            if(dictionary.ContainsKey(charArrayKey)){
                var existingList = dictionary[charArrayKey];
                existingList.Add(s);
                dictionary[charArrayKey] = existingList;
            }
            // Else insert into dictionary
            else{
                var list = new List<string>();
                list.Add(s);
                dictionary.Add(charArrayKey, list);
            }
        }

        // Store all anagram groups in the result
        foreach(var kvp in dictionary){
            result.Add(kvp.Value);
        }

        return result;

    }

    // Helper function to get char frequency array as a string
    public static string GetCharArray(string s){
        int[] charArray = new int[26];
        for(int i=0; i<s.Length; i++){
            int position = s[i] - 'a';
            charArray[position] += 1;
        }
        return String.Join('-', charArray);
    }
}
```

## 5. [Encode and Decode Strings](https://neetcode.io/problems/string-encode-and-decode) (Medium)

**Time Complexity**: O(M)

**Space Complexity**: O(M + N)

M: Sum of length of all strings

N: Number of strings

```cs
public class Solution {

    private const char uniqueIdentifier = '#';

    public string Encode(IList<string> strs) {
        var sb = new StringBuilder();
        foreach(string s in strs){
            sb.Append(s.Length);
            sb.Append(uniqueIdentifier);
            sb.Append(s);
        }
        return sb.ToString();
    }

    public List<string> Decode(string s) {

        var result = new List<string>();

        // First pointer
        // Store starting index of string length digit
        int i = 0;

        while(i < s.Length){

            // Second Pointer
            // Store the index of '#'
            int j = i;

            // Find index of '#'
            while(s[j] != uniqueIdentifier){
                j++;
            }

            // Get the string length digit
            int length = Convert.ToInt32(s.Substring(i, j-i));

            // Move first pointer after '#'
            // String decoding will start from here
            i = j + 1;

            // Get the decoded string
            string decoded = s.Substring(i, length);

            result.Add(decoded);

            // Move the first pointer to process next string
            i = i + length;

        }

        return result;
   }
}

```

## 6. [Product of Array Except Self](https://leetcode.com/problems/product-of-array-except-self) (Medium)

**Time Complexity**: O(N)

**Space Complexity**: O(1)

```cs
public class Solution {
    public int[] ProductExceptSelf(int[] nums) {

        var result = new int[nums.Length];

        int product = 1;

        // Start from right to left
        // For each num, get product of all numbers towards it's right
        for(int i=nums.Length-1; i>=0; i--){
            result[i] = product;
            product *= nums[i];
        }

        // reset the product
        product = 1;

        // Start from left to right
        // For each number, get product of all numbers toward it's left
        for(int i=0; i<nums.Length; i++){

            // Optimization: Do the product with right array directly
            result[i] *= product;
            product *= nums[i];
        }

        return result;

    }
}
```

## 7. [Valid Sudoku](https://leetcode.com/problems/valid-sudoku) (Medium)

**Time Complexity**: O(N^2)

**Space Complexity**: O(N^2)

```cs
public class Solution {
    public bool IsValidSudoku(char[][] board) {

        // Create maps to keep track of duplicate digits
        // in each row, column & sub-box
        var rowMap = new Dictionary<int, HashSet<char>>();
        var colMap = new Dictionary<int, HashSet<char>>();
        var subBoxMap = new Dictionary<int, HashSet<char>>();

        // Fill the maps
        for(int i=0; i<9; i++){
            rowMap.TryAdd(i, new HashSet<char>());
            colMap.TryAdd(i, new HashSet<char>());
            subBoxMap.TryAdd(i, new HashSet<char>());
        }

        // Start visiting the digits
        for(int i=0;i<9;i++){
            for(int j=0;j<9;j++){

                // Ignore void cells
                if(board[i][j] == '.'){
                    continue;
                }

                int row = i;
                int col = j;
                int subBox = (i/3) * 3 + (j/3); // Calculate sub-box index
                char ch = board[row][col];

                // Check if digit is a duplicate in row
                if(rowMap[row].Contains(ch)){
                    return false;
                }
                else{
                    rowMap[row].Add(ch);
                }

                // Check if digit is a duplicate in column
                if(colMap[col].Contains(ch)){
                    return false;
                }
                else{
                    colMap[col].Add(ch);
                }

                // Check if digit is a duplicate in sub-box
                if(subBoxMap[subBox].Contains(ch)){
                    return false;
                }
                else{
                    subBoxMap[subBox].Add(ch);
                }
            }
        }

        return true;
    }
}
```

## 8. [Longest Consecutive Sequence](https://leetcode.com/problems/longest-consecutive-sequence) (Medium)

**Time Complexity**: O(N)

**Space Complexity**: O(N)

```cs
public class Solution {
    public int LongestConsecutive(int[] nums) {

        int result = 0;

        // Create a set using nums to remove duplicates
        var set = new HashSet<int>(nums);

        // Start iterating the set
        foreach(int i in set){

            // If number is part of existing sequence
            // Then we can skip it
            if(set.Contains(i-1)){
                continue;
            }

            int longest = 1;
            int num = i;

            // Keep checking if next number is available
            while(set.Contains(num+1)){
                longest++;
                num++;
            }

            // Check if this count is the longest
            result = Math.Max(result, longest);
        }

        return result;

    }
}
```
