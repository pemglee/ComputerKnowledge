# Qt & IDE QtCreator

## Qt & QtC++

### Qt class library

+ (Qt) Core

+ (Qt) Network

+ (Qt) GUI

+ QML

+ JavaScript

+ QtQuick

+ QtQuickControls

+ QtGraphicalEffects

+ XML

+ Database

+ Multimedia

+ WebEngine

+ WebSockets

+ Widgets

### 内省数据

内省 vs 反射

#### QObject基类

#### Meta 元信息 

信号 和 插槽机制

## QtCreator

+ 创建项目  
  1. 起名  
     "Name":"Chapter2601"  
     "Create in":"/mnt/c/Workspace/workspaces/CppWrkspces/lessons/lin64/Qt6"  
     [x] Use as default projection location
  
  2. 构建  
     "Build System":"CMake for Qt5 and Qt6"

项目目录为"C:\Workspace\workspaces\CppWrkspces\lessons\lin64\Qt6\Chapter2601"

+ 打开项目  
  现在项目目录下的"CMakeLists.txt"

+ 快捷键

  | Function | shortcut | explain |
  | :------- | :------- | :------ |
  | Switch Header/Source | `F4` | 在同名的**头文件**和**源文件**间切换 |
  | Follow Symbol Under Cursor | `F2` | 对于变量，跳转到**声明**； 对于函数，在**声明**和**定义**间切换 |
  | Switch Between Function Declartion and Definition | `Shift+F2` | 函数，在**声明**和**定义**间切换 |
  | Refactor\Rename Symbol Under Cursor | `Ctrl+Shift+R` | 该名称，将替换所有用到这个符号的地方 |
  | Refactor\Add Definition in .cpp |   | 在cpp文件中为**函数原型**生成**函数体** |
  | Auto-indent Selection | `Ctrl+I` | 对选择的文字自动进行缩进 |
  | Toggle Comment Selection | `Ctrl+/` | 注释/取消注释 |
  | Context Help | `F1` | 为贯标所处的文字显示帮助 |
  | Save All | `Ctrl+Shift+S` |  |
  | Find/Replace | `Ctrl+F` |  |
  | Find Next    | `F3` |  |

## Qt Class继承

`QObject` <-- `QCoreApplication` <-- `QGuiApplication` <-- `QApplication`

+ `QObject`  
  所有使用**元对象**系统的类的基类。  
  **不**是所有Q开头的类都是QObject的派生类，如 OString  

+ `QCoreApplication`
  + 为"**非**GUI应用程序"提供**主事件循环**  

+ `QGuiApplication`
  + 为"GUI应用程序"提供**主事件循环**；
  + 初始化GUI所需的资源；
  + 提供字符串本地化、剪贴板、鼠标处理等功能；

+ `QApplication`
  为"Qt Widgets模块"的应用程序提供**主事件循环**

## Meta-Object System

MOC(元对象编译器, Meta-Object Compiler)是一个预处理器，将Qt特性的C++程序转换为标准C++程序；
之后再由标准C++编译器进行编译  
Meta-Object System是C++扩展，更适合组件化GUI编程。  

是对C++的扩展，增加了新的功能  

+ 信号与槽机制  
  只有在 private 部分声明了 Q_OBJECT 宏， MOC才会为为其增加Qt特性
+ 属性  
  动态管理  
+ 内存管理  

## Qt Class

### QObject

QObject**不支持拷贝**，也**不支持赋值**。  
QObject以对象树的结构组织自己。  

+ `QObject.dumpObjectTree()`

+ `OObject.dumpObjectInfo()`

