---
title: Sum of Two Integers
layout: default
nav_order: 1.2
parent: LeetCode
grand_parent: 알고리즘 문제 풀기
has_children: false
---


## [Sum of Two Integers](https://leetcode.com/problems/sum-of-two-integers/description/)
Given two integers a and b, return the sum of the two integers without using the operators + and -.

Example 1:

Input: a = 1, b = 2
Output: 3
Example 2:

Input: a = 2, b = 3
Output: 5
 

Constraints:

-1000 <= a, b <= 1000

## 생각한 방법
`+`와 `-`를 사용하지 않고 덧셈 구현 문제

## 팁
[Bit 다루는 방법](https://leetcode.com/problems/sum-of-two-integers/solutions/84278/a-summary-how-to-use-bit-manipulation-to-solve-problems-easily-and-efficiently) 


1. Set union : A | B  
-   집합론에서의 합집합(Union)에 해당
-   비트적으로 보면, A와 B에서 1인 비트가 하나라도 있으면 결과가 1이 됨
<br/>  

2. Set intersection : A & B
 - 집합론에서의 교집합(Intersection)에 해당
 - A와 B에서 동시에 1인 비트만 결과가 1이 됨
<br/>  

3. Set subtraction : A & ~B
 - 집합론에서의 차집합(Subtraction)에 해당
 - A에서 B에 해당하는 부분을 제거
 - A에서 1인 비트 중 B에서 1인 비트를 제외(즉, B가 1인 곳을 0으로)
<br/>  

4. Set negation ALL_BITS : ^ A or ~A
 - 집합론에서의 여집합(Complement)에 해당
 - 모든 비트(ALL_BITS)에서 A가 1인 비트를 0으로, 0인 비트를 1로 뒤집음
 - ~A(비트 NOT)와 같은 의미 (단, ~A 사용 시 전체 비트 수(ALL_BITS 크기)에 유의)
<br/>  

5. Set bit : A |= 1 << bit
  - 특정 위치(bit)의 비트를 1로 설정
  - 예: bit=3이면 (1 << 3)은 0b1000
  - A |= 0b1000은 A의 3번째 비트를 1로 만든다
<br/>  

6. Clear bit : A &= ~(1 << bit)
 - 특정 위치(bit)의 비트를 0으로 설정
 - 예: bit=3이면 (1 << 3)은 0b1000
 - ~(0b1000)은 0b0111 (해당 위치만 0이 된 마스크)
 - A &= 0b0111은 A의 3번째 비트를 0으로 만든다
<br/>  

7. Test bit : (A & 1 << bit) != 0
  - 특정 위치(bit)가 1인지 검사
  - 예: bit=3이면 (A & 0b1000)이 0이 아니면 A의 3번째 비트가 1
<br/>  

8. Extract last bit : A & -A (또는 A & ~(A-1), x ^ (x & (x-1)))
 - "가장 오른쪽에 있는 1비트"만 추출
 - 예: A = 0b10100일 때 → A & -A는 0b00100 (맨 마지막 1비트)
 - A & ~(A-1), x ^ (x & (x-1))도 같은 효과
<br/>  

9. Remove last bit : A & (A - 1)
 - "가장 오른쪽에 있는 1비트"를 제거
 - 예: A = 0b10100 → A - 1 = 0b10011, 따라서 0b10100 & 0b10011 = 0b10000
 - 오른쪽 끝 1비트가 사라진 값이 됨
<br/>  

10. Get all 1-bits : ~0
- 모든 비트가 1로 설정된 값
- 2의 보수 체계에서 ~0은 이론상 무한 개의 1비트이지만,
  실제 컴퓨터에서는 자료형 크기(int, long 등)에 따라 최대 비트 수만큼 1이 됨
<br/>  

보던 중 좋은 게 있어서 가져왔음. 
AND, OR, XOR, 쉬프트연산 알아도 이런팁 기억못하면 코테풀때 생각해서 만들어 풀어야해서 시간상 불리할듯.

## 문제 공부하면서 다시 확인한 내용
반가산기는 “Carry-in이 없는” 1비트 덧셈 담당.  
전가산기는 “Carry-in이 있는” 1비트 덧셈 담당.  <br/>  
덧셈은  **여러 자리(bit)**에 대해 반복해야 하므로 전가산기를 while문을 돌면서 처리하도록 만든 게 이번 문제 답안.
<br/>  
반가산기
- 반가산기는 이진수 한 자리씩 더할 때, 두 입력 비트(A, B)에 대해서 **합(Sum)**과 **올림(Carry)**를 구해주는 디지털 논리 회로입니다. 
- “반가산기”라고 불리는 이유는, 이전 자리에서 넘어온 캐리(Carry-in)는 고려하지 않기 때문입니다.
<br/>  
전가산기
- 전가산기는 **이전 자리에서 넘어온 캐리(Carry-in)**까지 고려하여, 세 개의 입력 비트(A, B, Carry-in)를 더한 결과를 산출하는 디지털 논리 회로입니다. 
- 결과로는 **부분합(Sum)**과 새로운 **올림(Carry-out)**을 출력합니다.



## 답안
```c++
class Solution {
public:
    int getSum(int a, int b) {
        // 캐리가 생기는 부분 덧셈을 하면 됨.
        
        while(b!=0){
            int carry = a & b;
            a = a ^ b;
            b = carry << 1;
        }

        return a;
    }
};
```