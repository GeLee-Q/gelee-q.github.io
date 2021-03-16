---
layout:     post
title:      DailyLearning
subtitle:   日课
date:       2021-03-16
author:     Lee
header-img: img/code.jpg
catalog: true
tags:
   - leetcode
   - c++
   - Daily 
---

> 落尽梨花春又了，满地残阳，翠色和烟老。

# 递归

分治法是一种是思想，递归是实现它的方法。

## 递归的三个条件：

- 一个问题的解可以分为几个子问题的解。
- 这个问题与分解后的子问题，除了数据规模不同，求解思路完全一样。
- 存在递归终止条件

## 如何编写递归代码：

1.找到大问题分解成小问题的规律

2.基于此写出递推公式

3.推敲终止条件

4.将递推公式和终止条件翻译成代码

## 弊端：

堆栈溢出；重复计算；函数调用耗时多；空间复杂度高；

## 调试递归：

1.打印日志发现，递归值。
2.结合条件断点进行调试。



# LC125 验证回文串

```c++
class Solution {
public:
    bool isPalindrome(string s) {
       
        if(s.length()<=1) return true;
        int i = 0; int j = s.size();
        while(i<j){
            while(!isalnum(s[i]) && i<j ) i++;
            while(!isalnum(s[j]) && i<j) j--;

            if (tolower(s[i])==tolower(s[j])){
                i++;
                j--;
                continue;
            } else{
                return false;
            }
        }
        return true;
    }
};
```

思路：对撞指针。

# LC345 反转字符串中元音字母

```c++
class Solution {
bool isVow(char l){
    if(l =='a' ||l =='e'||l =='i'||l =='o'||l =='u' ) return true;
    else {
        return false;
    }
}
public:
    string reverseVowels(string s) {
        int i=0 ; int j = s.size()-1;
        while (i < j)
    {
        while (!isVow(tolower(s[i])) && i < j)
            i++;
        while (!isVow(tolower(s[j])) && i < j)
            j--;
        swap(s[i],s[j]);
        i++;
        j--;
        continue;
    }
    return s;
    }
};
```

