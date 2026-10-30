## Problem
Given an integer array nums, find a subarray that has the largest product, and return the product.

The test cases are generated so that the answer will fit in a 32-bit integer.

Note that the product of an array with a single element is the value of that element.

Example 1:

Input: nums = [2,3,-2,4]
Output: 6
Explanation: [2,3] has the largest product 6.

Example 2:

Input: nums = [-2,0,-1]
Output: 0
Explanation: The result cannot be 2, because [-2,-1] is not a subarray.

 

Constraints:

    1 <= nums.length <= 2 * 104
    -10 <= nums[i] <= 10
    The product of any subarray of nums is guaranteed to fit in a 32-bit integer.

### Idea
let min = max = result = number[0]
for each number k<sub>i</sub> in k<sub>1</sub> - k<sub>n</sub
new_min = minimum of k<sub>i</sub> * min,  k<sub>i</sub> * max, 
new_min = maximum of k<sub>i</sub> * min,  k<sub>i</sub> * max,
result = maximum of new_max, k<sub>1</sub>

#### Complexity
Time : O(n)
Space : O(1)

### Code Java
```java
class Solution {
    public int maxProduct(int[] nums) {
        int result=nums[0], min=nums[0], max = nums[0];
        for(int i=1; i < nums.length; i++ ) {
           int prodMin = min*nums[i];
           int prodMax = max*nums[i];
           min = Math.min(Math.min(nums[i], prodMin), prodMax);
           max = Math.max(Math.max(nums[i], prodMin), prodMax);
           result = Math.max(result, max);

        }
        return result;
    }
}
```

### Code Python
```python
class Solution:
    def maxProduct(self, nums: list[int]) -> int:
        mini = nums[0]
        maxi=nums[0]
        result =nums[0]
        for i in range(1,len(nums)):
            minProd = mini*nums[i]
            maxProd = maxi*nums[i]
            mini = min(minProd, maxProd, nums[i])
            maxi = max(maxProd, minProd , nums[i])
            result = max(maxi, result, mini)
        return result

        
```


