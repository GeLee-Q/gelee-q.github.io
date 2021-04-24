---
layout:     post
title:      DailyCode
subtitle:   日课
date:       2021-04-24
author:     Lee
header-img: img/code.jpg
catalog: true
tags:
   - leetcode
   - c++
   - Daily
  
---

# 链表题 回文链表

思路：

- 快慢指针，当快指针指向最后的节点，慢指针指向中间的节点。
- 然后翻转链表，把快指针指向头节点。然后比较即可。

链表反转：

- pre指向前一个，cur表示当前节点，temp表示下一个节点。
- 将cur->next指向pre，然后讲cur复制给pre；接着吧temp给cur;

 方法图解：https://zhuanlan.zhihu.com/p/105749135

```c++
public:
    ListNode* reverseList(ListNode* head) {
			ListNode* pre=nullptr; *cur = head;
      while(cur!=nullptr){
        ListNode* temp = cur->next;
        cur->next = pre;
        pre = cur;
        cur = temp;
      }
      return pre
    }
		bool isPalindrome(ListNode* head){
      LisNode* slow = head; *fast = head;
      while(fast!=nullptr && fast->next!=nullptr){
        slow=slow->next;
        fast=fast->next->next;
      }
      
      if(fast!=nullptr){
        slow = slow->next;
      }
      
      slow = reverseList(slow);
      fast = head;
      
      while(slow!=nullptr){
        if(fast->val!=slow->val){
          return false;
        }
        slow = slow->next;
        fast = fast->next;
       return true;
      }
     
    }
	
```

