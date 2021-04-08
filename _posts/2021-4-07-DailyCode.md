---
layout:     post
title:      DailyCode
subtitle:   日课
date:       2021-04-07
author:     Lee
header-img: img/code.jpg
catalog: true
tags:
   - leetcode
   - c++
   - Daily
  
---

> 桃李春风一杯酒 江湖夜雨十年灯

# C++ Prime Plus

## Chapter11 使用类

### 运算符重载

限制：

- 重载后至少有一个操作数是用户定义的类型，这将防止用户为标准类型重载运算符。
- 使用运算符时不能违反运算符原来的句法规则。
- 不能创造新的运算符。
- 不能重载部分运算符。

### 友元

- 友元类
- 友元函数
- 友元成员函数

通过让函数成为类的友元，可以赋予该函数与类的成员函数相同的访问权限。

在原型声明前加上关键字friend；在定义中不要使用关键字friend；



## 链表

```c++
#include <iostream>
using namespace std;

class List{
public:
    List(){create_List();}
    ~List(){clear();}
    //创建头节点
    void creat_List();
    //插入节点
    void insert_pos(const int& d, const int& d1);
    //删除指定数据的节点
    void erase(const int& d);
    //修改指定的数据
    void updata(const int& d,const int& d1);
    //反转列表
    void reverse();
private:
    //节点结构
    struct Node{
        int data;
        Node * next;
        Node(const int& d):data(d),next(NUll){}
    }
    
    Node * head;//头节点
    //清理链表函数
    void clear(){
        Node * p = head;
        while(p){
            Node * q = p->next;
            delete p;
            p = q;
        }
    }
    
    //查找操作
    Node * find(const int & d){
        Node * p = head;
        for(;p;p=p->next){
            if(p->next->data==d)
                break;
        }
        return p;
    }
};

void List::create_List(){
    head = new Node(0);
}

void List::insert(const int& d){
    Node * p = new Node(d);
    p->next = head ->next;
    head->next = p;
}

void List::insert_pos(const int&d , const int& d1){
    Node* p = find(d);
    Node* q = new Node(d1);
    q->next = p->next;
    p->next = q;
}

void List::erase(const int& d){
    Node * p = find(d);
    Node * q = p->next;
    p->next = p->next->next;
    delete q;
}

void List::update(const int& d, const int & d1){
    Node * p = find(d);
    p->next->data = d1;
}
    

void List::reverse(){
    Node * p = head->next;
    Node * q = head->next->next;
    Node * m = head->next->next->next;
    p->next = NULL;
    //判断m是否为空来判断 以此逆序每一个节点
    while(m){
        q->next = q;
        p = q;
        q = m;
        m = m->next;
    }
    q->next = p;
    head->next = q;
    
    
}
	
```



链表反转，首先要保存修改节点的下一个节点；同时要保存上一个节点，因为next域即将修改保存到这个节点。因此定义三个指针，分别指向当前遍历的节点，前一个结点，后一个节点。



```c++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        ListNode * pre = nullptr,*next;
        while(head){
          next= head->next;
          head->next = pre;
          pre= head, head = next;
        }
        return pre;
     
    }
};
```























