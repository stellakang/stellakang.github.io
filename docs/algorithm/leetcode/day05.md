---
layout: default
title: Day05 Best Time to Buy and Sell Stock II
parent: LeetCode
grand_parent: Algorithm
nav_order: 5
---

# Day05

## Best Time to Buy and Sell Stock II    

### Complexity  
- Time complexity:
o(n)

- Space complexity:
o(1)

### Code  
```c++
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int profit = 0;
        int num = 10001;
        for(int i=0;i<prices.size();++i){
            if(prices[i] > num){
                profit += prices[i] - num;
            }
            num = prices[i];
        }
        return profit;
    }
};
```
