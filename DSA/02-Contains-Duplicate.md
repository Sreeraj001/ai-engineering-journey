# Problem 
Given an integer array, return true if any value appears at least twice, otherwise return false

eg : [1,2,3,1] -> true  ,  [5,6,7,8] -> false

## Approach 1: Brute force

### Idea
loop through all the elements and check all the other elements to find duplicate , i can start from 0, j can statrt from i + 1 so that it avoids 
checking the same element and previous elements which are already checked

### Code - [Java]

```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        for(int i=0; i< nums.length; i++) {
            for(int j= i+1; j < nums.length; j++) {
                if( nums[i] == nums[j]) {
                    return true;
                }
            }
        }

        return false;
    }
}
```

Time Complexity: O(N^2) , in worst case it does n(n-1)/2 comparisons.
Space Complexity: O(1) as no additional space is used

## Approach 2: HashSet

### Idea

Add array elements to HashSet and if it already has the same one, the add method returns false

### Code - [Java]
```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
       Set<Integer> numSet = new HashSet<>();
       for(int num: nums) {
        if(!numSet.add(num)) {
            return true;
        }
       }

       return false;
    }
}
```
### Code - [Python]
```python
class Solution:
    def containsDuplicate(self, nums: List[int]) -> bool:
        sol_set = set()
        for num in nums:
            if num in sol_set:
                return True
            else:
                sol_set.add(num)
        return False
```
Time Complexity: O(n) , considering adding to HashSet is O(1)
Space complexity : O(n) , additional space is used


