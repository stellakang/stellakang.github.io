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
    int ladderLength(string beginWord, string endWord, vector<string>& wordList) {
        int length = beginWord.length();
        int listSize = wordList.size();
        int endIndex = -1;
        vector<int>graph[5003];
        
        for(int i=0;i<listSize;++i){
            if(wordList[i] == endWord){
                endIndex = i;
                break;
            }
        }
        if(endIndex==-1)return 0;

        bool visit[5002];
        for(int i=0;i<listSize;++i){
           visit[i] = false;
        }
        for(int i=0;i<listSize;++i){
            for(int j=i+1;j<listSize;++j){
                int cnt = 0;
                for(int k=0;k<length;++k){
                    if(wordList[i][k] != wordList[j][k]){
                        if(++cnt>1)break;
                    }
                }
                if(cnt==1){
                    graph[i].push_back(j);
                    graph[j].push_back(i);
                }
            }
        }
        queue<int> qu;
        for(int i=0;i<listSize;++i){
            int cnt = 0;
            for(int k=0;k<length;++k){
                if(beginWord[k] != wordList[i][k]){
                    if(++cnt>1)break;
                }
            }
            if(cnt==0){
                visit[i] = true;
            }
            if(cnt==1){
                qu.push(i);
                visit[i] = true;
            }
        }
       
        int cost = 2;
        while(!qu.empty()){ 
            int size = qu.size();
            while(size--){
                int currentWord = qu.front();
                qu.pop();
                if(currentWord == endIndex)return cost;
                for(int nextWord: graph[currentWord]){
                    if(!visit[nextWord]){
                        qu.push(nextWord);
                        visit[nextWord] = true;
                    }
                }
            }
            ++cost;
        }
        return 0;
    }
};
```