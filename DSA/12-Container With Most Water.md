## Problem
You are given an integer array height of length n. There are n vertical lines drawn such that the two endpoints of the ith line are (i, 0) and (i, height[i]).

Find two lines that together with the x-axis form a container, such that the container contains the most water.

Return the maximum amount of water a container can store.

Notice that you may not slant the container.

example 1  
Input: height = [1,8,6,2,5,4,8,3,7]
Output: 49
Explanation: The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.

Example 2:  

Input: height = [1,1]
Output: 1

## Idea 1. Bruteforce
checking all possible pairs in a double loop

### Complexity
Time : O(n<sup>2</sup>)  
Space: O(1)

### Code - Java
```java
class Solution {
    public int maxArea(int[] height) {
        int maxArea = 0;
        for(int i=0; i<height.length; i++) {
            for(int j=i+1; j<height.length; j++) {
                int area = (j-i)*(height[i]<height[j]?height[i]:height[j]);
                if(area > maxArea) {
                    maxArea = area;
                }
            } 
        }
        return maxArea;
    }
}
```

## Idea 2. Pointers
initialize left and right points with left = 0 and right = last elements position  
calculate area and update max area  
advance the pointer with least height  

### Complexity 
Time : O(n)
Space: O(1)

### Code -Java
```java
class Solution {
    public int maxArea(int[] height) {
        int left = 0, right = height.length-1;
        int maxArea = 0;
        while(left != right) {
            int area = (right - left)*(height[left]<height[right]?height[left]: height[right]);
            if(area > maxArea) {
                maxArea = area;
            }
            if(height[right]>height[left]) {
                left++;
            } else {
                right--;
            }
        }
        return maxArea;
    }
}
```

### Code -Python
```python
class Solution:
    def maxArea(self, height: list[int]) -> int:
        max_area = 0
        left = 0
        right = len(height) -1
        while right>left:
            area = (right -left)*(height[left] if height[left] < height[right] else height[right])
            if area > max_area:
                max_area = area
            if height[left]> height[right]:
                right -= 1
            else:
                left +=1
        return max_area

```

