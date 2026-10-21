## Problem
Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums[i].

The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.

You must write an algorithm that runs in O(n) time and without using the division operation.

Example 1:

Input: nums = [1,2,3,4]
Output: [24,12,8,6]

Example 2:

Input: nums = [-1,1,0,-3,3]
Output: [0,0,9,0,0]

### Idea

each item in the answer array is the product of product of elements in the left and product of elements in the right. in one parse calculate the product and elements in the left and in another parse multiply each items with their right products

### Complexity 
Time : O(n)
space: O(1)

### Code - Java

```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int[] answerList = new int[nums.length];
        int leftRightProduct = 1;
        for(int i=0;i<nums.length; i++) {
            answerList[i] = leftRightProduct;
            leftRightProduct = leftRightProduct*nums[i];
        }

        leftRightProduct = 1;

        for(int i=nums.length-1;i>=0; i--) {
            answerList[i] = answerList[i]*leftRightProduct;
            leftRightProduct = leftRightProduct*nums[i];
        }

        return answerList;
    }
}
```

### Python
```python
class Solution:
    def productExceptSelf(self, nums: list[int]) -> list[int]:
        prod_list = [1]*len(nums)
        left_right_product = 1
        for i in range(0, len(nums)):
            prod_list[i] = left_right_product
            left_right_product *= nums[i]

        left_right_product = 1

        for i in range(len(nums)-1, -1, -1):
            prod_list[i] *= left_right_product
            left_right_product *= nums[i]
        
        return prod_list
        
```
