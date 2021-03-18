---
layout:     post
title:      DailyCode
subtitle:   日课
date:       2021-03-17
author:     Lee
header-img: img/code.jpg
catalog: true
tags:
   - leetcode
   - c++
   - Daily 

---

> 醉里且贪欢笑，要愁哪得功夫？

# LC209 (M) 长度最小的字数组



```c++
public:
    int minSubArrayLen(int target, vector<int>& nums){
        int i=0;
        int len=65535;
        int sum=0;
        for(int j=0;j<nums.size();j++){
            sum+=nums[j];
            while(sum-nums[i]>=target)
                sum-=nums[i++];
            if(sum>=target&&j-i+1<len)
                    len=j-i+1;
        }
        if(len==65535) return 0; 
        return len;
    }
};
```