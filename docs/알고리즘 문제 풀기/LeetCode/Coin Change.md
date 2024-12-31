---
title: Coin Change
layout: default
nav_order: 1.6
parent: LeetCode
grand_parent: 알고리즘 문제 풀기
has_children: false
---


## [Coin Change](https://leetcode.com/problems/coin-change/description/)
You are given an integer array coins representing coins of different denominations and an integer amount representing a total amount of money.

Return the fewest number of coins that you need to make up that amount. If that amount of money cannot be made up by any combination of the coins, return -1.

You may assume that you have an infinite number of each kind of coin.

 

Example 1:

Input: coins = [1,2,5], amount = 11
Output: 3
Explanation: 11 = 5 + 5 + 1
Example 2:

Input: coins = [2], amount = 3
Output: -1
Example 3:

Input: coins = [1], amount = 0
Output: 0
 

Constraints:

1 <= coins.length <= 12
1 <= coins[i] <= 231 - 1
0 <= amount <= 104

## 생각한 방법
1. 이중for문으로 가능한 모든 방식을 확인 - time limit에 걸림
2. 코인수가 12개라 재귀접근 - 가능은한데 dp문제라 웬만하면 안쓰고싶었음
3. 재귀에서 한단계 나아가서 for문으로 선택 or 미선택에 따라 결과값 출력(DFS랑 접근개념같음)

## 답안 후 생각
```
if (arr[j - curr_coin] != INT_MAX) {
    arr[j] = min(arr[j], arr[j - curr_coin] + 1);
}
```
 j-curr_coin이 0,1,2,3,4....이런식으로 늘어나는데, 그중 가능한 값.   
 그러니까 그 값까지의 결과가 남아있으면 +1하는 방식, 아니라면 기존 값 유지.  


## 내 답안
[1차답안]
```c++
class Solution {
public:
    int MAX_INT_NUM = 0x7FFF'FFFF;
    int coinChange(vector<int>& coins, int amount) {
        vector<int> arr(amount + 1,MAX_INT_NUM);

        arr[0] = 0;
        for(int i=0 ; i<coins.size() ; i++){
            if(amount>= coins[i])
                arr[coins[i]] = 1;
        }

        for(int i=1 ; i<= amount ; i++){
            for(int j=1;j<=i/2;j++){
                if(arr[j]!=MAX_INT_NUM & arr[i-j]!=MAX_INT_NUM){
                    arr[i] = min(arr[j] + arr[i-j], arr[i]);
                }
            }
        }

        if(arr[amount] == MAX_INT_NUM){
            return -1;
        }
        return arr[amount];
    }
};
```

[2차답안]
```
class Solution {
public:
    int MAX_INT_NUM = 0x7FFF'FFFF;
    int coinChange(vector<int>& coins, int amount) {
        vector<int> arr(amount + 1,MAX_INT_NUM);
        arr[0] = 0;

        for (int i=0;i<coins.size();i++) {
            int curr_coin = coins[i];
            for (int j = curr_coin; j <= amount; j++) {
                if (arr[j - curr_coin] != INT_MAX) {
                    arr[j] = min(arr[j], arr[j - curr_coin] + 1);
                }
            }
        }

        return arr[amount] == MAX_INT_NUM ? -1 : arr[amount];
    }
};
```

## 답안
```
class Solution {
public:
    int coinChange(vector<int>& coins, int n) {
        // creating the base dp array, with first value set to 0
        int dp[++n];
        dp[0] = 0;
        // more convenient to have the coins sorted
        sort(begin(coins), end(coins));
        // populating our dp array
        for (int i = 1; i < n; i++) {
            // setting dp[0] base value to 1, 0 for all the rest
            dp[i] = INT_MAX;
            for (int c: coins) {
                if (i - c < 0) break;
                // if it was a previously not reached cell, we do not add use it
                if (dp[i - c] != INT_MAX) dp[i] = min(dp[i], 1 + dp[i - c]);
            }
        }
        return dp[--n] == INT_MAX ? -1 : dp[n];
    }
};
```