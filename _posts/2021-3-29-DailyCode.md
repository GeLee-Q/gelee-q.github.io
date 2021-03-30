---
layout:     post
title:      DailyCode
subtitle:   日课
date:       2021-03-29
author:     Lee
header-img: img/code.jpg
catalog: true
tags:
   - leetcode
   - c++
   - Daily
  
---

> a

# C++ Prime Plus

## Chapter 8

### 引用

引用不同于指针，指针可以先声明，再赋值，而引用声明时就要初始化。

使用引用的好处是，不用创建新的对象。

```c++
int & rodents = rats;
int * const pr = &rats;
```

```c++
//交换两个变量的值
void swapr(int & a, int & b){
  int temp ;
  temp = a;
  a = b;
  b = temp; 
}

//按值传递并不能实现这个功能
void swapr(int a, int  b){
  int temp ;
  temp = a;
  a = b;
  b = temp; 
}
```

函数的返回尽量避免一个临时的引用，因为函数运行后，这个变量将不复存在。

为了避免这种问题，返回一个作为参数传递给函数的引用。作为参数的引用，将指向调用函数使用这些数据，因此返回的引用也将指向这些数据。

**赋值表达式中，左值必须是可以修改的。**

- 通过传递引用，而不是整个数据对象，可以提高程序的运行速度。
- 数据对象是数组，则使用指针。
- 当数据对象是较大的结构时，则使用const指针或者const引用，可以提高程序的效率，节省复制的时间和空间。
- 数据对象是类对象，则使用引用。

### 函数多态（函数重载）

函数重载的关键是函数的参数列表-------即函数的特征标。

### 函数模版

```c++
template <typename AnyType>
void Swap(AnyType &a, AnyType &b)
{
  Anytype temp;
  temp =  a;
  a = b;
  b = temp;
}
```

调用函数模块，是一种实例化。自动完成重载函数的过程。



# LC   外观数列

```c++
class Solution {
public:
    string countAndSay(int n) {
        if (n == 1) return "1";

        string s = countAndSay(n-1);
        string r ;
        
        int cnt = 1;

        for (int i = 0 ; i<s.size(); i++ )
        {
            if(s[i]!=s[i+1]){
                r.push_back(cnt+'0');
                r.push_back(s[i]);
                cnt = 1;
            }else{
                cnt++;
            }
    
        }
        return r;

    }
};
```

