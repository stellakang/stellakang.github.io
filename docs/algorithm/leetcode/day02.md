---
layout: default
title: Day02 Max Points on a Line
parent: LeetCode
grand_parent: Algorithm
nav_order: 2
---

# Day02

## Max Points on a Line  

### Complexity
- Time complexity:
o(n * n/2)

- Space complexity:
o(n * n)

### Code  

```c++
class Solution {
public:
    int maxPoints(vector<vector<int>>& points) {
        sort(points.begin(), points.end());
        int len = points.size();
        int maxPoints = 1;

        vector<vector<bool>>visit(len, vector<bool>(len, false));
        for(int i=0;i<len;++i){
            int numOfPoints = maxPointsOnALine(points, visit, i, len, 0, 1);
            if(maxPoints<numOfPoints){
                maxPoints = numOfPoints;
            }   
        }
        return maxPoints;
    }

    int maxPointsOnALine(vector<vector<int>>& points, vector<vector<bool>>& visit, int index, int len, double slope, int cnt){
        if(index==len-1)
            return cnt;

        int maxPoints = cnt;
        for(int i=index+1;i<len;++i){
            if(visit[index][i])continue;
            double nextSlope;
            if(points[index][0] == points[i][0]){
                nextSlope = 10001;
            }
            else{
                nextSlope = (double)(points[i][1] - points[index][1])/(double)(points[i][0] - points[index][0]);
            }
            if(cnt == 1 || nextSlope == slope){
                visit[index][i] = true;
                int numOfPoints = maxPointsOnALine(points, visit, i, len, nextSlope, cnt+1);
                if(maxPoints<numOfPoints){
                    maxPoints = numOfPoints;
                }
            }
        }
        return maxPoints;
    }

};
```
