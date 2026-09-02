# Problem

Given two strings s and t, return true if t is an of s, and false otherwise.

Example 1:

Input: s = "anagram", t = "nagaram"

Output: true

Example 2:

Input: s = "rat", t = "car"

Output: false

Constraints:

    1 <= s.length, t.length <= 5 * 104
    s and t consist of lowercase English letters.

## Approach 1 : Using Map

### Idea
Use a map to store the count of each letters and in second loop minus the count of letters and remove once the count becomes 0. check it the map is empty at the end

### Code [Java]
```java
class Solution {
    public boolean isAnagram(String s, String t) {

        if (s.length() != t.length()) {
            return false;
        }

        Map<Character, Integer> charMap = new HashMap<>();

        for (char c : s.toCharArray()) {
            charMap.put(c, charMap.getOrDefault(c, 0) + 1);
        }

        for (char c : t.toCharArray()) {
            Integer count = charMap.get(c);

            if (count == null) {
                return false;
            }

            if (count == 1) {
                charMap.remove(c);
            } else {
                charMap.put(c, count - 1);
            }
        }

        return charMap.isEmpty();
    }
}
```

Time complexity: O(n)
Space complexity: O(k) where k is the number of distinct characters
For normal English lowercase letters, k ≤ 26.

### Approach 2 : Using array

### Idea 
use of a fixed length array is possible since its all lowercase in the input. It reduces the space complexity

```java
class Solution {
    public boolean isAnagram(String s, String t) {
        int[] count = new int[26];
        if(t.length() != s.length()) {
             return false;
        }
        for(char c: s.toCharArray()) {
            count[ c - 'a']++;
        }

        for(char c: t.toCharArray()) {
            count[ c - 'a']--;
            if(count[c - 'a'] < 0) {
                return false;
            }
        }
        return true;
    }
}

```

Time complexity : O(n)
Space Complexity: O(1) as the array is always 26

### Code [Python]
```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        if len(s) != len(t):
            return False
        
        count = [0]*26

        for i in range(len(s)):
            count[ord(s[i]) - ord('a')] += 1
            count[ord(t[i]) - ord('a')] -= 1

        return all(x == 0 for x in count)
```

