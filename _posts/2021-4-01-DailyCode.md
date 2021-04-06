---
layout:     post
title:      DailyCode
subtitle:   日课
date:       2021-04-01
author:     Lee
header-img: img/code.jpg
catalog: true
tags:
   - leetcode
   - c++
   - Daily
  
---



# C++ Prime Plus

## chapter 9

OOP特性：抽象；封装和数据隐藏；多态；继承；代码的可重用性；

类规范由两部分组成：

- 类声明：以数据成员的方式描述数据，以成员函数的方式描述公有接口。（提供蓝图）
- 类方法定义：描述如何实现类成员函数。（提供细节）

将类定义放在头文件里，将实现的代码放到源文件中。

**实现类的成员函数**

成员函数定义与常规函数定义十分相似，有函数头和函数体，以及返回类型和参数。但是有着两个特殊特征：

- 定义成员函数时，使用作用域解析运算符来标识函数所属的类；
- 类方法可以访问类的private组件

### 类的构造和析构函数

C++的目标之一是让使用类对象就像使用标准类型一样。一般来说，最好是在创建对象的时候就初始化。

构造函数的原型和函数头——没有返回值。

**构造函数：**

不可以将类成员的名称作为构造函数的函数的参数名。

```c++
Stock food = Stock ('world Cabbage',250,1.25)
  
Stock garment("Baidu",50,2.5)
Stock garment = Stock("Baidu",50,2.5)
```

构造函数被用来创建对象，而不能通过对象来调用。

**默认构造函数：**

如果没有提供任何构造函数，则C++将自动提供默认构造函数。不做任何工作，不初始化任何对象。

**析构函数：**

用构造函数创建对象后，程序负责跟踪该对象，直到其过期为止。

```c++
Stock::~Stock(){
    cout<<"Bye,"<<company<<"!\n"
}
```

由编译器决定什么时候调用析构函数。如果创建的是静态存储类对象，析构函数将在程序结束时自动调用。

如果创建的是自动存储类对象，则析构函数将在程序执行完代码块时自动被调用。

如果是用new创建，则驻留在栈内存或自由存储区中，使用delete来释放内存。

### this指针

有时候方法会要嗲用到两个对象，这种情况下就要使用C++的this指针。

### 类作用域

调用公有成员函数，必须通过对象；

定义成员函数时，必须使用作用域解析运算符。

直接成员运算符(.) 间接成员运算符(->，与一个指向对象的指针一起使用) 作用域解析运算符(::)



# LeetCode 

## 19 删除链表的倒数第n个节点

> 给你一个链表，删除链表的倒数第 `n` 个结点，并且返回链表的头结点。



```c++
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        ListNode* p = head;
        int length = 0;
        while(p!=nullptr){
            length++;
            p = p->next;
        }

        if (length == n ){
            return head->next; 
        }
        p = head;

        for(int i =0 ; i<length-1-n;i++){
            p = p->next;
        }
        p->next = p->next->next;
        
        return head;
    }
};
```





