## Problem 
Given an integer array nums, find the subarray with the largest sum, and return its sum.

Example 1:

Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: The subarray [4,-1,2,1] has the largest sum 6.

Example 2:

Input: nums = [1]
Output: 1
Explanation: The subarray [1] has the largest sum 1.

Example 3:

Input: nums = [5,4,-1,7,8]
Output: 23
Explanation: The subarray [5,4,-1,7,8] has the largest sum 23.

### Idea
let maxsum = 0 and currentsum = 0
for every i in [ 0 to length of array]
if currentsum + array[i] less than array[i]
currentsum = maxsum,
otherwise currentsum = currentsum + array[i]
if maxsum < currentsum 
maxsum = currentsum

### Complexity
Time : O(n)
Space: O(1)

### Code -Java

```java
class Solution {
    public int maxSubArray(int[] nums) {
        int currentSum = nums[0];
        int maxSum = nums[0]; 
        for(int i=1;i<nums.length;i++) {
            if(nums[i] > currentSum + nums[i]) {
                currentSum = nums[i];
            } else {
                currentSum =  currentSum + nums[i];
            }
            if(currentSum > maxSum) {
                maxSum = currentSum;
            }
        }

        return maxSum;
    }
}
```

### Code - python
```python
class Solution:
    def maxSubArray(self, nums: list[int]) -> int:
        maxSum = nums[0]
        currentSum = nums[0]
        for i in range(1, len(nums)):
            if nums[i] > currentSum + nums[i]:
                currentSum = nums[i]
            else:
                currentSum = currentSum + nums[i]
            if currentSum > maxSum:
                maxSum = currentSum
        
        return maxSum
```


