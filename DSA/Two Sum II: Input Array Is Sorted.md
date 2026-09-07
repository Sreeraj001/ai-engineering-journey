# Problem
Given:
numbers = [2, 7, 11, 15]
target = 9

Return: [1, 2]

because:
2 + 7 = 9

The important difference from the original Two Sum is that the array is already sorted.

## Approach : Two pointers
start -> from left
end -> from right
continue till start > end
  if sum of array[start] + array[end] greater than target
    decrement end by 1
  if sum is less than target 
    increment left by 1
  if sum is equal to the target 
    return start+1, end+1

complexity:
  time : O(n)
  space : O(1)

### Code - Java
```java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int start = 0;
        int end = numbers.length -1;
        int[] solArr = new int[2];
        while(start < end) {
	    int sum = numbers[start] + numbers[end];
            if(sum > target) {
                end--;
            } else if (sum < target) {
                start++;
            } else {
                solArr[0] = start +1;
                solArr[1] = end +1;
                return solArr;
            }
        }

        return solArr;
    }
}
```
### Code - Python
```python
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        start = 0
        end = len(numbers) -1

        while start < end:
            total = numbers[start] + numbers[end]
            if total > target:
                end -= 1
            elif total < target:
                start += 1
            else:
                return [start+1, end+1]
```
