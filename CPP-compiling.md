# CPP Compiling

## Overview

### 编译器

+ GCC, GNU Compiler Collection

  + GCC

  + MinGW-w64

+ Clang/LLVM

+ MSVC

+ ICC, Intel C++ Compiler

### 编译过程

1. Pre-Processing, 预处理，加入头文件
   + 生成文件, "*.i"
   + 命令示例, `g++ -E main.cpp -o test.i`

2. Compiling, 编译，生成汇编（指令）文件
   + 生成文件, "*.s"
   + 命令示例, `g++ -S test.i -o CTst.s`

3. Assembling, 汇编，生成目标文件（二进制）
   + 生成文件, "*.o"
   + 命令示例, `g++ -c CTst.s -o objTst.o`

4. Linking, 链接，生成可执行文件
   + 生成文件
   + 命令示例, `g++ objTst.o -o exeTest`

## GCC

### gcc参数

+ 调试信息

  `-g`, 生成带调试信息的可执行文件

+ 优化, -On

  + `-O0`

  + `-O!` / `-O1`

  + `-O2`

  + `-O3`

+ 库，头文件

  + `-l`

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

## make

## cmake