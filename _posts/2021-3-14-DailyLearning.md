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



# LC215(M) 数组中第k个最大的元素 

```c++
class Solution {
public:
     int count;
     void heapIni(vector<int>& nums){
        int n = count;
        for (int i = n/2-1; i>=0; --i){
            
                int maxPos = i;
                if(i*2+1<n && nums[i]<nums[i*2+1]) maxPos = i*2+1;
                if(i*2+2<n && nums[maxPos]<nums[i*2+2]) maxPos=i*2+2;
                if(maxPos == i) continue;
                swap(nums[i],nums[maxPos]);
                i  = maxPos; 
                                           
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

# 思路

## 堆的特点

- 堆是一个完全二叉树
- 堆中的每一个节点都必须大于等于（或小于等于）其中每个节点的值。
- 插入一个数据，把新插入的数据放到数组的最后，进行从下往上的堆化。
- 删除堆顶数据，把最后一个数据放到堆顶，然后从上往下堆化。

## 解题思路

1. 生成一个大顶堆
2. 删除顶堆的数，重新生成堆。
3. 要第K大的数，就删除k-1个顶堆

### 生堆函数

```c++
void HeapInt(vector<int>& nums){
    int n = count;//count 即为生成堆的大小
    for(int i=n/2-1; i>=0; i--){
        int maxPos = i;
        if(i*2+1<n && nums[i]<nums[i*2+1]) maxPos = i*2+1;
        if(i*2+2<n && nums[maxPos]<nums[i*2+1]) maxPos = i*2+2;
        if(maxPos ==i) continue;
        swap(nums[i],nums[maxPos]); 
    }
};
```

### 取K最大值函数

```c++
  int count;
  int findKthLargest(vector<int>& nums, int k){
      count = nums.size()
      HeapInt(nums);
      if(k==1) return nums[0];
      while(k>1){
          int a = count -1;
          nums[0]=nums[a];
          count--;
          heapIni(nums);
          k--;
      }
      return nums[0]   
      }
  };
  
```

### 堆排序

```c++
int count;
void buildHeap(vector<int> nums){
    count = nums.size();
    int n = count;
    for(int i=n/2-1;i>=0;i--){
        heapify(nums,i);
    }
}
void heapify(vector<int> nums,int i ){
    while(true){
        int maxPos=i;
        if(i*2+1<=n && nums[i]<nums[i*2+!]) maxPos = i;
        if(i*2+2<=n && nums[maxPos]<[i*2+2]) maxPos = i*2+2;
        if(maxPos == i) break;
        swap(nums[i],nums[maxPos]);
        //i = maxPos;
    }
}

void sort(vector<int>& nums){
    buildHeap();
    int k = nums.size()-1;
    while(k>0){
        swap(nums[k],nums[0]);
        k--;
        heapify(nums,0);
    }
}
```

### 总结：

- 堆排序是原地排序算法；
- 建堆的过程时间复杂度是O(n);排序过程的时间复杂度是O(n*logn);所以整体的时间复杂独是O(n*logn)
- 缺点：堆化的过程是跳着访问的，对CPU的缓存不友好。
- 对于同样的数据，在排序过程中，堆排序算法的交换次数要多于快速排序。