# Two Sum

## Problem

Given an integer array `nums` and an integer `target`, return the
indices of the two numbers such that they add up to `target`.

Assumptions:
- There is exactly one valid solution.
- The same element cannot be used twice.

---


# Approach 1: Brute Force

## Idea

Try every possible pair of elements.

For each `i`, compare `nums[i]` with every element after it.

## Code
```java
  class Solution {
    public int[] twoSum(int[] nums, int target) {

        int[] sols = new int[2];
        for(int i = 0; i < nums.length; i++) {
            for(int j=i+1; j< nums.length ; j++) {
                if(nums[i]+nums[j] == target) {
                    sols[0] = i;
                    sols[1] = j;
                    break;
                }
            }
        }

        return sols;
    }
}
```
  1.  Time complexity : O(n^2)
     two loops gives n*n/2 comparisons
  2. space complexity O(1)
     
# Approach 2: Sorted Array

## Idea

Sort the array and keep all the elements like this - [ (element, position) ] . use two pointers left and right. check if the sum of elements in left and right makes up the target 

## Code

2. Solution using sorted array
```java
   class Solution {
		class NumPos {
			int num;
			int pos;

			public NumPos(int num, int pos) {
				this.num = num;
				this.pos = pos;
			}
		};

		public int[] twoSum(int[] nums, int target) {

			int[] sols = new int[2];

			NumPos[] arr = new NumPos[nums.length];
			for(int i = 0; i< nums.length; i++) {
				arr[i] = new NumPos(nums[i], i);
			}

			Arrays.sort(arr, (a, b) ->Integer.compare(a.num, b.num));

			int left = 0;
			int right = nums.length -1;

			while(left < right) {
				if(arr[left].num + arr[right].num == target) {
					sols[0] = arr[left].pos;
					sols[1] = arr[right].pos;
					break;
				} else if(arr[left].num + arr[right].num > target) {
					right--;
				} else {
					left++;
				}
			}

			return sols;
		}
}
```
 1. time complexity: O(nlogn)- coming from sorting
 2. space complexity: O(n) 

# Approach 3: HashMap

## Idea

Use a hashmap with key as difference with target.

## Code
```java
   class Solution {
    public int[] twoSum(int[] nums, int target) {

        int[] sols = new int[2];
        Map<Integer, Integer> solmap = new HashMap<>();
        for(int i = 0; i < nums.length; i++) {
          int diff = target -  nums[i];
          if(solmap.containsKey(diff)) {
             sols[0] = solmap.get(diff);
             sols[1] = i;
             break;
          } else {
            solmap.put(nums[i], i);
          }
        }

        return sols;
    }
}
```
 1. time complexity: O(n)  - only one loop and hashmap searching/inserting is O(1)
 2. space complexity: O(n)

## Python code using dict 
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        diff_dict = {}

        for index, num in enumerate(nums):
            diff = target - num

            if diff in diff_dict:
                return [diff_dict[diff], index]

            diff_dict[num] = index
```
