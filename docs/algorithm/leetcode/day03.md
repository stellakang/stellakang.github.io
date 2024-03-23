---
layout: default
title: Day03 Word Ladder
parent: LeetCode
grand_parent: Algorithm
nav_order: 3
---

# Day03

## Word Ladder  

### Complexity
- Time complexity:
o(wordlength * n * n/2)

- Space complexity:
o(n * n)

### Code  
```c++
class Solution {
public:
    bool isConnected(string fromWord, string toWord, int len){
        int cnt = 0;
        for(int i=0;i<len;++i){
            if(fromWord[i] != toWord[i]){
                if(++cnt>1)return false;
            }
        }
        if(cnt==1)return true;
        return false;
    }
    int ladderLength(string beginWord, string endWord, vector<string>& wordList) {
        int length = beginWord.length();
        int listSize = wordList.size();
        int srcIndex = -1;
        int endIndex = -1;
        vector<int>graph[5003];
        for(int i=0;i<listSize;++i){
            if(wordList[i] == endWord){
                endIndex = i;
            }
            if(wordList[i] == beginWord){
                srcIndex = i;
            }
        }
        if(endIndex==-1)return 0;
        for(int i=0;i<listSize;++i){
            for(int j=i+1;j<listSize;++j){
                if(isConnected(wordList[i], wordList[j], length)){
                    graph[i].push_back(j);
                    graph[j].push_back(i);
                }
            }
        }
        vector<int>cost(listSize+1, 0xffffff);

       
        if(srcIndex == -1){
            srcIndex = listSize;
            for(int i=0;i<listSize;++i){
            if(isConnected(beginWord, wordList[i], length)){
                graph[i].push_back(srcIndex);
                graph[srcIndex].push_back(i);
            }
            }
        }
        queue<int> qu;
        qu.push(srcIndex);
        cost[srcIndex] = 1;
        
        while(!qu.empty()){
            int currentWord = qu.front();
            if(currentWord == endIndex){
                return cost[endIndex];
            }
            qu.pop(); 
            for(int nextWord: graph[currentWord]){
                if(cost[nextWord]> cost[currentWord]+1){
                    cost[nextWord] = cost[currentWord] + 1;
                    qu.push(nextWord);
                }
            }
        }
        return 0;
    }
};


```