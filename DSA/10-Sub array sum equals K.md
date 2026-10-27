## Problem
Given an array of integers nums and an integer k, return the total number of subarrays whose sum equals to k.

A subarray is a contiguous non-empty sequence of elements within an array.

 

Example 1:

Input: nums = [1,1,1], k = 2
Output: 2

Example 2:

Input: nums = [1,2,3], k = 3
Output: 2

## Idea 1
### Brute force
check if sum is equal to k in double loop and count sub array

#### Complexity
Time : O(n<sup>2</sup>)
Space: 1

#### Code - Java
```java
class Solution {
    public int subarraySum(int[] nums, int k) {
       int count = 0;
       for(int i=0; i<nums.length; i++) {
        int sum = 0;
        for(int j = i; j< nums.length; j++) {
            sum += nums[j];
            if(sum == k) {
                count++;
            }
        }
    }

       return count;
    }
}
```

## Idea 2
for every i<sup>th</sup> item in the array
check if sum<sub>i<sub> - sum<sub>j</sub> = k
a map can be used to record sum at every element
#### Complexity
Time : O(n)
Space: O(n)
#### Code - Java
```java
class Solution {
    public int subarraySum(int[] nums, int k) {
        Map<Integer, Integer> diffMap =new HashMap<>();
        diffMap.put(0, 1);
        int sum = 0;
        int count = 0;
        for(int num: nums) {
            sum += num;
            Integer diffCount = diffMap.get(sum - k);
            if(diffCount != null){
              count += diffMap.get(sum - k);
            } 
            diffMap.put(sum, diffMap.getOrDefault(sum, 0)+1); 
        }

        return count; 
    }
}
```
#### Code - Python
```python
class Solution:
    def subarraySum(self, nums: List[int], k: int) -> int:
        diff_dict = {}
        sum  = 0
        diff_dict[0] = 1
        count = 0
        for num in nums:
            sum += num
            count += diff_dict.get(sum - k, 0)
            diff_dict[sum] = diff_dict.get(sum, 0) + 1
        
        return count
        
```


