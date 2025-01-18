---
title: Course Schedule
layout: default
nav_order: 1.7
parent: LeetCode
grand_parent: 알고리즘 문제 풀기
has_children: false
---


## [Course Schedule](https://leetcode.com/problems/course-schedule/description/)
There are a total of numCourses courses you have to take, labeled from 0 to numCourses - 1. You are given an array prerequisites where prerequisites[i] = [ai, bi] indicates that you must take course bi first if you want to take course ai.

For example, the pair [0, 1], indicates that to take course 0 you have to first take course 1.
Return true if you can finish all courses. Otherwise, return false.

 

Example 1:

Input: numCourses = 2, prerequisites = [[1,0]]
Output: true
Explanation: There are a total of 2 courses to take. 
To take course 1 you should have finished course 0. So it is possible.
Example 2:

Input: numCourses = 2, prerequisites = [[1,0],[0,1]]
Output: false
Explanation: There are a total of 2 courses to take. 
To take course 1 you should have finished course 0, and to take course 0 you should also have finished course 1. So it is impossible.
 

Constraints:

1 <= numCourses <= 2000
0 <= prerequisites.length <= 5000
prerequisites[i].length == 2
0 <= ai, bi < numCourses
All the pairs prerequisites[i] are unique.

## 생각한 방법
1. 위상정렬문제(답안봤음)

## 답안 후 생각
첨에 문제 이해가 안됐음.
위상정렬 문제인건 알았는데, 위상정렬 어떻게 풀었지 싶었음.
들어오는 간선이 없는 노드에서 시작해서 하나씩 연결된 Vertex에서 간선 -1하면서 처리하는 식으로 순서를 지킬수 있다는걸 답지 보고 기억했음.

## 내 답안
```
class Solution {
public:

    bool dfs(int numCourses,vector<vector<int>>& prerequisites){
        queue<int> q;
        vector<int> indegree(numCourses, 0);
        vector<vector<int>> edge(numCourses);
        for(vector<int> p:prerequisites){
            edge[p[1]].push_back(p[0]);
            indegree[p[0]]++;
        }

        for(int i=0;i<numCourses;i++){
            if(indegree[i]==0){
                q.push(i);
            }
        }
        
        int visited=0;
        while(!q.empty()){
            int now = q.front();
            q.pop();
            visited++;
            for(int e:edge[now]){
                indegree[e]--;
                if(indegree[e]==0){
                    q.push(e);
                }
            }
        }
        return visited==numCourses;
    }

    bool canFinish(int numCourses, vector<vector<int>>& prerequisites) {
        return dfs(numCourses, prerequisites);
    }
};
```

## 답안
```
    bool canFinish(int n, vector<vector<int>>& prerequisites) {
        vector<vector<int>> G(n);
        vector<int> degree(n, 0), bfs;
        for (auto& e : prerequisites)
            G[e[1]].push_back(e[0]), degree[e[0]]++;
        for (int i = 0; i < n; ++i) if (!degree[i]) bfs.push_back(i);
        for (int i = 0; i < bfs.size(); ++i)
            for (int j: G[bfs[i]])
                if (--degree[j] == 0) bfs.push_back(j);
        return bfs.size() == n;
    }
```