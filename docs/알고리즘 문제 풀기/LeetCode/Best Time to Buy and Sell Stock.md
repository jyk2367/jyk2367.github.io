---
title: Best Time to Buy and Sell Stock
layout: default
nav_order: 1.1
parent: LeetCode
grand_parent: 알고리즘 문제 풀기
has_children: false
---


### [Best Time to Buy and Sell Stock](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/description/)
You are given an array prices where prices[i] is the price of a given stock on the ith day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.

 

Example 1:

Input: prices = [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.
Example 2:

Input: prices = [7,6,4,3,1]
Output: 0
Explanation: In this case, no transactions are done and the max profit = 0.
 

Constraints:

1 <= prices.length <= 105
0 <= prices[i] <= 104

### 생각한 방법
1. 이중for문으로 한번 풀고 접근맞는지 확인- O(N^2)라 구림
2. 결과만 저장하는 방식으로 변경 - idx와 maxNum을 두고 처리(카데인 알고리즘 Kadane's Algorithm)
- idx가 아니라 그냥 값을 저장하는 방식으로 바꿔도 상관없을듯.


### 답안
```c++
class Solution {
public:

    inline static const int MAX_PRICE_LENGTH = 100000; 
    int maxProfit(vector<int>& prices) {
        
        int price_length = prices.size();
        vector<pair<int,int>> profit(MAX_PRICE_LENGTH);

        for(int i = 0 ; i < price_length ; i++){
            profit[i] = {0,i};
            int current_price = prices[i];
            for(int j=0;j<i;j++){
                int last_price = prices[j];
                int sub = current_price - last_price;

                if(sub > 0 && profit[j].first < sub ){
                   profit[j] = {sub, i};
                }
            }
        }
        
        int maxNum = 0;
        for(auto p : profit){
            maxNum = max(p.first,maxNum);
        }
        
        return maxNum;
    }
};
```

```c++
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int idx = 0;
        int maxNum = 0;
        for(int i=0;i<prices.size();i++){
            int subValue = prices[i] - prices[idx];
            
            // 손절보는 경우 idx 변경
            if(subValue <= 0){
                idx = i;
                continue;
            }

            // Best Time to Sell
            if(subValue > maxNum){
                maxNum = subValue;
            }
        }


        return maxNum;
    }
};
```