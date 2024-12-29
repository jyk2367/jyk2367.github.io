---
title: Climbing Stairs
layout: default
nav_order: 1.5
parent: LeetCode
grand_parent: 알고리즘 문제 풀기
has_children: false
---


## [Climbing Stairs](https://leetcode.com/problems/climbing-stairs/description/)
You are climbing a staircase. It takes n steps to reach the top.

Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?

 

Example 1:

Input: n = 2
Output: 2
Explanation: There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps
Example 2:

Input: n = 3
Output: 3
Explanation: There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
 

Constraints:

1 <= n <= 45

## 생각한 방법
1. 전형적인 DP문제면서 피보나치수열 생각나게하는 문제라 바로품


## 답안 후 생각
다른 답안 확인했는데, 공간 최적화 하는 부분도 있어서 유심히 봤음.
왜 지금까지 계속 배열 놔두고 거기다가 저장하는 식으로 했을까? 
타 블로그에서 이런걸 봤으면 분명 내가 확인했을 것 같은데.
그냥 이전 값 2개에 해당하는 값들을 따로 저장만 해놨으면 공간복잡도에서도 이득을 볼테니 이게 내가 생각하는 답에 가까운듯.

## 내 답안
```c++
class Solution {
public:
    int climbStairs(int n) {
        int ways[n+1];
        
        // init
        ways[0] = 1;
        ways[1] = 2;

        for(int i=2;i<n;i++){
            ways[i] = ways[i-1] + ways[i-2];
        }

        return ways[n-1];
    }
};
```

## 답안
```
class Solution {
public:
    int climbStairs(int n) {
        if (n == 0 || n == 1) {
            return 1;
        }
        int prev = 1, curr = 1;
        for (int i = 2; i <= n; i++) {
            int temp = curr;
            curr = prev + curr;
            prev = temp;
        }
        return curr;
    }
};
```