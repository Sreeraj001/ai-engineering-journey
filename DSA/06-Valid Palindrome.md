# Problem 
Given:
***"A man, a plan, a canal: Panama"***
Return: true
because after removing non-alphanumeric characters and ignoring case:
***amanaplanacanalpanama*** is a palindrome.

## Approach : Two pointers
## Idea
start -> from left
end -> from right
continue till string[start] is alphanumeric
continue till string [end] is alphanumeric
compare string[start] not equal string[last] -> false 

continue inward

complexity:
  Time: O(n)
  Space: O(1)

### Code - JAVA
```java
class Solution {
    public boolean isPalindrome(String s) {
        int start = 0;
        int end = s.length()  - 1;
        while(start < end) {
            while( (start < end)  && !Character.isLetterOrDigit(s.charAt(start))) {
                start++;
            }
            while( (start < end) && !Character.isLetterOrDigit(s.charAt(end))) {
                end--;
            }

            if(Character.toLowerCase(s.charAt(start)) != Character.toLowerCase(s.charAt(end))) {
                return false;
            }

            start++;
            end--;
        }

        return true;
    }
}
```

### Code - Python
```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        start = 0
        end = len(s) - 1

        while start < end:
            while start < end and not s[start].isalnum():
                start += 1

            while start < end and not s[end].isalnum():
                end -= 1

            if s[start].lower() != s[end].lower():
                return False

            start += 1
            end -= 1
        
        return True
```

