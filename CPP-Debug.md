# C++ Programe DEBUG

## Overview

## on Linux

### Tool - GDB, GNU Debugger

#### Overview

+ 设置断点，在指定代码行上暂停执行  
  断点可以是条件表达式

+ 单步执行

+ 动态改变程序变量 值的变化

+ 分析 coredump 文件

#### gdb 调试命令参数

```sh
# gdb
GNU gdb (Debian 16.3-5) 16.3
Copyright (C) 2024 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
Type "show copying" and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<https://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
    <http://www.gnu.org/software/gdb/documentation/>.

For help, type "help".
Type "apropos word" to search for commands related to "word".
(gdb)
```

+ `help(h)`

+ `run(r)`

+ `start`

+ `list(l)`

+ `set`

+ `next(n)`  
  越过"函数"/"过程"/"方法"

+ `step(s)`  
  进入"函数"/"过程"/"方法"

+ `backstace(bt)`

+ `frame(f)`

+ `info(i)`

+ `finish`  
  结束当前"函数"执行，返回"函数"调用点

+ `continue(c)`

+ `print(p)`

+ `quit(q)`

+ `break+num(b)`

+ `info breakpoints`

+ `delete breakpoints num(d)`

+ `display`

+ `undisplay`

+ `watch`

+ `i watch`

+ `enable breakpoints`

+ `disable breakpoints`

+ `x`

+ `run argv[i] argv[2]`

+ `set follow-fork-mode child`  
  Makefile项目管理，选择跟踪父子进程（fork()）

#### 操作实例 1

```sh
# g++ main.cpp src/Swap.cpp -Iinclude -Wall -O2 -std=c++11 -o b.out

# g++ main.cpp src/Swap.cpp -Iinclude -Wall -O2 -std=c++11 -g -o a.out
```

```sh
# gdb b.out
Reading symbols from b.out...
(No debugging symbols found in b.out)

# gdb a.out
```

## on Windows