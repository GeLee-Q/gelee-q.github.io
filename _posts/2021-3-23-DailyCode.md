---
layout:     post
title:      DailyCode
subtitle:   日课
date:       2021-03-23
author:     Lee
header-img: img/code.jpg
catalog: true
tags:
   - leetcode
   - c++
   - Daily
---

# C++ Prime Plus 

## Chapter 5

**递增运算符和递减运算符：**

- 对操作数的影响是一样的，但是影响的时间不同。

```c++
int x = 5;	 // change x, then assign to y 
int y = ++x; // y = 6 , x = 6

int x = 5;	 // assign to y , then change x
int y = x++; // y = 5 , x = 6
```

++ 运算符的优先级比*的优先级高

```c++
(*pt)++; // increment pointed-to value
*pt++;   // 改了地址
```

**组合操作符：**

| 操作符 | 作用（L 左操作数；R右操作数） |
| ------ | ----------------------------- |
| %=     | 将L%R 赋值给L                 |

```c++
//for 和 while 本质上是相同的。
for(init-expression; test-expression; update-expression){
    statement(s);
}

init-expression;
while(test-expression){
    statement(s);
    update-expression;
}
```

```c++
do{
    body;
}while(test-expression);
```

**基于范围的for循环：**

```c++
double price[5] = {1.11, 2.22, 3.33, 4.44, 5.55};
for (double x : price)
    cout << x << std::endl;
```

**嵌套的for循环：**

```c++
for (int row = 0; row < 4; row++){
    for(int col = 0 ; col < 5; col++){
        cout << maxtemps[row][col]<< "\t";
        cout << endl;
    }
}
```



## Chapter 6