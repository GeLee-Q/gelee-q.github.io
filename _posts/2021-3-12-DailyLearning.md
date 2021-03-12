---
layout:     post
title:      DailyLearning
subtitle:   每日一题
date:       2021-03-12
author:     Lee
header-img: img/leetcode.jpg
catalog: true
tags:
   - leetcode
   - c++
   - Daily 
---

# 数组基础知识

## LC 移动零

给定一个数组 `nums`，编写一个函数将所有 `0` 移动到数组的末尾，同时保持非零元素的相对顺序。

```c++
class Solution {
    
public:
    void moveZeroes(vector<int>& nums) {
        // int i = 0 ;
        int j = 0 ;
        for (int i=0  ; i<nums.size();i++){
            if(nums[i]!=0){
                // temp = nums[j];
                // nums[j]=nums[i];
                // nums[i]=temp;
                swap (nums[j],nums[i]);
                j++;
            }
        }
       
    }
};
```

思路：

- 双指针，一个用来存放迭代出来的非零的数，另一个用来迭代。
- 最开始想用一个指针作为末尾，另一个来进行迭代，但是没写出来

```c++
//k 维护新的数组，指向最后一个数,另一个指针来遍历原数组,最后剩下的地方置0
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int n = nums.size();
        int k = 0;
        for(auto x :nums)
            if(x) nums[k ++] = x;

        while(k < n) nums[k ++] = 0;

    }
};


```

```c++
//冒泡的方法
class Solution {
public:
    void moveZeroes(vector<int>& nums) {
        int n = nums.size();
        // 冒泡 从后给前面找 找到 0 一直交换到最后不是0的地方
        for(int i = n - 1; i >= 0; i--)  
            if(nums[i] == 0)
                for(int j = i; j < n - 1; j++)
                    if(nums[j + 1] != 0)
                        swap(nums[j], nums[j + 1]);
            
    }
};

```

## LC 移除元素

```c++
class Solution {
public:
    int removeElement(vector<int>& nums, int val) {
        int j = 0 ;
        for (int i=0;i<nums.size();++i ){
            if(nums[i]!=val){
                nums[j]= nums[i];
                ++j;
            }
        }
        return j;
    }
    
};
```

## LC 删除排序数组中的重复项

```c++
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        if (nums.size()==0)
            return 0;
        else if (nums.size()==1)
            return 1;
        int j = 1;
        for(int i= 0; i<nums.size()-1; i++){
            if(nums[i]!=nums[i+1]){
                nums[j]=nums[i+1];
                j++;
            }
        } 
        return j;
```

## LC 删除排序数组中的重复项 保留两个一样的

```c++
class Solution {
public:
    int removeDuplicates(vector<int>& nums) {
        int len = 0;
        for (int i = 0; i < nums.size(); i++) {
            if (len < 2 || nums[i] != nums[len-2])
                nums[len++] = nums[i];
        }
        return len;
    }
};


```

# LeetCode 88

## 合并两个有序数组

思路：构造一个独立的数组，剩下两个数组归并排序，必将先处理完一个数组，剩下的数组直接添加即可。

```c++
class Solution {
public:
    void merge(vector<int>& nums1, int m, vector<int>& nums2, int n) {
        vector<int> nums3;
        int i = 0;
        int j = 0;
        //第一个循环将较小的那个先排完，剩下的两个是随机处理没排完的，直接添加就好。
        while(i<m && j<n) {
            if(nums1[i]<nums2[j]){
                nums3.push_back(nums1[i]);
                i++;
            }
            else
            {
                nums3.push_back(nums2[j]);
                j++;
            }
        while(i<m){
            nums3.push_back(nums1[i]);
            i++;
        }
        while(j<n){
            nums3.push_back(nums2[j]);
            j++;
        }
        nums1 = nums3;
        }            
    }
};
```

