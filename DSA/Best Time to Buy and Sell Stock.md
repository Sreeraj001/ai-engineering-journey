### Problem 

You are given an array prices where prices[i] is the price of a given stock on the ith day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.

Example 1:

Input: prices = [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.

### Idea

let minPrice = array[0] and maxprofit = 0
for i in 1 to length of array
if array[i] greater than minPrice
update minPrice = array[i]
else if array[i] - minPrice > maxProfit
update maxprofit =  array[i] - minPrice
return maxProfit

### Complexity
Time : O(n)
Space: O(1)

### Code -Java
```java
class Solution {
    public int maxProfit(int[] prices) {
        int minPrice = int[0];
        int maxProfit = 0;

        for(int i= 1; i< prices.length; i++) {
            if(prices[i] < minPrice) {
                minPrice = prices[i];
            } else if(prices[i] - minPrice > maxProfit) {
                maxProfit = prices[i] - minPrice;
            }
        }

        return maxProfit;
    }
}
```

### Code - Python
```python
class Solution:
    def maxProfit(self, prices: list[int]) -> int:
        minPrice = prices[0]
        maxProfit = 0

        for i in range(1, len(prices)):
            if prices[i] < minPrice:
                minPrice = prices[i]
            elif prices[i] - minPrice > maxProfit:
                maxProfit = prices[i] - minPrice

        return maxProfit 
```
