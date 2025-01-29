---
layout: default
title: Day06 Rotate Array
parent: LeetCode
grand_parent: Algorithm
nav_order: 6
---

# Day06

## Rotate Array    

### Complexity  
- Time complexity:
o(n)  

- Space complexity:
o(1) -> inplace  

### Code  
```c++
class Solution {
public:
    void reverse(vector<int>&nums, int from, int to){
        while(from<to){
            swap(nums[from], nums[to]);
            ++from;
            --to;
        }
    }
    void rotate(vector<int>& nums, int k) {
        int size = nums.size();
        reverse(nums, 0, size-1);
        reverse(nums, 0, k%size-1);
        reverse(nums, k%size, size-1);
    }
};
```