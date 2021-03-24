---
layout:     post
title:      DailyCode
subtitle:   日课
date:       2021-03-24
author:     Lee
header-img: img/code.jpg
catalog: true
tags:
   - leetcode
   - c++
   - Daily
---

> 无所可用，安所困苦哉

# C++ Prime Plus

## Chapter 6

{}**表示其之间是一个语句块**

**取值范围：**

```c++
if (10<age<18) //don't do this 编译器不会捕捉这种错误 if((10<age)<17) 不论那种情况，答案都是true
if (age>10 && age<18) // ok
```

&&和||的优先级低于关系运算符，但是！的优先级高于关系运算符。

```c++
if((ch>='a' && ch<='z') || (ch>='A' && ch<='Z' ))
    
if (isalpha(ch));
if (isaspace(ch));
if (isadigit(ch));
if (isapunct(ch));//判断是否为标点符号。
if (isalnum(ch)) ;// 字母或者数字
```

[^]: 判断字符是不是字母字符

```c++
tolower();
toupper();
```

**? : 运算符**

```c++
expression1 ? expression2 : expression3
```

如果表达式1为true； 那么条件表达式的值为表达式2 的值，否则就是表达式3的值。

**switch语句**

其更容易从大型列表中选择;case后如果不接break ，那么他将一直执行下去。

```c++
switch statement:
switch(integer-expression){
    case label1 : statement(s) break;
    case label2 : statement(s) break;
    ...
    default     : statement(s)
}
```

## Chapter 7

创建自己的函数：定义，提供原型和调用。

```c++
typeName functionName(parameterList){
    statements
    return value;
}
```

返回的类型必须是typeName类型或者可以转换为typeName; C++对返回值有一定的限制，不能是数组，可以实任何类型，甚至是可以是结构或者对象，虽然其不能直接返回数组，但是可以把数组作为结构或者对象的组成部分来返回。

C++的变成风格是将main放在最前面，它通常提供了程序的整体结构。

**原型的功能：**

- 编译器正确处理函数的返回值
- 编译器检查使用的参数数目是否正确
- 编译器检查使用的参数类型是否正确

用于接收传递变量的值为形参，传递给函数的值被称为实参。

**函数是处理更复杂的类型的（如数组与结构）关键**

```c++
arr[i] == *(ar+i) // valus in two notations
&arr[i] == ar + i // addresses in two notations
```



```c++
void fillArray(int arr[],int size) //prototype
void fillArray(int arr[size])      // bad
```



**bottom-up programming:**

- 通过设计数据类型和设计适当的函数来处理数据，然后将这些函数组成一个程序。此为自下而上的程序设计。
- 自上而下则是指定模块化设计方案，再研究细节。









# LC242 有效的字母异位词

> 给定两个字符串 *s* 和 *t* ，编写一个函数来判断 *t* 是否是 *s* 的字母异位词。

```c++
class Solution {
public:
    bool isAnagram(string s, string t) {
        int word1[26] = {0};
        int word2[26] = {0};
        int i = s.size();
        int j = t.size();
        if(i!=j) return false;

        for(int m = 0;m<i;m++){
            word1[s[m]-'a']++;
        }
        for(int n = 0;n<j;n++){
            word2[t[n]-'a']++;
        }
        int x = 0;

        for (int x = 0 ; x<26 ;x++)
            if(word1[x]!=word2[x]) return false;
            if(word1[x]==word2[x]){
                i++;
            }
            
        return true;
    }
};
```





