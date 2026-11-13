## Problem 
Given n non-negative integers representing an elevation map where the width of each bar is 1, compute how much water it can trap after raining.

Example 1:

Input: height = [0,1,0,2,1,0,1,3,2,1,2,1]
Output: 6
Explanation: The above elevation map (black section) is represented by array [0,1,0,2,1,0,1,3,2,1,2,1]. In this case, 6 units of rain water (blue section) are being trapped.

Example 2:

Input: height = [4,2,0,3,2,5]
Output: 9

 

Constraints:

    n == height.length
    1 <= n <= 2 * 104
    0 <= height[i] <= 105


## Idea 1 : Bruteforce 
use double loop to find left max(including current item)  and right max(including current item) and calculate water trapped in each step

### Complexity 
Time : O(n<sup>2</sup>)  
Space : O(1)

### Code - Java
```java
class Solution {
    public int trap(int[] height) {
        int area = 0;
       for(int i=0;i<height.length;i++) {
        int leftMax = 0;
        int rightMax = 0;
        for(int j=i; j>=0; j--) {
            if(leftMax < height[j]) {
                leftMax = height[j];
            }
        }
        for(int j=i;j<height.length;j++) {
            if(height[j]>rightMax) {
                rightMax = height[j];
            }
        }
        area += (leftMax>rightMax?rightMax:leftMax) - height[i];
       }
       return area;
    }
}
```

## Idea 2: Using an array to capture left max

Use an array to capture left maxes in one loop from left to right, in another loop calculate water level from right to left

### Complexity:
Time : O(n)  
Space: O(n)

### Code - Java
```java
class Solution {
    public int trap(int[] height) {
        int waterVolume = 0;
        int max = 0;
        int[] leftMax = new int[height.length]; 
        for(int i=0;i<height.length;i++) {
            if(height[i]>max) {
                max = height[i];
            }
            leftMax[i] = max;
        }
        max = 0;
        for(int i=height.length-1;i>=0;i--) {
            if(height[i]>max) {
                max = height[i];
            }
            waterVolume += (max < leftMax[i]?max:leftMax[i]) - height[i];
        }
        return waterVolume;
    }
}
```

## Idea 2: Two pointers 
use left and right pointers to calculate left max and right max

### Complexity
Time : O(n)  
Space: O(1)

### Code -Java
```java
class Solution {
    public int trap(int[] height) {
        int waterVolume = 0;
        int left = 0;
        int right = height.length-1;
        int leftMax = 0;
        int rightMax = 0;
        while(right>left) {
            leftMax = height[left] > leftMax? height[left]: leftMax;
            rightMax = height[right] > rightMax? height[right]: rightMax;
            if(height[left] < height[right]) {
                waterVolume += leftMax - height[left];
                left++;
            } else {
                waterVolume += rightMax - height[right];
                right--;
            }
        }
        return waterVolume;
    }
}

```
### Code - Python
```python
class Solution:
    def trap(self, height: list[int]) -> int:
        if len(height) < 3:
            return 0
        water_volume = 0
        left = 0
        right = len(height) -1
        left_max = height[left]
        right_max =  height[right]
        while right > left:
            if height[left] < height[right]:
                water_volume += left_max - height[left]
                left += 1
                left_max = height[left] if height[left] > left_max else left_max
            else:
                water_volume += right_max - height[right]
                right -= 1
                right_max = height[right] if height[right] > right_max else right_max
        return water_volume
```
