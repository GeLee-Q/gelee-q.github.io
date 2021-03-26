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

>   既要马儿跑，又要马儿不吃草。

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





# LC 字符串转换整数 (atoi)

> 请你来实现一个 myAtoi(string s) 函数，使其能将字符串转换成一个 32 位有符号整数（类似 C/C++ 中的 atoi 函数）。
>
> 函数 myAtoi(string s) 的算法如下：
>
> 读入字符串并丢弃无用的前导空格
> 检查下一个字符（假设还未到字符末尾）为正还是负号，读取该字符（如果有）。 确定最终结果是负数还是正数。 如果两者都不存在，则假定结果为正。
> 读入下一个字符，直到到达下一个非数字字符或到达输入的结尾。字符串的其余部分将被忽略。
> 将前面步骤读入的这些数字转换为整数（即，"123" -> 123， "0032" -> 32）。如果没有读入数字，则整数为 0 。必要时更改符号（从步骤 2 开始）。
> 如果整数数超过 32 位有符号整数范围 [−231,  231 − 1] ，需要截断这个整数，使其保持在这个范围内。具体来说，小于 −231 的整数应该被固定为 −231 ，大于 231 − 1 的整数应该被固定为 231 − 1 。
> 返回整数作为最终结果。

```c++
class Solution {
public:
    int myAtoi(string s) {
        int i = 0 ; int n = s.size();int sign = 1;
				//处理空格
        while(isspace(s[i])){
            i++;
        }
				//处理字母
        if(isalpha(s[i])) return 0;
        //处理符号
        if(s[i] ==  '-') {
            sign = -1;
            i++;
        }else if(s[i] =='+') {
            sign = 1;
            i++;
        }

        if(s[i] ==  '+' || s[i] ==  '-' ) return 0 ;

				// 处理数据
        int a  = i;
        double num1 = 0;
        while(isdigit(s[i])) {
            int num = s[i]-'0';
            num1 = num1*10+num;
            i++;
        }
        
        if(num1*sign>-2147483648 && num1*sign<2147483647) return num1*sign;
        else if (sign>0) return 2147483647;
        else return 2147483648;
    }
};
```



