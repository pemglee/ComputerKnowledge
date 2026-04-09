---
title: Java学习
markmap:
  colorFreezeLevel: 24
---

## 概述

+ 一些概念

  + JDK -- Java Development Kit
    + java.exe, 启动JVM
    + javac.exe, Java编译器，把 .java文件编译成 .class (java字节码文件)
    + .jar, 把一组 .class文件打包成 .jar文件，用于发布
    + javadoc.exe, 从 .java文件中自动提取注释并生成帮助文档
    + jdb.exe, Java调试器，用于开发阶段的运行调试

  + JRE -- Java Runtime Environment
  + JVM -- Java Virtual Machine
  + EE -- Enterprise Edition
    + Java SE
    + API+ 扩展库
  + SE -- Standard Edition
    + JVM
    + 标准库
  + ME -- Micro Edition
  + OpenJDK
  + Hotspot
  + JSR -- Java Specification Request
  + JCP -- Java Community Process

+ 关键字

  + [表格]

    | 类别    | 关键字 | 说明   |
    | :------ | :--------- | :---- |
    | 访问控制 | private    | 私有类成员  |
    |         | protected  | 受保护类成员 |
    |         | public     | 公共类成员  |
    |         | default    | 默认类成员  |
    | 修饰符   | abstract   | 声明抽象    |
    |         | class      | 类         |
    |         | extends    | 扩充、继承  |
    |         | final      | 最终值、不可变 |
    |         | implements | 实现(接口) |
    |         | interface  | 接口      |
    |         | native     | 本地、原生 |
    |         | new        | 创建      |
    |         | static     | 静态      |
    |         | strictfp   | 严格浮点、精确浮点 |
    |         | synchronized | 线程、同步 |
    |         | transient  | 短暂的 |
    |         | volatile   | 易失  |
    | 程序控制 | break      | 终止循环 |
    |         | case       | switch选择 |
    |         | continue   | 继续处理   |
    |         | do         | 运行      |
    |         | else       | 否则      |
    |         | for        | 循环      |
    |         | if         | 如果      |
    |         | instanceof | 实例      |
    |         | return     | 返回      |
    |         | switch     | 选择      |
    |         | while      | 循环      |
    | 错误处理 | assert     | 断言表达式  |
    |         | catch      | 捕捉异常   |
    |         | finally    | 强制执行   |
    |         | throw      | 抛出异常对象 |
    |         | throws     | 声明可能抛出的异常 |
    |         | try        | 尝试运行   |
    | 包相关   | import     | 导入      |
    |         | package    | 包        |
    | 基本类型 | boolean    | 布尔类型   |
    |         | byte       | 字节类型   |
    |         | char       | 字符类型   |
    |         | double     | 双精度浮点 |
    |         | float      | 单精度浮点 |
    |         | int        | 整型      |
    |         | long       | 长整型    |
    |         | short      | 短整型    |
    | 变量引用 | super      | 父类、超类 |
    |         | this       | 本类      |
    |         | void       | 无返回值   |
    | 保留关键字 | goto      | 跳转，禁用 |
    |          | const     | 常量，禁用 |

  + [说明]

    + null，字面常量，非关键字
    + true & false，字面常量，非关键字

+ JVM  

  + 内存模型，  
    运行时数据区

    + 线程共享区

      + 方法区 Method Area
        + [功能] 存储类信息、常量、静态变量、JIT编译后的代码
        + [说明]
          + 实现
            + JDK 1.7: 永久代(PermGen, Permanent Generation)
              Java启动参数 `-XX:MaxPermSize`
            + JDK 1.8: 元空间(Metaspace)，使用本地内存(不再受JVM堆的限制)
              + 运行时常量池，存放类、方法、字段的符号引用，及字面量(如，String.intem()的字)
          + Exceptions
            + OutOfMemoryError  
              元空间溢出，抛出 java.lang.OutOfMemoryError: Java heap space --> PermGen

      + 堆 Heap

        + [功能] 存放所有的对象实例和数组，均为 _引用类型_
        + [说明]
          + Java启动参数 `-Xmx`
          + 垃圾回收(GC, Garbage Collector)的主要区域
          + 新生代 + 老年代
            + 新生代 Young Generation
              + Eden区 （默认占比 80%）
              + Survivor From区（默认占比 10%）
              + Survivor To区（默认占比 10%）
            + 老年代 Old Generation
              长期存活的对象
          + Exceptions
            + OutOfMemoryError  
              + 当堆无法分配内存时，抛出 java.lang.OutOfMemoryError: Java heap space
                + 超出预期的访问量或数据量
                + 内存泄漏 Memory Leak
              + 垃圾回收错误，抛出 java.lang.OutOfMemoryError: GC overhead limit exceeded

    + 线程私有区，
      每个线程独有

      + 程序计数器 PC Register, Program Counter Register
        唯一不会发生 OutOfMemoryError的区域

        + [功能] 存储下一条待执行指令的内存地址
        + [说明] 
          + 线程切换后，能恢复到正确执行的位置

      + 虚拟机栈 VM Stack
        + [功能] 存储 方法调用的栈帧
        + [说明]
          + 栈帧结构 Stack Frames
            + 局部变量表 Local Variable Array，存储方法参数和局部变量
            + 操作数栈 Operand Stack，执行字节码指令的工作区，如 加、减、乘、除， 策略为先进后出(FILO)/后进先出(LIFO)
            + 动态链接 Dynamic Linking，指向方法区(线程共享区>方法区)中该方法的符号引用
              + 指向运行时常量池中该方法的符号引用
              + 支持方法的多态，即晚期绑定
            + 返回地址 Return Address，方法退出后应回到的指令位置
              + 记录方法退出时的字节码指令地址
              + 返回时
                + 正常，调用者的PC计数器值
                + 异常，异常处理器表的地址
          + Exceptions
            + StackOverflowError, 栈深度超过限制，如无限递归
            + OutOfMemoryError, 扩展栈时，无法申请到足够空间

      + 本地方法栈 Native Stack
        + [功能] 为JVM调用Native方法(如 C/C++ 代码)服务
        + [说明]
          + 与"VM Stack"类似，但服务于"Native"方法
          + Exceptions，与"VM Stack"类似
            + StackOverflowError
            + OutOfMemoryError

    + Heap vs Stack

      + 对比
        + [表格]

          |        | JVM Stack | JVM Heap |
          | :----- | :-------- | :------- |
          | 共享性质 | 线程私有区域 | 线程共享区域 |
          | 创建时间 | 线程创建时，会分配一个独立的栈 | JVM启动时，整个JVM只有一个堆 |
          | 存储内容 | 存储方法执行时的栈帧 | 对象实例 和 数组 |
          | 生命周期 | 自动管理，与作用域绑定，不涉及GC | 由GC管理 |
          | 线程安全 | 天然线程安全 | 非线程安全 |
          | 内存碎片 | 无内存碎片 | 存在内存碎片 |
          | 错误异常 | StackOverflowError + OutOfMemoryError | OutOfMemoryError |

      + 线程安全问题 
        + [说明] 
          堆是共享区域，多个线程可以同时访问(读+写)一个堆上的数据  
          手动使用 synchronized, volatile, lock 等机制来保证并发安全(可见性、原子性、有序性)

  + Java启动参数

+ 数据类型
  Java是强类型语言

  + 基本数据类型
    + byte, 8 bits / 1 Byte, -128 ~ 127, integer
    + short, 16 bits / 2 Bytes, -32768 ~ 32767, integer
    + int, 32 bits / 4 Bytes, -2147483648 ~ 2147483647, integer
    + long, 64 bits / 8 Bytes, -9223372036854775808 ~ 9223372036854775807, interger
    + float, 32 bits / 4 Bytes, 
    + double, 64 bits / 8 Bytes, 
    + char, 16 bits / 2 Bytes,
    + boolean,

  + 引用数据类型
    + class
    + interface
    + array

  + 类型转换

    + 自动类型提升

    + 强制类型转换

+ Operator

  + 算术运算符

  + 赋值运算符

  + 比较运算符

  + 逻辑运算/布尔运算
    + 位运算符

    + 与 `&&`(短路与), `&`
    + 或 `||`(短路或), `|`

  + 三元运算符

  + 运算优先级
    1. `()`
    2. 一元运算符: `!`, `~`, `++`, `--`
    3. 乘除运算符: `*`, `/`, `%`
    4. 加减运算符: `+`, `-`
    5. 移位运算符: `<<`, `>>`, `>>>`

    7. 比较运算符: `>`, `>=`, `<`, `<=`, `instanceof`
    8. 相等运算符: `==`, `!=`
    9. 位与运算符: `&`
    10. 位异或运算符: `^`
    11. 位或运算符: `|`
    12. 逻辑与运算符: `&`, `&&`
    13. 逻辑或运算符: `|`, `||`
    14. 条件运算符: `? : `
    15. 赋值运算符: `+=`, `-=`, `*=`, `/=`

+ Control

  + 顺序结构

  + 分支控制 / 条件控制 / 选择结构

    + `if {}`, `if {} else {}`, `if {} elseif {} else {}`

    + `swith () {case :...}`

  + 循环结构

    + for

    + foreach

    + while

    + do while
  
    + 中断终止
  
      + break
  
      + continue


+ OOP -- Object-Oriented Programming
  + 封装 Encapsulation
    将数据和可对其操作的方法绑定在一起
  + 继承 Inheritance

    + 子类可不可以重写父类的**静态**方法  
      不可以  
      核心在于.class文件(二进制)。静态方法不是对象调用。  
      @Override不可以  
      @Shadow可以  
  + 多态 Polymorphism
    允许不同类的对象对同一消息做出不同相应
  + 抽象 Abstraction
    + 接口
  + 类 Class
  + 对象 Object
  + 方法 Method
  + 重载 Overload/Override

+ Java类库  
  + 数学、计算

  + 字符、字符串

  + 集合
    + java.util.ArrayList
    + java.util.LinkedList
    + java.util.HashMap
    + java.util.Vector
    + java.util.HashSet
    + java.util.Scanner
    + java.util.regex.Pattern
    + java.util.regex.Macher

  + IO/NIO
    + java.io.File
    + java.io.InputStream
    + java.io.OutputStream
    + java.nio.file.Files

  + 多线程
    + java.lang.Thread
    + java.util.concurrent.ExecutorService

  + 日期、时间
    + java.time.LocalDate
    + java.time.LocalDateTime
    + java.time.ZonedDateTime
    + java.util.Date
    + java.text.SimpleDateFormat
    + java.util.Calendar
    + java.util.GregorianCalendar
    + java.time.Instant
    + java.time.ChronoUnit
    + java.time.Period
    + java.time.Duration

  + 网络编程
    + java.net.URL
    + java.net.Socket

+ Java第三方库

+ Java应用框架

+ 分布式、微服务

  + C(Consistency强一致性) A(Availability可用性) P(Parition tolerance分区容错性)
    最多智能满足上述三项中的两项

  + BA(Base Avalibale基本可用) S(Soft State软状态/中间状态) E(Eventually Consistent最终一致性)
    AP的拓展和工程化，不追求实时强一致性，但保证最终结果正确，且核心流程永远可用  
    时间窗口  

  + ACID
    追求强一致性、强隔离、事务边界清晰

+ 数据库 & 持久化框架

+ 异常处理

  + try catch

    + try-catch会影响性能吗
      + 未出异常时，不会影响性能
      + 出现异常，
        增加异常状态判断，增加异常栈建立，...，会影响性能
        仍需对可预测的异常进行return处理，而非抛出通用异常  


## 专题

+ File， Stream， IO

+ 集合 & 泛型

  + 集合
    + [说明]
      Java集合框架主要是由 Collection 和 Map 两个接口派生而来
  
    + List
    + Set
    + Queue
    + ArrayList
      动态数组。查询效率高，插入和删除效率低
    + LinkedList
      基于双向链表。插入和删除效率高，查询效率低
    + HashMap
      基于Hash表实现。透过哈希值快速定位键值，具有较高的查找效率。非线程安全
    + TreeMap
      基于红黑树实现。能够对键进行排序
    + ConcurrentHashMap
      线程安全的哈希表，采用分段锁机制
    + HashSet
    + TreeSet

  + 泛型

    + 泛型类

    + 泛型接口

    + 泛型方法

    + 泛型通配符

      + 无界通配符
      + 上界通配符
      + 下届通配符

+ 多线程 & 并发

  + 继承 Thread类

  + 实现 Runnable接口

  + 线程池

    + 固定大小线程池

    + 单线程线程池

    + 缓存栈线程池

+ AOP 面向切面编程  

  + 业务类

  + 切面类

  + 配置类

+ Spring

  + Spring Boot

  + Spring Cloud



## reference doc

+ [知乎 -- 划重点，Java入门指南](https://zhuanlan.zhihu.com/p/24611339952)