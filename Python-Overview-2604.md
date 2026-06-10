---
title: Python学习
markmap:
  colorFreezeLevel: 24
---

# Python 学习

## Overview

### 相关概念

### Python 解释器 interpreter

+ 解释器，代码与机器的计算机硬件之间的**软件逻辑层**

+ Python环境
  + Python解释器
  + 支持库

+ Python运行
  + 将 每一条 源代码 编译成 字节码
  + PVM(Python Virtual Machine)
    + Psyco 实时编译器 (![question](./images/question-trans-small.png)已停止维护)
    + PyPy 实时编译器
    + Shedskin C++转换器

+ 冻结二进制文件
  + ![question](./images/question-trans-small.png)第三方工具
  + 字节码+PVM混合在一起的独立组件

+ Python 种类

  + 综述

    + 图示

      + [diagram]  
        ![Python Code Interpreter](./images2/Python-Code.drawio.svg)

    + 字节码 vs. 机器码

  + CPython 官方标准实现
    + 类型：C语言解释器
    + 特点
      + 源代码 ==> 字节码，编译器逐行运行
      + 全局解释锁(GIL)限制多线程并行性能

  + IPython
  
  + PyPy 高性能JIT实现
    + 类型：即时编译解释器
    + 特点
      + JIT(Just-In-Time),
      + 动态优化代码
      + 兼容**大部分**CPython和库
      + 默认支持 无栈(Stackless)模式，适合高并发
      + 场景： 计算密集型任务(如，科学计算， 长时间运行)

  + Jython(曾用名：JPython) Java平台
    + 类型：JVM解释器
    + 特点
      + 源代码 ==> Java字节码，运行在JVM上
      + 可直接调用Java类库，实现Python与Java的互操作
      + 无GIL，但性能通常低于CPython
      + 场景： Java生态集成

  + IronPython

### Python 环境

#### summary

+ 安装解释器

+ 运行
  + 终端，PATH含有python可执行文件的路径
    + 适用于小规模测试
  + 直接代码文件
    + "python 代码文件"
  + IDE

+ 配置说明

#### 虚拟环境

##### venv

+ 说明

  + 目录结构示例 windows

    + 项目名称
      + [D] .idea
      + [D] .venv
        + [D] Include
          + [D] site
            + [D] python*version*
              + [D] pygame

        + [D] Lib
          + [D]site-packages
            + [D] __pycache__
            + [D] pip
            + [D] pip-26.1.dist-info
            + [D] pygame
            + [D] pygame-2.6.1.dist-info
            + [f] _virtualenv.pth
            + [f] _virtualenv.py

        + [D] Scripts
          + [f] activate
          + [f] activate.bat
          + [f] activate.fish
          + [f] activate.nu
          + [f] activate.ps1
          + [f] activate_this.py
          + [f] deactivate.bat
          + [f] pip.exe
          + [f] pip3.13.exe
          + [f] pip3.exe
          + [f] pydoc.bat
          + [f] python.exe
          + [f] python3
          + [f] python3.exe
          + [f] pythonw.exe
          + [f] venvalauncher.exe

+ 操作

  + 创建

    `python -m venv 虚拟环境名`

  + 激活

    + windows 
      `虚拟环境名\Scripts\activate`

    + Linux
      `source 虚拟环境名/bin/activate`

  + 安装包

    `pip install 包名`

  + 退出

    `deactivate`

  + 删除

    删除文件夹/目录即可

##### anaconda

+ conda操作

  + 检索环境，罗列所有环境

    `conda env list`

  + 创建

    + `conda create --name 虚拟环境名 python=版本`

    + `conda create --prefix 环境路径/虚拟环境名 python=版本`  **慎用**

  + 激活

    `conda activate 虚拟环境名`

  + 退出

    `conda deactivate`

  + 删除

    `conda remove --name 虚拟环境名 --all`

##### pipenv

##### virtualenv

#### 开发环境

#### 生产环境

## 基础

### 关键字

+ 列表

  + "False"

  + "None"

  + "True"

  + "and"

  + "as"

  + "assert"

  + "async"

  + "await"

  + "break"

  + "class"

  + "continue"

  + "def"

  + "del"

  + "elif"

  + "else"

  + "except"

  + "finally"

  + "for"

  + "from"

  + "global"

  + "if"

  + "import"

  + "in"

  + "is"

  + "lambda"

  + "nonlocal"

  + "not"

  + "or"

  + "pass"

  + "raise"

  + "return"

  + "try"

  + "while"

  + "with"

  + "yield"

+ Soft keywords

  + [官方文档 Python3.13](https://docs.python.org/3.13/reference/lexical_analysis.html#other-tokens)

    + [quote]

      ```text
      Added in version 3.10.
      
      Some identifiers are only reserved under specific contexts. These are known as soft  keywords. The identifiers match, case, type and _ can syntactically act as keywords in certain contexts, but this distinction is done at the parser level, not when tokenizing.
      
      As soft keywords, their use in the grammar is possible while still preserving compatibility with existing code that uses these names as identifier names.
      
      match, case, and _ are used in the match statement. type is used in the type statement.
      
      Changed in version 3.12: type is now a soft keyword.
      ```

  + [百度百科](https://baike.baidu.com/item/%E8%BD%AF%E5%85%B3%E9%94%AE%E5%AD%97/61987673)

    + [quote]

      ```text
      仅在特定上下文中被保留的标志符
      软关键字（Soft Keywords）是编程语言中仅在特定上下文中被保留的标识符，属于计算机语言学科范畴。这类标识符在Python、Scala等语言中以保留语义的方式存在，但其保留性仅限特定语法环境而非全局生效。
      在Python3.10.7版本中，match、case和_等软关键字仅在模式匹配语句上下文具备关键字语义。这种区分通过解析器层级实现，而非在形符化阶段处理，从而保持与使用这些标识符作为变量名的既有代码的兼容性      
      ```

### 常量、变量

#### 说明

+ 标识符是常量、变量、函数、属性、类、模块等可以由程序员指定名称的代码元素
  即，被标识的内存

+ 为一个变量赋值的同时就声明了该变量，且指定了数据类型
  Python中只能通过赋值的方式创建变量，无法提前声明或定义

  + 示例

    + [operating]

      ```python
      >>> a=10
      >>> type(a)
      <class 'int'>
      >>>
      ```

+ 代码是由关键字、标识符、表达式和语句构成
  一行代码就是一条**语句**

+ 一个模块就是一个文件
  模块是保存代码的最小单元

+ 字面量，字面值常量(literal)讨论
  + 在代码中，规定的值
  + 不是指不可变的对象和变量，不同于 C/C++ 中的 const 概念

    + 示例

      + [operating]

        ```python
        >>> LITERAL_A = 255
        >>> type(LITERAL_A)
        <class 'int'>
        >>>
        ```

#### 命名规则、约定

+ 大小写敏感
+ **只能** 字母、数字、下划线
+ **禁止** 数字 开始
+ **禁止** 关键字 内置函数名
+ _建议_ 具有描述性
+ 变量名 要有唯一性

+ 推荐规则

  + 驼峰
    + "CamelCase"
    + 类名, 接口名, 组件名 "UpperCamelCase" / "PascalCase"
    + 变量, 属性, 方法, 函数 "lowerCamelCase"

  + 蛇形命名 
    + "snake_case"

+ 举例说明

  | 变量名 | 是否正确 | 解释 |
  | :---- | :---: | :---- |
  | name@ | 否    |       |
  | a_    | 可    |       |
  | _     | 可    | 不建议，无描述性      |
  | 3n    | 否    |       |
  | 2$t   | 否    |       |
  | __    | 可    | 不建议，无描述性      | 

+ 约定
  + snack_case, 普通变量名
  + UPPER_SNAKE_CASE, 常量名
  + UPPERCASE, 常量名
  + _leading_under_score, 受保护的属性和方法
    + "_" 较强
    + "__" 更强
  + trailing_under_score_, 类关键字，避免与真正的关键字冲突
  + CamelCase, 类及其成员
    + UpperCamelCase, 类名 & 属性名
    + lowerCamelCase, 方法


#### 变量是对象

+ 说明
  在Python中，变量总是一个指向对象的指针，而不是可改变的内存区域的标签；
  给一个变量赋一个新值，并不是替换了原始对象，而是让这个变量去引用完全不同的一个对象。
  
+ 变量创建
  当代码第一次给它赋值时创建了它。
  之后的赋值 将会 改变 已创建的变量名的**值**

+ 变量类型
  变量永远不会有任何的和它关联信息或约束。
  类型的概念存在于对象中而不是变量名
  变量原本是通用的，只是在一个特定的时间点，简单引用了一个特定的对象而已

+ 变量使用
  当变量出现在表达式中时，它会马上被当前引用的对象所替代，无论这个对象时什么类型。

+ 说明 2

  + 变量名指向的是数据/对象，而非变量。
  
  + 示例 1

    + [operating]

      ```python
      >>> age1 = 18
      >>> age2 = age1
      >>> age1 = 20
      >>> age3 = age2
      >>> print(age1, age2, age3)
      20 18 18
      >>>
      ```

      + 说明
        + _创建一个对象来代表/存储值18_
        + _创建一个变量age1_
        + age1 指向一块儿 值为18 的内存，即age1保存了内存地址
        + age2 指向age1同样地址的内存
        + age1 指向了另一块儿新建的 值为20 的内存，age1保存的内存地址发生了变化，但age2未变
        + age3 指向了age2同样地址的内存
        + 分别打印三个变量指向内存中的值

  + 示例 2

    + [operating]

      ```python
      >>> a = [1,2,3,4]
      >>> b = a
      >>> c = a[:]  # copy a's value to c, just for list
      >>> b[2]=9
      >>> print(a)
      [1, 2, 9, 4]
      >>> print(b)
      [1, 2, 9, 4]
      >>> print(c)
      [1, 2, 3, 4]
      ```


### 数据类型 i.e. 内置对象

#### 类型图示

+ 图示
  + [diagram]  
    ![Python Object Organization](./images2/python-TypeOrganization.svg)

#### 数字

+ int 整数

  + 示例

    + [operating]

      ```python
      >>> a=10
      >>> type(a)
      <class 'int'>
      >>> 0b11100
      28
      >>> 0o34
      28
      >>> 0x1c
      28
      >>>
      ```

+ float 浮点数
  + 说明
    + 浮点数是不精确的

      + [operating]

        ```python
        >>> f1 =10.
        >>> print(type(f1))
        <class 'float'>
        >>>
        >>> print(0.1 + 0.2)
        0.30000000000000004
        >>>
        ```

+ complex 复数

  + 说明

    + [operating]

      ```python
      >>> a = 10 + 12j
      >>> type(a)
      <class 'complex'>
      >>>
      ```

+ boolean `True` / `False`
  + 说明
    + 非零数字、非空对象 均为True
    + 数0、空对象、特殊对象None 均为False
    + 比较 和 相等测试 会递归地应用在数据结构中
    + 比较 和 相等测试 会返回 True 或 False
    + 布尔 and 和 or 运算符会返回 True 或 False的操作对象

  + 示例
    + [operating]
  
      ```python
      >>> bool(0.0)
      False
      >>> bool(0.1)
      True
      >>> bool(0)
      False
      >>> bool(2)
      True
      >>> bool(1)
      True
      >>> bool('')
      False
      >>> bool(' ')
      True
      >>> bool([])
      False
      >>> bool({})
      False
      >>> bool(())
      False
      >>>
      ```

+ 算术运算符

  + `+`
  + `-`
  + `*`
  + `/`
  + `//`, 整除
  + `**`
  + `%`, 取余，模运算

+ 类型转换
  + 显式转换
  + 隐式转换

+ 类型特定方法

#### **str** 字符串

+ 字符序列, Sequence of characters
+ 双引号定义, string with double quotes, `""`
+ 单引号定义，string with single quotes, `''`
+ 多行定义，Multiline strings

    ```python
    """ 
    """
    ```

+ 字符串拼接, string concatenation
  + `+`
+ 字符串重复, string Multiplication
  + `*`
+ 转义字符, Escape Sequence Characters
  + `\`
  + `\\`
  + `\n`, 新行
  + `\b`, 回退
+ 原文定义，raw string
  + 说明
    不再处理`\`而进行转义
  + 示例
    + [operating]

      ```cmd
      [edgar@ThinkPadT14P-23 chapter02]$ python
      Python 3.13.13 (main, Apr 26 2026, 22:45:29) [GCC 8.5.0 20210514 (Red Hat 8.5.0-28)] on linux
      Type "help", "copyright", "credits" or "license" for more information.
      >>> print(r"\n\\\'")
      \n\\\'
      >>>
      ```

+ 序列操作
  + 图示
    + [diagram]  
      ![Python String Sequence](./images/python-string-small.jpg)
  + 正向索引
    + 示例
      + [operating]

        ```cmd
        >>> S="HELLO!"
        >>> len(S)
        6
        >>> S[0]
        'H'
        >>> S[4]
        'O'
        >>>          
        ```

  + 反向索引

    + 示例
      + [operating]

        ```cmd
        >>> S="HELLO!"
        >>> len(S)
        6
        >>> S[-1]
        '!'
        >>> S[len(S)-1]
        '!'
        >>> S[-5]
        'E'
        >>>
        ```

  + 分片 slice，**半闭半开区间**
    + 示例
      + [operating]

        ```cmd
        >>> S="HELLO!"
        >>> len(S)
        6
        >>> S[2:4]
        'LL'
        >>> S[-5:-2]
        'ELL'
        >>> S[2:]
        'LLO!'
        >>> S[:-2]
        'HELL'
        >>> S[:]
        'HELLO!'
        >>>
        ```

+ 不可改变性，但可以重新赋值
  + 示例
    + [operating]

      ```cmd
      >>> S="HELLO!"
      >>> len(S)
      6
      >>> S[:2]
      'HE'
      >>> S=S[:2]+"l"+S[3:]
      >>> print(S)
      HElLO!
      >>>
      ```

+ 类型特定方法
  + .find()
  + .replace()
  + .split()
  + .upper()
  + .isalpha()
  + .rstrip()
  + 格式化
  + 模式匹配

+ `print()` 函数

#### list, 列表

+ 序列 Sequence、可变
+ `[]`

#### tuple, 元组

+ 序列 Sequence、不可变
+ `()`

#### dict, 字典

+ 映射 Map（无序）、唯一
+ `{key1:value1, key2:value2, ...}`

#### set, 集合

+ 集合 Set（无序）、唯一
+ `{}` / `set()`

#### file, 文件

#### 其他类型

#### 编程单元类型

+ 常量/常量表达式
+ 表达式
+ 函数
+ 模块 / 文件
+ 类

#### 与实现相关的类型

+ 编译的代码堆栈跟踪

### 运算, 表达式

#### 数学计算

#### 字符串处理

#### 比较运算

+ `==` 相等 / 等于
+ `!=` 不等于
+ `>` 大于
+ `>=` 大于等于 / 不小于
+ `<` 小于
+ `<=` 小于等于 / 不大于

#### 逻辑运算

+ `not`
+ `and`
+ `or`

+ 说明
  Python逻辑运算采用了短路设计

  + 示例

    + [operating]

      ```python
      >>> a = 1
      >>> b = 0
      >>> def f1():
      ...     print('function 1')
      ...     return True
      ...
      >>> ( a > b ) or f1()
      True
      >>> ( a < b ) or f1()
      function 1
      True
      >>> ( a < 1 ) and f1()
      False
      >>> ( a > 1 ) and f1()
      False
      >>>
      ```


#### 位运算

+ `~` 位反
  + 说明
    + [diagram]  
      ![Python Bit Compl](./images2/algebra-Compl.svg)
+ `&` 位与
+ `|` 位或
+ `^` 位异或
+ `>>` 右移

  + 说明
    高位 用 符号位 补位
+ `<<` 左移
  + 说明
    低位 用 0 补位

#### 赋值运算符

+ `=`

  + 示例

    + [operating]

      ```python
      >>> a = 10
      >>> b = 15
      >>> print("a =", a, ", b=", b)
      a = 10 , b= 15
      >>> a, b = b, a
      >>> print("a =", a, ", b=", b)
      a = 15 , b= 10
      >>>      
      ```

+ `+=`

+ `-=`

+ `*=`

+ `/=`

+ `%=`

+ `//=`

+ `**=`

#### 成员运算符

+ `in`

+ `not in`

#### 身份运算符

+ `is`

+ `is not`

#### 优先级

+ BODMAS

  + 图示

    + [diagram]  
      ![BODMAS](./images/bodmas-diagram-small.png)

  + 列表

    + [table]

      | priority | operator             | Notes |
      | :------- | :------------------- | :---- |
      | 1        | `()`                 |       |
      | 2        | `**`                 | 幂    |
      | 3        | `~`                  | 位反            |
      | 4        | `+` , `-`            | 正负            |
      | 5        | `*`, `/` , `%`, `//` | 乘、除、模、地板除 |
      | 6        | `+` , `-`            | 加、减          |
      | 7        | `<<`, `>>`           | 移位/位移        |
      | 8        | `&`                  | 位与            |
      | 9        | `^`                  | 位异或          |
      | 10       | `\|`                 | 位或            |
      | 11       | `<`, `<=`, `>`, `>=`, `<>`, `\|=`, `==` | 比较 |
      | 12       | `not`                | 逻辑非          |
      | 13       | `and`, `or`          | 逻辑与， 逻辑或  |
      | 14       |                      | 赋值运算        |

### 流程控制

#### 条件控制 / 条件判断

+ if

+ if else

+ if elif else

+ 条件嵌套

+ 类 switch ... case ...

  + 示例

    + [operating]

      ```python
      >>> choice = "ham"
      >>> print( {"spam": 1.25, "ham": 1.99, "eggs": 0.99, "bacon": 1.10}[choice])
      1.99
      >>>
      ```

+ if/else三元表达式

  + 示例

    + [operating]

      ```python
      >>> a = "t" if True else "f"
      >>> print(a)
      t
      >>> a = "t" if False else "f"
      >>> print(a)
      f
      >>> ["f","t"][bool("")]
      'f'
      >>> ["f","t"][bool("True")]
      't'
      >>>
      ```

#### 循环控制

+ 关键词

  + while
  + break
    跳出最近循环
  + continue
    跳过循环本次处理的剩余部分
  + pass
    占位语句
  + else
    循环正常结束时执行
  + for

    + 示例

      + [operating]

        ```python
        >>> S = "lumberjack"
        >>> for x in S: print(x, end=" ")
        ... print("")
        ...
        l u m b e r j a c k 
        >>> 
        >>> T = ("and", "I'm", "okay")
        >>> for x in T: print(x, end = " ")
        ... print("")
        ...
        and I'm okay
        >>> 
        >>> L = [(1,2), (2,3), (3,4)]
        >>> for (a, b) in L: print(a,b)
        ... print("")
        ...
        1 2
        2 3
        3 4
        
        >>> 
        ```

#### 递归

#### 异常处理

##### 异常简述

+ 错误类型
+ 异常捕获
+ 异常抛出

### 语句, 表达式, 内置函数, 自定义函数, 函数式编程

#### 内置函数列表

[官方文档 Python3.13](https://docs.python.org/zh-cn/3.13/library/functions.html)

+ `abs()`

+ `aiter()`
  + 说明
    + 起始版本，Python3.10
    + 终止版本

+ `all()`
  + 说明
    + 判断可迭代对象中的所有元素是否都为True
    + 起始版本
    + 终止版本

+ `anext()`
  + 说明
    + 起始版本，Python3.10
    + 终止版本

+ `any()`
  + 说明
    + 判断可迭代对象中的所有元素是否都为False
      至少有一个为True时，返回True

    + 起始版本
    + 终止版本

+ `ascii()`

+ `bin()`

+ `bool()`

+ `breakpoint()`

+ `bytearray()`

+ `bytes()`

+ `callable()`

+ `chr()`

+ `classmethod()`

+ `compile()`

+ `complex()`

+ `delattr()`

+ `dict()`

+ `dir()`

+ `divmod()`

+ `enumerate()`

  + 说明
    + 起始版本
    + 终止版本

  + [opreating]

    ```python
    >>> S = "splitSting"
    >>> offset = 0
    >>> for item in S:
    ...     print(item, "appears at offset", offset)
    ...     offset += 1
    ...
    s appears at offset 0
    p appears at offset 1
    l appears at offset 2
    i appears at offset 3
    t appears at offset 4
    S appears at offset 5
    t appears at offset 6
    i appears at offset 7
    n appears at offset 8
    g appears at offset 9
    >>>
    >>> for (offset, item) in enumerate(S):
    ...     print(item, "appears at offset", offset)
    ...
    s appears at offset 0
    p appears at offset 1
    l appears at offset 2
    i appears at offset 3
    t appears at offset 4
    S appears at offset 5
    t appears at offset 6
    i appears at offset 7
    n appears at offset 8
    g appears at offset 9
    >>>
    >>> E = enumerate(S)
    >>> E
    <enumerate object at 0x7d3fe0e60860>
    >>> print(type(E))
    <class 'enumerate'>
    >>> next(E)
    (0, 's')
    >>> next(E)
    (1, 'p')
    >>> next(E)
    (2, 'l')
    >>> next(E)
    (3, 'i')
    >>> next(E)
    (4, 't')
    >>> next(E)
    (5, 'S')
    >>> next(E)
    (6, 't')
    >>> next(E)
    (7, 'i')
    >>> next(E)
    (8, 'n')
    >>> next(E)
    (9, 'g')
    >>> next(E)
    Traceback (most recent call last):
      File "<python-input-19>", line 1, in <module>
        next(E)
        ~~~~^^^
    StopIteration
    >>>
    >>> [str(i) + " - " + c for (i, c) in enumerate(S)]
    ['0 - s', '1 - p', '2 - l', '3 - i', '4 - t', '5 - S', '6 - t', '7 - i', '8 - n', '9 - g']
    >>>    ```

+ `eval()`

+ `exec()`

+ `filter()`

+ `float()`

+ `format()`

  + 语法 help(format)

    + [operating]

      ```text
      Help on built-in function format in module builtins:
      
      format(value, format_spec='', /)
          Return type(value).__format__(value, format_spec)
      
          Many built-in types implement format_spec according to the
          Format Specification Mini-language. See help('FORMATTING').
      
          If type(value) does not supply a method named __format__
          and format_spec is empty, then str(value) is returned.
          See also help('SPECIALMETHODS').
      ```

+ `frozenset()`

+ `getattr()`

+ `globals()`

+ `hasattr()`

+ `hash()`

+ `help()`

+ `hex()`

+ `id()`

  + 语法 help(id)

    + [operating]

      ```text
      Help on built-in function id in module builtins:
      
      id(obj, /)
          Return the identity of an object.
      
          This is guaranteed to be unique among simultaneously existing objects.
          (CPython uses the object's memory address.)
      ```

  + 示例

    + [operating]

      ```python
      >>> a = 10
      >>> print(id(a))
      10841416
      >>>
      ```

+ `input()`

  + 语法 help(input)

    + [operating]

      ```text
      Help on method input in module _pyrepl.readline:
      
      input(prompt: 'object' = '') -> 'str' method of _pyrepl.readline._ReadlineWrapper instance
      ```

    + parameters
      + "prompt"
        提示信息
      + ”object"
        字符串

  + 示例
    + [operating]

      ```python
      >>> a = input()
      100
      >>> print(type(a))
      <class 'str'>
      >>> a = int(input())
      100
      >>> print(type(a))
      <class 'int'>
      >>>
      ```

+ `int()`

+ `isinstance()`

+ `issubclass()`

+ `iter()`

+ `len()`

+ `list()`

+ `locals()`

+ `map()`

+ `max()`

+ `memoryview()`

+ `min()`

+ `next()`

+ `object()`

+ `oct()`

+ `open()`
  + 语法 help(open)

    + [operating]

      ```text
      ...
      Help on built-in function open in module _io:

      open(
          file,
          mode='r',
          buffering=-1,
          encoding=None,
          errors=None,
          newline=None,
          closefd=True,
          opener=None
      )
          Open file and return a stream.  Raise OSError upon failure.
          ========= ===============================================================
          Character Meaning
          --------- ---------------------------------------------------------------
          'r'       open for reading (default)
          'w'       open for writing, truncating the file first
          'x'       create a new file and open it for writing
          'a'       open for writing, appending to the end of the file if it exists
          'b'       binary mode
          't'       text mode (default)
          '+'       open a disk file for updating (reading and writing)
          ========= ===============================================================
      ...
      ```

  + 示例

    + [operating]

      ```python
      >>> f = open("etc/log1.log","a")
      >>> print("hello, python spring", file=f)
      >>>
      >>> with open("etc/log2.log", "a") as f2:
      ...     print("hi, python print", file=f2)
      ...
      >>> quit()
      
      ┌──(edgar㉿ThinkPadT14P-23)-[~/workspaces/PythonWrkspces/Exercises26]
      └─$ cat etc/log1.log
      hello, python spring
      
      ┌──(edgar㉿ThinkPadT14P-23)-[~/workspaces/PythonWrkspces/Exercises26]
      └─$ cat etc/log2.log
      hi, python print
      
      ┌──(edgar㉿ThinkPadT14P-23)-[~/workspaces/PythonWrkspces/Exercises26]
      └─$
      ```  

      + with 方式，会自动关闭文件。**建议使用该方式**

+ `ord()`

+ `pow()`

+ `print()`

  + 语法 help(print)

    + [operating]

      ```text
      >>> 
      Help on built-in function print in module builtins:
      
      print(*args, sep=' ', end='\n', file=None, flush=False)
          Prints the values to a stream, or to sys.stdout by default.
      
          sep
            string inserted between values, default a space.
          end
            string appended after the last value, default a newline.
          file
            a file-like object (stream); defaults to the current sys.stdout.
          flush
            whether to forcibly flush the stream.
      
      >>>
      ```

    + parameters

      + "objects"
        输出一个或多个对象，输出多个对象需要 "sep" 分隔
      + "sep"
        输出多个对象时使用"sep"指定的分隔符分隔，默认为一个空格
      + "end"
        输出结束后以"end"指定的字符结尾，默认为换行符("\n")
      + "file"
        要写入的文件对象，默认为终端输出("sys.stdout")
      + "flush"
        输出是否被立刻刷新。立刻刷新("True")，默认为缓存("False")

  + 示例

    + [operating]

      ```python
      >>> print("1+1=",1+1)
      1+1= 2
      >>>
      ```

    + [operating]

      ```python
      >>> print("1+1=",1+1, sep="", end="\n")
      1+1=2
      >>> print("1+1",1+1, sep="=", end="\n")
      1+1=2
      >>> print("1+1",1+1, sep=" = ", end="\n")
      1+1 = 2
      >>>
      ```

  + 示例

    + [operating]

      ```python
      >>> print("abcd""efg")
      abcdefg
      >>>
      ```

  + 示例

    + [operating]

      ```python
      >>> text = "%s: %-.4f, %05d" % ("Result", 3.1415926, 42)
      >>> print(text, type(text))
      Result: 3.1416, 00042 <class 'str'>
      >>>
      ```

      + 格式化字符

        + "%c", character
        + "%s", string
        + "%d", Decimal integers
        + "%f", float

  + 示例

    + [operating]

      ```python
      >>> name, age = "Bob Lee", 18
      >>> print(f"name is {name}, aga is {age}")
      name is Bob Lee, aga is 18
      >>>
      ```

      + f表达式

  + 示例

    + [operating]

      ```python
      >>> print("My name is {}, I am {} years old.".format("Bob",18))
      My name is Bob, I am 18 years old.
      >>>
      ```

+ `property()`

+ `range()`
  + 说明
    + 半闭半开区间
    + 步长
  
+ `repr()`

+ `reversed()`

+ `round()`

+ `set()`

+ `setattr()`

+ `slice()`

+ `sorted()`

+ `staticmethod()`

+ `str()`

+ `sum()`
  + 说明
    `sum(iterable[,start=0])`
  + parameters
    + iterable, 可迭代的对象
    + start, 求和的初始值。默认为 0

+ `super()`

+ `tuple()`

+ `type()`

+ `vars()`

+ `zip()`

+ `__import__()`

#### 自定义函数

+ 说明
  + 一些语句集合在一起的部件
  + 最大程度的重用和最小化代码冗余
  + 对流程的分解

+ def 语句

+ 函数调用
+ 参数传递

### 面向对象编程 AllIsObject

#### OOP简述

+ Python对象三要素

  + id, 对象唯一标识符
  + type, 对象类型
    + 类型存在于对象中，而非定义在变量上
  + value, 对象的值

+ 程序员视角

  + 程序是由模块构成的
  + 模块包含语句
  + 语句包含表达式
  + 表达式建立并处理对象

+ 类 & 对象
  + 动态语言和静态语言
    Python面向对象更加彻底
  + 函数 和 类 是对象，属于python的顶层对象
    + 类 是 模板对象
    + 将 函数、类 赋值给变量
    + 函数、类 可以添加到集合对象中
    + 函数、类 可以作为参数传递给函数
    + 函数、类 可以作为函数的返回值

  + 模块 是对象

+ 继承 & 多态

+ 封装 & 访问控制

+ 猴子补丁

+ 鸭子类型

+ 魔法函数

### 模块 & 包

#### 模块简述

+ 模块导入
  + [operating]

    ```sh
    ┌──(edgar㉿ThinkPadT14P-23)-[~/workspaces/PythonWrkspces/Exercises26/Test]
    └─$ tree ./
    ./
    ├── model1
    │   └── say.py
    └── model2
        ├── hello.py
        ├── __pycache__
        │   └── hello.cpython-313.pyc
        └── say.py
    
    4 directories, 4 files
    
    ┌──(edgar㉿ThinkPadT14P-23)-[~/workspaces/PythonWrkspces/Exercises26/Test]
    └─$ cd model2
    
    ┌──(edgar㉿ThinkPadT14P-23)-[~/workspaces/PythonWrkspces/Exercises26/Test/model2]
    └─$ cat hello.py
    # -*- coding: utf-8 -*-
    
    print("Hello, the world!")
    
    ┌──(edgar㉿ThinkPadT14P-23)-[~/workspaces/PythonWrkspces/Exercises26/Test/model2]
    └─$ cat say.py
    # -*- coding: utf-8 -*-
    
    import hello
    
    
    
    ┌──(edgar㉿ThinkPadT14P-23)-[~/workspaces/PythonWrkspces/Exercises26/Test/model2]
    └─$ python say.py
    Hello, the world!
    
    ┌──(edgar㉿ThinkPadT14P-23)-[~/workspaces/PythonWrkspces/Exercises26/Test/model2]
    └─$ cd ../model1
    
    ┌──(edgar㉿ThinkPadT14P-23)-[~/workspaces/PythonWrkspces/Exercises26/Test/model1]
    └─$ cat say.py
    # -*- coding: utf-8 -*-
    
    import sys
    
    sys.path.append("/home/edgar/workspaces/PythonWrkspces/Exercises26/Test/model2")
    
    import hello
    
    ┌──(edgar㉿ThinkPadT14P-23)-[~/workspaces/PythonWrkspces/Exercises26/Test/model1]
    └─$ python say.py
    Hello, the world!
    
    ┌──(edgar㉿ThinkPadT14P-23)-[~/workspaces/PythonWrkspces/Exercises26/Test/model1]
    └─$
    ```

  + [operating]

    ```python
    ┌──(edgar㉿ThinkPadT14P-23)-[~/workspaces/PythonWrkspces/Exercises26/Test/model1]
    └─$ ll
    total 12
    -rw-r--r-- 1 edgar edgar   56 May 21 23:59 myfile.py
    drwxr-xr-x 2 edgar edgar 4096 May 22 00:00 __pycache__
    -rw-r--r-- 1 edgar edgar  132 May 19 00:56 say.py
    
    ┌──(edgar㉿ThinkPadT14P-23)-[~/workspaces/PythonWrkspces/Exercises26/Test/model1]
    └─$ cat myfile.py
    # -*- coding: utf-8 -*-
    
    title = "The Meaning of Life"
    
    
    ┌──(edgar㉿ThinkPadT14P-23)-[~/workspaces/PythonWrkspces/Exercises26/Test/model1]
    └─$ python
    Python 3.13.12 (main, Feb  4 2026, 15:06:39) [GCC 15.2.0] on linux
    Type "help", "copyright", "credits" or "license" for more information.
    >>> import myfile
    >>> print(myfile.title)
    The Meaning of Life
    >>>
    >>> from myfile import title
    >>> print(title)
    The Meaning of Life
    >>>
    ```

+ 包导入
+ 模块搜索路径
  + [operating]

    ```python
    >>> import sys
    >>> print(sys.path)
    ['', '/usr/lib/python313.zip', '/usr/lib/python3.13', '/usr/lib/python3.13/lib-dynload', '/usr/local/lib/python3.13/dist-packages', '/usr/lib/python3/dist-packages', '/usr/lib/python3.13/dist-packages']
    >>>
    ```

## 专题

### 安装工具

### 虚拟环境

### Python标准库

[官方文档 Python3.13](https://docs.python.org/zh-cn/3.13/library/index.html)

+ ConfigParser
  
+ cmath
  + 说明
    复数计算库
  + 属性 / 成员
  + 方法 / 函数

+ datetime

+ math
  + 说明
    + 角度, 
      与常识数学相反: 顺时针旋转为正向; Y轴向下为正向
  + 属性 / 成员
    + pi, 圆周率
      + 示例
        + [operating]

          ```python
          >>> import math
          >>> math.pi
          3.141592653589793
          ```

  + 方法 / 函数
    + acos(), 返回反余弦
    + asin(), 返回反正弦
    + atan(), 返回反正切
    + atan2(), 返回给定坐标的反正切值

    + cos(), 返回余弦
    + degress(), 返回弧度转角度
    + radians(), 返回角度转弧度
    + sin(), 返回正弦
    + sqrt(), 开平方
      + 说明
      + 示例
        + [operating]

          ```python
          >>> import math
          >>> math.sqrt(82)
          9.055385138137417
          >>>
          ```

    + tan(), 返回正切

+ os

+ shutil

+ socket

+ random

  + 说明
  + 属性 / 成员
  + 方法 / 函数

    + random()
      + 示例
        + [operating]

          ```python
          >>> import random
          >>> random.random()
          0.04030966249741974
          ```

    + choice()
      + 示例
        + [operating]

          ```python
          >>> import random
          >>> random.choice([2,4,6,8])
          2
          >>> random.choice([2,4,6,8])
          4
          >>> random.choice([2,4,6,8])
          2
          >>> random.choice([2,4,6,8])
          6
          ```

+ re
  + 说明，正则表达式处理库
  + 属性 / 成员
  + 方法 / 函数

  + 常用规则代码

    + 常用元字符
      + ".", 匹配除换行符以外的任意字符
      + "\w", 匹配字母或数字或下划线
      + "\s", 匹配任意的空白符
      + "\d", 匹配数字
      + "\b", 匹配单词的开始或结束
      + "^", 匹配字符串的开始
      + "$", 匹配字符串的结束

    + 常用限定符
      + “*”, 重复零次或更多次
      + "+", 重复一次或更多次
      + "?", 重复零次或一次
      + "{n}", 重复n次
      + "{n,}", 重复n次或更多次
      + "{n,m}", 重复n次到m次

    + 常用反义词
      + "\W", 匹配任意不是字母、数字、下划线、汉字的字符
      + "\S", 匹配任意不是空白符的字符
      + "\D", 匹配任意非数字的字符
      + "\B", 匹配不是单词开头或结束的位置
      + "[^x]", 匹配除了x以外的任意字符
      + "[^aeiou]", 匹配除了aeiou这几个字母以外的任意字符

### 第三方库

#### 数学计算

##### summary

#### 文件操作

##### summary

#### 日期时间

##### summary

#### 网络

##### summary

+ requests

#### 并发

#### 爬虫

#### 金融

#### 科学计算

#### 图形处理

#### 数据分析 和 可视化

##### 数据分析概述

+ NumPy
+ Pandas
+ Matplotlib
+ Seaborn

#### 机器学习、深度学习、人工智能

##### 概述

+ Scikit-learn

+ 数据预处理

+ 机器学习算法

+ PyTorch

#### Web编程

##### Python Web 简述

+ Django
  + MTV

+ Flask

+ FastAPI

#### 数据库

#### 大数据

#### 算法

#### 系统运维

## 附录

### 交互式

### IDE & Tools

#### PyCharm

+ File

  + Setting
    + Python
      + Interpreter
        + packages
          + "cfg"
          + "pygame":{"version":"2.6.1"}
    + Editor
      + General
        + [content]
          + Mouse Control
            + [X] Change font size with Ctrl+Mouse Wheel in:
              + [X] Active Editor

      + Color Scheme
        + [content]
          + Schema: VSCode light Modern
        + Color Scheme Font
          + [V] Use color schema font instead of the default
            + Font: Intel One Mono
            + Size: 13, Line height: 1.2
    + Plugins
      + ~~activate-power-mode-x~~
      + CodeGlance Pro 缩略图
      + Inspection Lens 错误提示
      + Rainbow Brackets 括号成对提示

#### Jupyter

#### Anaconda

### 参考

#### internet

##### 官方网站

+ [python.org](https://www.python.org/)

  + [Documentation CN](https://docs.python.org/zh-cn/3.13/index.html)

  + [Documentation EN](https://www.python.org/doc/)

  + [Community](https://www.python.org/community/)

##### 学习网站

+ [百度](http://www.baidu.com)
  + [百度文库](http://wenku.baidu.com)
    + [Python / 基础]()
      + [~~(完整版)python教案~~](https://wenku.baidu.com/view/15e225620a75f46527d3240c844769eae109a357.html?fr=aladdin664466&ind=1&word=Python&aigcsid=0&qtype=0&lcid=1&queryKey=Python&verifyType=&_wkts_=1777200435716&bdQuery=python&chatType=chat)

+ [bilibili]()

  + [python入门特训营]

    + [Python / 基础]()

      + [【97全集】（2025最新）Python高级核心技术全套课程](https://www.bilibili.com/video/BV172nxzzEZT/?spm_id_from=333.337.search-card.all.click&vd_source=38fc599412349dcfe60484e3ff320c66)

+ [C语言中文网](https://c.biancheng.net/)

  + [Python教程](https://c.biancheng.net/python/)

    + [Python / 基础](https://c.biancheng.net/python/)

+ [CSDN](https://www.csdn.net/)
  + [呆呆敲代码的小Y]()
    + [Python / 基础]()
      + [全网最详细的Python入门基础教程，Python最全教程（非常详细，整理而来）](https://xiaoy.blog.csdn.net/article/details/117248277)

### 系统维护

#### "wsl -d AlmaLinux8"

+ [数据库学习笔记](./Database-Overview-2604.md)

#### "wsl -d KaliLinux26"

+ [Linux网络学习笔记](./Linux-Network.md)

### Tips

+ 字符集相关

  + 图示

    + [diagram]  
      ![python character](./images/python-char_string_coding.jpeg)

  + 文件首定义
    + [code]

      ```python
      # -*- coding: utf-8 -*-
      ```

+ 编程建议

  + 源文件末尾加空行

+ PyCharm 快捷键

### 项目练习

