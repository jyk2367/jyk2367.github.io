---
title: Number of 1 Bits
layout: default
nav_order: 1.4
parent: LeetCode
grand_parent: 알고리즘 문제 풀기
has_children: false
---


## [Number of 1 Bits](https://leetcode.com/problems/number-of-1-bits/description/)
Given a positive integer n, write a function that returns the number of 
set bits
 in its binary representation (also known as the Hamming weight).

 

Example 1:

Input: n = 11

Output: 3

Explanation:

The input binary string 1011 has a total of three set bits.

Example 2:

Input: n = 128

Output: 1

Explanation:

The input binary string 10000000 has a total of one set bit.

Example 3:

Input: n = 2147483645

Output: 30

Explanation:

The input binary string 1111111111111111111111111111101 has a total of thirty set bits.

 

Constraints:

1 <= n <= 231 - 1

## 생각한 방법
1. 1과 AND해서 각 bit count


## 답안 후 생각
일반적인 Iteration방식도 있고, Brian Kernighan의 정수의 bit를 계산하는 알고리즘도 있어서 확인해봤다.  
```
n & (n-1) : 숫자의 가장 오른쪽에 존재하는 비트를 끄는데 사용
```
0111010101이란 값이 있으면, 0111010101에서 맨 오른쪽 1을 말 그대로 꺼서 0111010100이 되는 것이다.  

0111010101
0111010100 &
= 0111010100

00110100
00110011 &
= 00110000 
00110100의 맨 오른쪽 1이 사라져 결과가 00110000이 되는 걸 확인할 수 있다.


## 내 답안
```c++
class Solution {
public:
    int MAX_INT = 0x7FFF'FFFF;
    int hammingWeight(int n) {
        int count = 0;
        while(n!=0){
            // count += (n & 1);
            if(n & 1 == 1){
                count++;
            }
            n = n >> 1;
        }

        return count;
    }
};
```
