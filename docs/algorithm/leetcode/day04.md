---
layout: default
title: Day04 Remove Duplicates from Sorted Array
parent: LeetCode
grand_parent: Algorithm
nav_order: 4
---

# Day04

## Remove Duplicates from Sorted Array    

### Complexity  
- Time complexity:
o(n)  

- Space complexity:
o(1) -> inplace  

### Code  
```c++
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int j = 1;
        for(int i=1;i<nums.size();i++){
            if(nums[i] != nums[i-1]){
                nums[j] = nums[i];
                j++;
            }
        }
        return j;
    }
};
```