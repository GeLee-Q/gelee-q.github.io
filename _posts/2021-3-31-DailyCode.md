---
layout:     post
title:      DailyCode
subtitle:   日课
date:       2021-03-31
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

### 名称空间

namespace 提供一个声明名称得空间，不会与另一个名称空间的相同名称发生冲突，同时允许程序的其他部分使用该名称空间中声明的东西。

可以使用**作用域解析运算符**：：来访问给定名称空间中的名称。

using声明使特定的标识符可用；

using编译指令将使整个名称空间使用；

```c++
using Jill::fetch //a using declaration
```

```c++
using namespace Jack // make all the names in Jack available 
```

```c++
#include <iostream> //place names in namespcae std
using namespace std; // make names avaliable globally
```

> C++鼓励程序员在开发程序时使用多个文件。一种有效的组织策略是，使用头文件来定义用户类型，为操纵用户类型的函数提供函数原型；并将函数定义放在一个独立的源代码文件中。头文件和源代码文件一起定义和实现了用户定义的类型及其使用方式。最后，将main( )和其他使用这些函数的函数放在第三个文件中。
>
> C++的存储方案决定了变量保留在内存中的时间（储存持续性）以及程序的哪一部分可以访问它（作用域和链接性）。自动变量是在代码块（如函数体或函数体中的代码块）中定义的变量，仅当程序执行到包含定义的代码块时，它们才存在，并且可见。自动变量可以通过使用存储类型说明符register或根本不使用说明符来声明，没有使用说明符时，变量将默认为自动的。register说明符提示编译器，该变量的使用频率很高，但C++11摒弃了这种用法。
>
> 静态变量在整个程序执行期间都存在。对于在函数外面定义的变量，其所属文件中位于该变量的定义后面的所有函数都可以使用它（文件作用域），并可在程序的其他文件中使用（外部链接性）。另一个文件要使用这种变量，必须使用extern关键字来声明它。对于文件间共享的变量，应在一个文件中包含其定义声明（无需使用extern，但如果同时进行初始化，也可使用它），并在其他文件中包含引用声明（使用extern且不初始化）。在函数的外面使用关键字static定义的变量的作用域为整个文件，但是不能用于其他文件（内部链接性）。在代码块中使用关键字static定义的变量被限制在该代码块内（局部作用域、无链接性），但在整个程序执行期间，它都一直存在并且保持原值。
>
> 在默认情况下，C++函数的链接性为外部，因此可在文件间共享；但使用关键字static限定的函数的链接性为内部的，被限制在定义它的文件中。
>
> 动态内存分配和释放是使用new和delete进行的，它使用自由存储区或堆来存储数据。调用new占用内存，而调用delete释放内存。程序使用指针来跟踪这些内存单元。
>
> 名称空间允许定义一个可在其中声明标识符的命名区域。这样做的目的是减少名称冲突，尤其当程序非常大，并使用多个厂商的代码时。可以通过使用作用域解析运算符、using声明或using编译指令，来使名称空间中的标识符可用。