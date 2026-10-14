## Problem
Longest Substring Without Repeating Characters

Given a string s, find the length of the longest substring without duplicate characters.

Example 1:

Input: s = "abcabcbb"
Output: 3
Explanation: The answer is "abc", with the length of 3. Note that "bca" and "cab" are also correct answers.

Example 2:

Input: s = "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.


### Idea

initialize left and maxlength to 0
for i in length of string
if s[i] is found in the map and s[i] greater than left
maxlength = max(maxlength, i - left)
update left to s[i] + 1
add s[i]. i to map

### Complexity

Time = O(n)
Space = O(min(n, charset)), effectively O(n) in the general case

### Code - Java
```java

class Solution {
    public int lengthOfLongestSubstring(String s) {
        Map<Character, Integer> charMap = new HashMap<>();
        int left = 0;
        int maxLen = 0;
        for(int i=0; i < s.length() ; i++) {
            Integer pos = charMap.get(s.charAt(i));
            if(pos != null && pos >= left) {
                 if(maxLen < (i - left)) {
                    maxLen = i - left;
                }
               
                left = pos + 1;  
            } 
            charMap.put(s.charAt(i), i);

        }

        return Math.max(maxLen, s.length() - left);

    }
}
```

### python
```python
class Solution:
    def lengthOfLongestSubstring(self, s: str) -> int:
        charDict = {}
        maxLen = 0
        left  = 0
        for i in range(len(s)):
            pos = charDict.get(s[i])
            if pos is not None and pos >= left:
                left = pos + 1
            maxLen = max(maxLen, i - left + 1)
            charDict[s[i]] = i
        return maxLen

```
