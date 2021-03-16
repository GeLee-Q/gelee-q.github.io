---
layout:     post
title:      DailyLearning
subtitle:   每日一题
date:       2021-03-13
author:     Lee
header-img: img/code.jpg
catalog: true
tags:
   - leetcode
   - c++
   - Daily 
---

~~爱情求不得，知识学海无涯，人类用在苦难之中。~~



## LC 颜色分类

- 任务：颜色所代表的数值从小到大排列。

```c++
class Solution {
public:
    void sortColors(vector<int>& nums) {
        if (nums.size()<=1) return; 
        for(int i =1 ; i<nums.size();i++){\
            int value = nums[i];
            int j = i-1;
            // 后面未排序的每一个数都要和前面所有排序好的数对比
            for(;j>=0;j--){
                // 与最邻近的数对比，若是大于，则下一个数字
                // 若是小于，则将大数放到后面去。
                if (nums[j]>value){
                    swap(nums[j+1],nums[j]);
                }else{
                    break;
                }
            }
        }
    }
};
```

方法总结：

- 插入排序：1.元素比较 2.元素移动
- 数组中分为，已排序区间和未排序区间。每次将未排序的区间同已排序的区间的最后一位数来开始做，一旦小于这个数，那么将二者的数值进行互换，然后与下一个数进行比较。
- 插入排序是原地排序算法，也是稳定的排序算法。

