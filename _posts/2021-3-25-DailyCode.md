---
layout:     post
title:      DailyCode
subtitle:   日课
date:       2021-03-25
author:     Lee
header-img: img/code.jpg
catalog: true
tags:
   - leetcode
   - c++
   - Daily
---

# C++ Prime Plus

## Chapter 7

  **指针和const**：

1. 让指针指向一个常量对象；防止使用该指针修改所指向的值；
2. 将指针本身声明为一个常量，防止改变指针指向的位置；

```c++
//指向常量的指针pt
int age  = 39 ;
const int* pt = &age;

*pt +=1 // invalid because pt points to a const int
//可以通过修改age来改变age的值，但是不能使用pt指针来改变age的值
```

**C++禁止将const的地址赋给非const指针；**

将指针参数声明为指向常量数据的指针有两条理由：

- 可以避免无意间修改数据而导致的编程数据；
- 使用const使得函数能够处理const和非const实参，否则将只能接受非const数据；

```c++
int sloth = 3;
const int* pt = &sloth;		//a pointer to const int 
int* const finger = &sloth; //a const pointer to int
```



**递归**

```c++
void recures(arguments)
{
    statements1
    if(test)
        recures(arguments)
    statements2
}
```

每个递归调用都创建自己的一套变量。

**函数指针**

- 获取函数的地址
- 声明一个函数指针
- 使用函数指针来调用函数

1.获取函数的地址

```c++
process(think);  // passes address of think() to process()
process(think()) // passes return value of think() to thought
```

2.声明函数指针

```c++
double pam(int)    //prototype
double (*pf)(int)  //pf points to a function that returns double 
pf = pam ;         // pf now points to the pam() function 
```

3.使用指针来调用函数

```c++
double x = pam(4);   //call pam use the function name
double y = (*pf)(5); //call pam use the pointer pf
```















