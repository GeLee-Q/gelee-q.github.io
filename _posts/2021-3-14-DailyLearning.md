---
layout:     post
title:      DailyLearning
subtitle:   每日一题
date:       2021-03-14
author:     Lee
header-img: img/code.jpg
catalog: true
tags:
   - leetcode
   - c++
   - Daily 
---



# LC202 

数组中第k个最大的元素

```c++
class Solution {
public:
     int count;
     void heapIni(vector<int>& nums){
        int n = count;
        for (int i = n/2-1; i>=0; --i){
            while(true){
                int maxPos = i;
                if(i*2+1<n && nums[i]<nums[i*2+1]) maxPos = i*2+1;
                if(i*2+2<n && nums[maxPos]<nums[i*2+2]) maxPos=i*2+2;
                if(maxPos == i) break;
                swap(nums[i],nums[maxPos]);
                i  = maxPos; 
            }                               
        }
    }

    int findKthLargest(vector<int>& nums, int k) {  
        count = nums.size();
        heapIni(nums);
        
        if(k==1)return nums[0];
        while(k>1){
            int a = count-1;
            // nums[0]= -2147483648;
            nums[0]= nums[a];
            count--;
            heapIni(nums);
            k--;
        }  
        return nums[0];
    }
};
```

```c++

```

