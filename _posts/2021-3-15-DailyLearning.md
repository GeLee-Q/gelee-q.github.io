---
layout:     post
title:      DailyLearning
subtitle:   每日一题
date:       2021-03-15
author:     Lee
header-img: img/code.jpg
catalog: true
tags:
   - leetcode
   - c++
   - Daily 
---

# LC 两数之和

给定一个已按照 **升序排列** 的整数数组 `numbers` ，请你从数组中找出两个数满足相加之和等于目标数 `target` 

## 方法1:对撞指针

### 思路

- 首先判断首尾两项的和是不是Target；
- 如果比Target大，则尾指针-1；如果比Target小，则首指针+1。

```c++
class Solution {
public:
    vector<int> twoSum(vector<int>& numbers, int target) {
        int i = 0; int j = numbers.size()-1;
        vector<int> a(2,0);
        int sum = numbers[i]+numbers[j];
        while(sum!=target){
            if(numbers[i]+numbers[j]>target) j--;
            if(numbers[i]+numbers[j]<target) i++;
            sum = numbers[i]+numbers[j];
        }
        a[0]=i+1;a[1]=j+1;
        return a;
    }
};
```

## 方法2:二分查找

### 思路

- 当看到数组有序，就应该想到二分查找。
- 遍历每个 nums[i]，在剩余数组中查找 target-nums[i] 的值，时间复杂度为 O(n log n)。

```c++
class Solution {
public:
    vector<int> twoSum(vector<int>& numbers, int target) {
        int mid;
        int low=0;
        int high=numbers.size()-1;
        for(int i=0;i<numbers.size()-1;++i){
            // 要在剩下的已经排序的数组里找，所以 low = i+1
            low=i+1;
            high=numbers.size()-1;
            while(low<=high){
                mid=low + (high-low)/2;
                if(numbers[i]+numbers[mid]==target)
                    return {i+1,mid+1};
                else if(numbers[i]+numbers[mid]<target)
                    low=mid+1;
                else
                    high=mid-1;
            }
        }
        return {-1,-1};
    }
};
```

