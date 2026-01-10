# CPP Compiling

## Overview

### 动态库 vs 静态库

+ 静态库，程序编译时，将相关静态库中的代码直接编入可执行文件中，文件偏大，速度快

+ 动态库，程序编译时，只将相关动态库中的信号？编入可执行文件中，文件偏小，速度慢

### 编译器

+ GCC, GNU Compiler Collection

  + GCC

  + MinGW-w64  
    [MinGW & CMake安装配置笔记](./CPP_MINGW-setup.md)  
    [VS Code安装配置笔记](./CPP_VSCode-Settings-2512.md)    

+ Clang/LLVM

+ MSVC  
  + Microsoft Visual Studio Community 2026   
    + MSVC  
      "x86_x64 Cross Tools Comman"  

      ```cmd
      **********************************************************************
      ** Visual Studio 2026 Developer Command Prompt v18.1.1
      ** Copyright (c) 2025 Microsoft Corporation
      **********************************************************************
      [DEBUG:ext\vcvars.bat] Found potential v145 version file: 'Microsoft.VCToolsVersion.VC.14.50.18.0.txt'
      [DEBUG:ext\vcvars.bat] Testing v145 version file: 'Microsoft.VCToolsVersion.VC.14.50.18.0.txt'
      [vcvarsall.bat] Environment initialized for: 'x86_x64'

      C:\Program Files\Microsoft Visual Studio\18\Community>cl
      Microsoft (R) C/C++ Optimizing Compiler Version 19.50.35721 for x64
      Copyright (C) Microsoft Corporation.  All rights reserved.

      usage: cl [ option... ] filename... [ /link linkoption... ]

      C:\Program Files\Microsoft Visual Studio\18\Community>
      ```

      `cl /EHsc `

    + [MS-VisualStudio配置笔记](./CPP_VS-Settings-2512.md)

+ ICC, Intel C++ Compiler

### gcc/g++ 编译过程

1. Pre-Processing, 预处理，加入头文件
   + 生成文件, "*.i"
   + 命令示例, `g++ -E main.cpp -o test.i`

2. Compiling, 编译，生成**汇编（指令）文件**  
   + 生成文件, "*.s"  
   + 命令示例, `g++ -S test.i -o CTst.s`  

3. Assembling, 汇编，生成**目标文件**（二进制）  
   + 生成文件, "*.o"
   + 命令示例, `g++ -c CTst.s -o objTst.o`

4. Linking, 链接，生成可执行文件
   + 生成文件
   + 命令示例, `g++ objTst.o -o exeTest`

## GCC / G++

### g++参数

+ 调试信息

  `-g`, 生成带调试信息的可执行文件

+ 优化, -On

  + `-O0`

  + `-O!` / `-O1`

  + `-O2`

  + `-O3`

+ 库，头文件

  + `-l`
    指定编译时使用的库

  + `-L`
    库文件搜索（存放）目录

  + `-I`
    头文件搜索（存放）目录

+ 警告信息

  + `-Wall`

  + `-w`
    关闭警告信息

+ 编译标准

  + `-std`
    如, `-std=c++11`

+ 生成文件

  + `-o`

+ 其他

  + `-D`

### 操作实例 1

"lin_path": "/mnt/c/Workspace/workspaces/CppWrkspces/lessons/lin64/ProjFromI8/XiaoBing1016/comp_header-2512a"  
"win_path": "C:\Workspace\workspaces\CppWrkspces\lessons\lin64\ProjFromI8\XiaoBing1016\comp_header-2512a"
  
+ 目录结构

  ```sh
  # tree .
  .
  ├── include
  │   └── Swap.h
  ├── lib
  ├── main.cpp
  └── src
      └── Swap.cpp
  
  4 directories, 3 files
  
  ```

+ 错误命令，未指定头文件路径

  ```sh
  # g++ main.cpp src/Swap.cpp
  main.cpp:2:10: fatal error: swap.h: No such file or directory
      2 | #include "swap.h"
        |          ^~~~~~~~
  compilation terminated.
  src/Swap.cpp:1:10: fatal error: swap.h: No such file or directory
      1 | #include "swap.h"
        |          ^~~~~~~~
  compilation terminated.
  
  ```

+ 普通命令， `-I`指定头文件目录

  ```sh
  # g++ main.cpp src/Swap.cpp -Iinclude
  #
  # ll
  total 20
  -rwxrwxrwx 1 root root 16400 Dec 27 14:49 a.out
  drwxrwxrwx 1 root root  4096 Dec 27 14:27 include
  drwxrwxrwx 1 root root  4096 Dec 27 14:27 lib
  -rwxrwxrwx 1 root root   564 Dec 27 14:44 main.cpp
  drwxrwxrwx 1 root root  4096 Dec 27 14:47 src
  
  # ./a.out
  the 1st integer: 35,    the 2nd integer: 67
  the 1st integer: 67,    the 2nd integer: 35
  
  ```

+ 普通命令（增加编译参数）， `-Wall -O2 -std=c++11`

  ```sh
  # g++ main.cpp src/Swap.cpp -Iinclude -Wall -O2 -std=c++11 -o b.out
  #
  # ll
  total 44
  -rwxrwxrwx 1 root root 16400 Dec 27 14:51 a.out
  -rwxrwxrwx 1 root root 16736 Dec 27 14:55 b.out
  drwxrwxrwx 1 root root  4096 Dec 27 14:27 include
  drwxrwxrwx 1 root root  4096 Dec 27 14:27 lib
  -rwxrwxrwx 1 root root  1373 Dec 27 14:52 main.cpp
  drwxrwxrwx 1 root root  4096 Dec 27 14:47 src
  ```

### 操作实例 2

"lin_path": "/mnt/c/Workspace/workspaces/CppWrkspces/lessons/lin64/ProjFromI8/XiaoBing1016/comp_header-2512a"  
"win_path": "C:\Workspace\workspaces\CppWrkspces\lessons\lin64\ProjFromI8\XiaoBing1016\comp_header-2512a"

+ 目录结构

  ```sh
  # tree .
  .
  ├── include
  │   └── Swap.h
  ├── lib
  ├── main.cpp
  └── src
      └── Swap.cpp
  
  4 directories, 3 files
  
  ```

+ 生成静态库

  ```sh
  # g++ src/Swap.cpp -c -Iinclude -o src/Swap.o

  # ll src/
  total 4
  -rwxrwxrwx 1 root root  109 Dec 27 14:51 Swap.cpp
  -rwxrwxrwx 1 root root 1136 Dec 27 16:00 Swap.o

  # ar rs lib/libswap.a src/swap.o
  ar: creating lib/libswap.a
  
  # g++ main.cpp -Iinclude -Llib -lSwap -o staticmain
  
  # tree
  .
  ├── include
  │   └── Swap.h
  ├── lib
  │   └── libswap.a
  ├── main.cpp
  ├── src
  │   ├── Swap.cpp
  │   └── Swap.o
  └── staticmain
  
  4 directories, 6 files
  ```

### 操作实例 3

"lin_path": "/mnt/c/Workspace/workspaces/CppWrkspces/lessons/lin64/ProjFromI8/XiaoBing1016/comp_header-2512a"  
"win_path": "C:\Workspace\workspaces\CppWrkspces\lessons\lin64\ProjFromI8\XiaoBing1016\comp_header-2512a"

+ 目录结构

  ```sh
  # tree .
  .
  ├── include
  │   └── Swap.h
  ├── lib
  │   └── libswap.a
  ├── slib
  ├── main.cpp
  └── src
      ├── Swap.o
      └── Swap.cpp
  
  4 directories, 3 files
  
  ```

+ 生成动态库  

  ```sh
  # g++ src/Swap.cpp -Iinclude -c -fPIC -o src/Swap2.o

  # ll src/
  total 8
  -rwxrwxrwx 1 root root 1136 Dec 27 16:32 Swap2.o
  -rwxrwxrwx 1 root root  109 Dec 27 14:51 Swap.cpp
  -rwxrwxrwx 1 root root 1136 Dec 27 16:00 Swap.o

  # gcc -shared -o slib/libSwap.so src/Swap2.o

  # g++ main.cpp -Iinclude -Lslib -lSwap -o dynamain
  
  # tree
  .
  ├── dynamain
  ├── include
  │   └── Swap.h
  ├── lib
  │   └── libswap.a
  ├── main.cpp
  ├── slib
  │   └── libSwap.so
  ├── src
  │   ├── Swap2.o
  │   ├── Swap.cpp
  │   └── Swap.o
  └── staticmain
  
  5 directories, 9 files
  
  ```

  + 执行命令  

    ```sh
    # ./dynamain
    ./dynamain: error while loading shared libraries: libSwap.so: cannot open shared object file: No such file or directory
    
    # LD_LIBRARY_PATH=slib ./dynamain
    the 1st integer: 35,    the 2nd integer: 67
    the 1st integer: 67,    the 2nd integer: 35

    ```

## make

## cmake

[CMake学习笔记](./CPP_CMake-2512.md)

## qmake