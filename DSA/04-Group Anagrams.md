# Problem 
Given an array of strings strs, group the together. You can return the answer in any order.

Example 1:

Input: strs = ["eat","tea","tan","ate","nat","bat"]

Output: [["bat"],["nat","tan"],["ate","eat","tea"]]

Explanation:

    There is no string in strs that can be rearranged to form "bat".
    The strings "nat" and "tan" are anagrams as they can be rearranged to form each other.
    The strings "ate", "eat", and "tea" are anagrams as they can be rearranged to form each other.

## Approach 1 : Brute force

### Idea
Loop thought every combination of items in the list to check if they are anagrams. create a map of with key as first item which has not been grouped yet

for each string i
    if already grouped → skip

    create a group with strs[i]

    for every later string j
        if strs[i] and strs[j] are anagrams
            add strs[j] to group
            mark j as found

### Code - JAVA

```java
class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        List<List<String>> solList = new ArrayList<>();
       
       boolean[] foundIndex = new boolean[strs.length];

       for(int i=0;i< strs.length ; i++) {
        if(foundIndex[i]) {
            continue;
        }
        List<String> lst = new ArrayList<>();
        lst.add(strs[i]);
        for(int j= i+1 ; j< strs.length ; j++) {
            if(isAnagram(strs[i], strs[j])) {
                foundIndex[j] = true;
                lst.add(strs[j]);
            }
        }
        solList.add(lst);
       } 

       return solList;
    }

    private boolean isAnagram(String a, String b) {
        int[] arr = new int[26];
        if(a.length() != b.length()) {
            return false;
        }

        for(int i=0;i< a.length(); i ++) {
            char ca = a.charAt(i);
            char cb = b.charAt(i);

            arr[ca - 'a'] = arr[ca - 'a'] + 1;
            arr[cb - 'a'] = arr[cb - 'a'] - 1;
        }

        for(int i=0;i< arr.length; i ++) {
            if(arr[i] != 0) {
                return false;
            }
        }

        return true;
    }
}

```

***Time complexity:*** O(n^2*k)  - where k is length of string
n^2 for the double loops and k for anagram checking
***Space Complexity:*** O(n)
The O(n) space comes mainly from foundIndex and the result itself is normally not counted as auxiliary space.

## Approach 2 : HashMap
### Idea
instead of checking anagram or not, hash all the strings to an array of 26 with letter frequencies and use that as a key to the map. value of the map is list of all values with same hash key

for each string
    create frequency array
    convert frequency array → String key
    map[key].add(string)

### Code - JAVA

class Solution {
    public List<List<String>> groupAnagrams(String[] strs) {
        Map<String, List<String>> solMap = new HashMap<>();

        for (String str : strs) {
            int[] arr = new int[26];

            for (char c : str.toCharArray()) {
                arr[c - 'a']++;
            }

            String strKey = Arrays.toString(arr);

            solMap
                .computeIfAbsent(strKey, key -> new ArrayList<>())
                .add(str);
        }

        return new ArrayList<>(solMap.values());
    }
}

***Time Complexity:*** O(n*k) k -the length of string
***Space Complexity:*** O(1)

### Code Python
```python
class Solution:
    def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
        sol_map = {}
        for s in strs:
            arr = [0]*26
            for c in s:
                arr[ord(c) - ord('a')] += 1
            key = ','.join(map(str, arr))
            sol_map.setDefault(key, []).append(s)
            
        return list(sol_map.values())
```


  
    
