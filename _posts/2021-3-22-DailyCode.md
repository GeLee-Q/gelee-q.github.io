---
layout:     post
title:      DailyCode
subtitle:   日课
date:       2021-03-22
author:     Lee
header-img: img/code.jpg
catalog: true
tags:
   - leetcode
   - c++
   - Daily
---

> 伐木丁丁，鸟鸣嘤嘤。
>
> 出自幽谷，迁于乔木。
>
> 嘤其鸣矣，求其友声。

# LC344 反转字符串

```c++
class Solution {
public:
    void reverseString(vector<char>& s) {
        int n = s.size();
        int i = 0 ; int j = n -1;
        while(i<j){
            swap(s[i],s[j]);
            i++;
            j--;
        }
    }
};
```

[^思路]: 双指针

```c++
class Solution {
public:
    void reverseString(vector<char>& s) {
        reverse(s.begin(),s.end());
       
    }
};
```

# LC7 整数反转

```c++
class Solution {
public:
    int reverse(int x) {
        long a = 0 ;
        while(x!=0){
            a = a*10+x%10;
            x = x /10;
        }
        return (int) a == a ? (int) a : 0;
    }
};
```

[^条件?表达式1:表达式2]: 当(int) a == a 时，则返回 (int) a，否则返回0 。



# C++ Prime Plus

```c++
int* p_value;
```

- 其中  p_value  是指针的值，也就是地址；
- *p_value 则是指针地址所存储的值；

**指针的使用危险:**

C++中创建指针，计算机只会分配存储指针的地址；不会分配存储指针指向数据的内存。

```c++
 int* p_value = new int ;
```

**动态数组：**

动态意味着是在运行时分配内存，而不是编译时分配。

```c++
// type_name* pointer_name = new type_name [num_elements]
int* psome = new int[10];
p[0] = 1;    //操作的数组的值
p = p + 1 ;  //操作的是指针的值
```

指针和数组基本等价的原因在于指针运算和C++内部的处理方式。

将指针变量+1后，其增加的值等于指向的类型占用的字节数。

多数情况下，C++将数组名解释为数组第一个元素的地址，而对数组名进行取址运算符时，得到的是整个数组的地址。

 **字符串：**

(Int*) ps 显示该字符串的地址；

```c++
ps = new char[strlen(animal)+1]; // get new storage
strcpy(ps,animal);               // copy string to new storage
```



