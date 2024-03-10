---
layout: default
title: Day01 Wildcard Matching
parent: LeetCode
grand_parent: Algorithm
nav_order: 1
---

# Day01

## Wildcard Matching  

### Complexity
- Time complexity:
o(n * m)

- Space complexity:
o(n * m) + O(n + m)

### Code
```c++
class Solution {
public:
    bool solve(int i, int j, string &s, string&p, vector<vector<int>> &dp){
        if(i<0 && j<0)return true;
        if(j<0)return false;
        if(i<0){
            for(int index=j;index>=0;--index){
                if(p[index] != '*')return false;
            }
            return true;
        }
        if(dp[i][j] != -1) return dp[i][j];
        if(s[i] == p[j] || p[j] == '?'){
            return dp[i][j] = solve(i-1, j-1, s, p, dp);
        }
        if(p[j] == '*'){
            return dp[i][j] = solve(i, j-1, s, p, dp) || solve(i-1,j,s,p, dp);
        }
        return dp[i][j] = false;
    }
    bool isMatch(string s, string p) {
        int slen = s.length();
        int plen = p.length();

        vector<vector<int>> dp(slen, vector<int>(plen, -1));
        return solve(slen-1, plen-1, s, p, dp);
    }
};
```

