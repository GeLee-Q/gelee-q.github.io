---
layout:     post
title:      DailyCode
subtitle:   日课
date:       2021-03-30
author:     Lee
header-img: img/code.jpg
catalog: true
tags:
   - leetcode
   - c++
   - Daily
  
---

# C++ Prime Plus

## Chapter 9 

### 单独编译

- 头文件：包含结构声明和使用这些结构的函数的原型
- 源代码文件：包函结构有关的函数代码
- 源代码文件：包含调用与结构相关的函数的代码

头文件中常包含的内容：

- 函数原型
- 使用#define或者const定义的符号常量
- 结构声明
- 类声明
- 模板声明
- 内联函数

### 存储连续性、作用域、和链接性

作用域（scope）描述了文件再多大范围内可见。例如，函数中定义的变量，仅仅能在此函数中使用。

链接性（linkage）描述了名称如何在不同单元间共享。链接性为外部可在文件间共享，为内部的名称只能由一个文件中的函数共享。

**自动存储连续性**

默认情况下，函数的参数和声明的变量的存储的连续性为自动，作用域为局部，没有链接性。

如果在代码块中定义了变量，其存在时间与作用域将被限制在改代码块内。

static 可以让变量在代码块之后仍存在，并且在**相应作用域做出限制。**表示其链接性为内部性。

如果要在多个文件中使用外部变量，只需在一个文件中包含该变量的定义（单定义规则），**但在使用该变量的其他所有文件中，都必须使用关键字extern声明它。**

计算经验表明，程序越能避免对数据进行不必要的访问，就越能保证数据的完整性。

- 通常编译器将使用三块独立的内存，一块用于静态变量，一块用于自动变量，一块用于动态存储。



new 运算符不仅可以在heap中找到 一个足以满足要求的内存块，也可以把它放到指定的为位置。

```c++
#include<new>
struct chaff
{
  char dross[20];
  int slag;
};
char buffer1[50];
char buffer2[200];

int main()
{
  chaff *p1 , *p2;
  int *p3,  *p4;
  
  p1 = new chaff;
  p3 = new int[20];
  
  p2 = new (buffer1) chaff; //place structure in buffer1
  p4 = new (buffer2) int[20]; // place int array in buffer2
  
}
```





# LC 最长公共前缀

```c++
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        if(strs.size() == 0 ) return "";

        int len = strs[0].length();

        for(int i = 0 ; i<len ; i++){
            char a = strs[0][i];
            for(int j = 1 ; j<strs.size(); j++){
                if( strs[j][i]!= a){
                    return strs[0].substr(0,i);
                }
            }
        }
        return strs[0];
    }
};
```











