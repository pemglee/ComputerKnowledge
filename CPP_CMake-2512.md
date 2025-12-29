# CMake学习笔记

## Overview

CMake, Cross-platform development, 跨平台安装编译工具。  
生成本地平台的构建系统，即生成"Makefile"等构建脚本。  

### 构成

#### 初始文件

+ "CMakeLists.txt"
  
  + 语法概述  
    + 参数使用 "(" 和 ")" 圈定; 使用 "空格" 或 ";" 分隔。  
    + 指令，大小写不敏感； 但 参数 和 变量 大小写敏感。  
    + 变量使用 "${变量名}" 取值，但在 "if" 控制中**须**直接使用变量名
    + 子目录中可包含"CMakeLists.txt"。  
      如无，则继承父祖目录的"CMakeLists.txt"。  

  + CMake指令
    + `cmake_minimum_required`, 指定CMake的最小版本要求  
      **语法**, `cmake_minimum_required(VERSION versionNumber [FATAL_ERROR])`  
      ex. 
      ```CMake
      cmake_minimum_required (VERSION 3.31)
      ```  

    + `project`, 定义工程名称，并指定工程支持的语言  
      **语法**, `project(projectname [CXX|C|Java])`  
      ex. 
      ```CMake
      project (HelloWorld)
      ```  

    + `set`, 显示定义变量  
      **语法**, `set(VAR [VALUE] [CACHE TYPE DOCSTRING [FORCE]])`  
      ex. 
      ```CMake
      set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Werror -std=c++17")
      set (source_dir "${PROJECT_SOURCE_DIR}/src")
      ```

    + `include_directories`, 向工程添加多个特定头文件的搜索路径  
      相当于 g++ 指令中的 `-I` 参数  
      **语法**, `include_directories([AFTER|BEFORE] [SYSTEM] dir1 dir2 ...)`

    + `link_directories`, 向工程添加多个特定库文件的搜索路径  
      相当于 g++ 指令中的 `-L` 参数  
      **语法**, `link_direcotries(dir1 dir2 ...)`  

    + `add_library`, 生成库文件  
      **语法**, `add_library(libname [SHARED|STATIC|MODULE] [EXCLUDE_FROM_ALL] source1 source2 ...)`  
      + "SHARED", 动态库  
      + "STATIC", 静态库  
      + "MODULE",  
 
    + `add_compile_options`, 添加编译参数  
      **语法**, `add_compile_options(<option> ...)`  
      ex.  
      ```CMake
      add_compile_optins(-Wall -std=C++17 -O2)
      ```

    + `add_executable`, 生成可执行文件  
      **语法**, `add_executable(execute_name cppfile)`  
      ex.  
      ```CMake
      add_executable(main main.cpp)
      ```

      ex.  
      ```CMake
      file (GLOB source_files "${source_dir}/*.cpp")

      add_executable (HelloWorld ${source_files})
      ```

    + `target_link_libraries`, 为target添加需要链接的共享库  
      相当于 g++ 指令中的 `-l` 参数  
      **语法**, `target_link_libraries(target library1<debug|optimized> library2 ...)`  

    + `add_subdirectory`, 向当前工程添加存放源文件的子目录，并可指定中间二进制和目标二进制存放的位置  
      **语法**, `add_subdirectory(source_dir [binary_dir] [EXCLUDE_FROM_ALL])`  
      source_dir目录下**须**有 "CMakeLists.txt"  
      ex.  
      ```CMake
      add_subdirectory(src)
      ```

    + `aux_source_directory`, 发现一个目录下所有的源文件并将列表存储在一个变量中，用于临时构建源文件列表  
      **语法**, `aux_source_directory(dir VARIABLE)  
      ex.
      ```CMake
      aux_source_directory(. SRC)

      add_executable(main ${SRC})
      ```

  + 常用变量  
    + "CMAKE_C_FLAGS"  
    + "CMAKE_CXX_FLAGS" g++编译
    + "CMAKE_BUILD_TYPE" 编译类型  
      + "Debug"  
      + "Release"
    + "CMAKE_BINARY_DIR" _vs_ "PROJECT_BINARY_DIR" _vs_ "<projectname>_BINARY_DIR"  
      此三者指代内容一致。如果  
      "in-source build", 变量为工程顶层目录  
      "out-of-source build", 变量为工程编译发生的目录  
      
      + "PROJECT_BINARY_DIR"  

    + "CMAKE_SOURCE_DIR" _vs_ "PROJECT_SOURCE_DIR" _vs_ "<projectname>_SOURCE_DIR"  

    + "CMAKE_C_COMPILER", 指定C编辑器

    + "CMAKE_CXX_COMPILE", 指定C++编辑器  

    + "EXECUTABLE_OUTPUT_PATH", 可执行文件的输出/存放路径  

    + "LIBRARY_OUTPUT_PATH", 库文件的输出/存放路径  
      

+ "build.sh" Cherno示例文件  
  ex.  
  ```sh
  #!/bin/sh

  cmake -G "CodeLite - Unix Makefiles" -DCMAKE_BUILD_TYPE=Debug
  ```
#### 衍生文件

#### 构建方式

+ "in-source build", 内部构建

+ "out-of-source build", 外部构建 **推荐使用**(将编译输出文件和源文件放到不同的目录中)  
  1. `mkdir build && cd build`
  2. `cmake ..`
  3. `make`

_Cherno_ 教程中的CMake用法，  
先通过cmake指令在codelite工作目录下建立相关的工程文件，  
再编程，  
后利用codelite的内建命令进行修改CMake项目文件和编译

**操作过程** (外部构建)
1. 手动编写"CMakeLists.txt"文件  
2. `makedir build && cd build`
2. 执行`cmake ..`命令生成"Makefile"  
3. 执行`make`进行编译  

### Cherno CMakeLists.txt 学习

原始文件  

```CMake
cmake_minimum_required (VERSION 3.31)

project (HelloWorld)

set (CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -Wall -Werror -std=c++17")
set (source_dir "${PROJECT_SOURCE_DIR}/src")

file (GLOB source_files "${source_dir}/*.cpp")

add_executable (HelloWorld ${source_files})

```

### 操作实例 1

+ "Project_Path": "/mnt/c/Workspace/workspaces/CppWrkspces/lessons/lin64/ProjFromI8/XiaoBing1016/clsSwapExercise"  

+ "CMakeLists.txt"  
  + "File_Path":   
    "/mnt/c/Workspace/workspaces/CppWrkspces/lessons/lin64/ProjFromI8/XiaoBing1016/clsSwapExercise/build/CMakeLists.txt"
  + "code"  
    ```CMake
    cmake_minimum_required(VERSION 3.10)
    
    project(SWAP)
    
    include_directories(include)
    
    add_executable(mainCmake main.cpp src/swap.cpp)

    ```

+ Operating Steps

  1. `makedir build && cd build`  
  2. `cmake ..`
  3. `make`

