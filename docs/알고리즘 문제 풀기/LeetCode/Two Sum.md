---
title: Two Sum
layout: default
nav_order: 1.3
parent: LeetCode
has_children: false
---


### [Two Sum](https://leetcode.com/problems/two-sum/description/)
Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

You may assume that each input would have exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

 

Example 1:

Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
Example 2:

Input: nums = [3,2,4], target = 6
Output: [1,2]
Example 3:

Input: nums = [3,3], target = 6
Output: [0,1]

Constraints:
2 <= nums.length <= 104
-109 <= nums[i] <= 109
-109 <= target <= 109
Only one valid answer exists.

### 생각한 방법
1. __order 후 체크? : order이 들어가는 순간 O(NlogN)이라 거름__
2. __Map만들고 체크 : 시간복잡도 O(N), 공간복잡도 O(N)라 이걸 사용__
3. ~~이중for문 : O(N^2)~~


### 답안 후 생각
LeetCode는 언어별 속도차이 지원을 안해서 앞으로 C++로만 풀어야 할 것 같다.  
속도가 너무 느려서 확인해보니 언어차이.  
내가 구현한 건 Approach 3 : One-pass Hash Table이라고 한다. 
Approach1은 이중for문이라 거르고, Approach2,3은 Map에다 넣는 족족 검사하는 방법이랑, 맵에 다 넣고 난 뒤에 검사하는 방법의 차이.  

답변 보니까 어차피 순차적으로 넣는 방식을 사용하고 있어서 indexMap하나만 사용해도 됨.  
map과 unordered_map의 차이로 시간복잡도가 O(N)까지 내려가게 됨.


### 내 답안
```java
class Solution {

    static final int MAX_NUMS_LENGTH = 10000;
    public int[] twoSum(int[] nums, int target) {
        Map<Integer,Integer> board = new HashMap<>(MAX_NUMS_LENGTH);
        Map<Integer,Integer> boardIdx = new HashMap<>(MAX_NUMS_LENGTH);
        
        // initialize (nums size min=2)
        board.put(nums[0],target-nums[0]);
        boardIdx.put(target-nums[0],0);

        for(int i=1 ; i<nums.length ; i++){
            if(board.containsValue(nums[i])){
                return new int[]{boardIdx.get(nums[i]),i};
            }

            board.put(nums[i],target-nums[i]);
            boardIdx.put(target-nums[i],i);
        }


        return new int[]{0,0};
    }
}
```

```c++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        map<int,int> board;
        map<int,int> boardIdx;

        // initialize (nums size min=2)
        board[nums[0]] = target-nums[0];
        boardIdx[target-nums[0]] = 0;

        for(int i=1;i<nums.size();i++){
            if(boardIdx.find(nums[i]) != boardIdx.end()){
                return vector<int>{boardIdx[nums[i]], i};
            }

            int opposite_number = target-nums[i];
            board[nums[i]] = opposite_number;
            boardIdx[opposite_number] = i;
        }


        // error handling
        return {0,0};

    }
};
```

# 정답
```c++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        unordered_map<int,int> indexMap;

        for(int i=0;i<nums.size();i++){
            int opposite_num = target-nums[i];
            if(indexMap.find(opposite_num) != indexMap.end()){
                return {indexMap[opposite_num], i};
            }
            indexMap[nums[i]] = i;
        }


        // error handling
        return {};

    }
};
```