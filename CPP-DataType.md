# C++ 数据类型

[cppreference.com, Arithmetic types (英文)](https://en.cppreference.com/w/c/language/arithmetic_types)  
[cppreference.com, Arithmetic types (中文)](https://zh.cppreference.com/w/c/language/arithmetic_types)  

## 概述

定义了数据元素的内容，还定义了可以在这数据上的操作。

**！**注意，**最小尺寸**的提法。一般情况下，参考**字节**标定  
```
2 ^  7 =                        128  // 4 signed
2 ^  8 =                        256  // 4 unsigned

2 ^ 15 =                     32,768  // 4 signed
2 ^ 16 =                     65,536  // 4 unsigned

2 ^ 31 =              2,147,483,648  // 4 signed
2 ^ 32 =              4,294,967,296  // 4 unigned  

2 ^ 63 =  9,223,372,036,854,775,808  // 4 signed
2 ^ 64 = 18,446,744,073,709,551,616  // 4 unsigned
```

| 类型 | 含义 | 最小尺寸(bit) | 字节(Byte) | 范围 | 说明A | 说明B |
| :---- | :---- | ----: | ----: | :----: | :---- | :---- |
| bool | 布尔类型 | N/A |  |  | true \| falses |  |
| char | 字符 | 8 | 1 |  | char = (unsigned char \| signed char) | char是(最)基本的数据类型，即**char**的大小和**机器字节**相同 |
| unsigned char | 无符号字符 | 8 | 1 | 0 ~ 255 |  |  |
| signed char | 带符号字符 | 8 | 1 | -128 ~ 127 |  |  |
| wchar_t | 宽字符 | 16 |  |  |  |  |
| char16_t | Unicode字符 | 16 |  |  |  |  |
| char32_t | Unicode字符 | 32 |  |  |  |  |
| short | 短整型 | 16 | 2 | -32768 ~ 32767 |  |  |
| short int | 短整型 | 16 | 2 | -32768 ~ 32767 |  |  |
| unsigned short int | 短整型 | 16 | 2 | 0 ~ 65535 |  |  |
| signed short int | 短整型 | 16 | 2 | -32768 ~ 32767 |  |  |
| int | 整型 | 16 | 4 | -2147483648 ~ 2147483647 |  | int类型应该位32位 |
| unsigned int | 无符号整数 |  | 4 | 0 ~ 4294967295 |  |  |
| signed int | 符号整数 |  | 4 | -2147483648 ~ 2147483647 |  |  |
| long | 长整型 | 32 | 8 |  |  |  |
| long int | 长整型 | 32 | 8 |  |  |  |
| unsigned long int | 长整型 | 32 | 8 |  |  |  |
| signed long int | 长整型 | 32 | 8 |  |  |  |
| long long | 长整型 | 64 |   |  |  |  |
| float | 单精度浮点数 | 6 |  |  |  | 6位有效数字 |
| double | 双精度浮点数 | 10 |  |  |  | 10位有效数字 |
| long double | 扩展精度浮点数 | 10 |  |  |  | 10位有效数字 |
|  |  |  |  |  |  |  |


### . 位(bit)、字节(Byte)、字(word)


## 内置类型/built-in type

*内置类型* 分为 *算术类型* 和 *空类型*。  

### . void  

### . 布尔类型  

### . 整数类型

整数类型简表:  
位宽 -- 数据模型中的位宽  

| 类型说明符 | 等价类型 | 位宽 - C标准 | 位宽 - LP32 | 位宽 - ILP32 | 位宽 - LLP64 | 位宽 - LP64 | 说明A | 说明B |  
| :---- | :---- | ----: | ----: | ----: | ----: | ----: | :---- | :---- |  
|  |  |  |  |  |  |  |  |  |  
| short | short int | 16 | 16 | 16 | 16 | 16 |  |  |  
| short int | short int | 16 | 16 | 16 | 16 | 16 |  |  |  
| singed short | short int | 16 | 16 | 16 | 16 | 16 |  |  |  
| singed short int | short int | 16 | 16 | 16 | 16 | 16 |  |  |  
| unsigned short | unsigned short int | 16 | 16 | 16 | 16 | 16 |  |  |  
| unsigned short int | unsigned short int | 16 | 16 | 16 | 16 | 16 |  |  |  
| int | int | 16 | 16 | 32 | 32 | 32 |  |  |  
| signed | int | 16 | 16 | 32 | 32 | 32 |  |  |  
| signed int | int | 16 | 16 | 32 | 32 | 32 |  |  |  
| unsigned | unsigned int | 16 | 16 | 32 | 32 | 32 |  |  |  
| unsigned int | unsigned int | 16 | 16 | 32 | 32 | 32 |  |  |  
| long | long int | 32 | 32 | 32 | 64 | 64 |  |  |  
| long int | long int | 32 | 32 | 32 | 64 | 64 |  |  |  
| signed long | long int | 32 | 32 | 32 | 64 | 64 |  |  |  
| signed long int | long int | 32 | 32 | 32 | 64 | 64 |  |  |  
| unsigned long | unsigned long int | 32 | 32 | 32 | 64 | 64 |  |  |  
| unsigned long int | unsigned long int | 32 | 32 | 32 | 64 | 64 |  |  |  
| long long | long long int | 64 | 64 | 64 | 64 | 64 |  |  |  
| long long int | long long int | 64 | 64 | 64 | 64 | 64 |  |  |  
| signed long long | long long int | 64 | 64 | 64 | 64 | 64 |  |  |  
| signed long long int | long long int | 64 | 64 | 64 | 64 | 64 |  |  |  
| unsigned long long | unsigned long long int | 64 | 64 | 64 | 64 | 64 |  |  |  
| unsigned long long int | unsigned long long int | 64 | 64 | 64 | 64 | 64 |  |  |  
|  |  |  |  |  |  |  |  |  |  


**注意**，
1. 《C++ Primer Ed. 5th》，int 最小尺寸为16位，但64位系统上，其尺寸为32位。  

### . 字符类型  
signed char  

unsigned char  

char  

wchar_t 宽字符型  
类型定义:  
```C++
typede short int wchar_t
```

char16_t  

char32_t  


### . float 浮点型  

### . double 双精度/双浮点'型  


## 类型转换

## 类型修饰符

### . signed

### . unsigned

### . short

### . long


## 内置类型程序演示

### . 源代码

[示例代码 ExampleCode001/CPP_Type-000001.cpp](./CppPrimer/ExampleCode001/CPP_Type-000001.cpp)


#### .. 运行结果
source_code: `/mnt/c/Workspace/workspaces/CppWrkspces/lesson/src/DataType/CPP-BuildIn_DataType-211016a.cpp`  

```shell
$ ./datatype_2511
type:           ***************size***************
bool:           所占字节数: 1   最大值: 1                       最小值: 0
char:           所占字节数: 1   最大值:                         最小值: ▒
signed char:    所占字节数: 1   最大值:                         最小值: ▒
unsigned char:  所占字节数: 1   最大值: ▒                       最小值:
wchar_t:        所占字节数: 2   最大值: 65535                   最小值: 0
short:          所占字节数: 2   最大值: 32767                   最小值: -32768
int:            所占字节数: 4   最大值: 2147483647              最小值: -2147483648
unsigned:       所占字节数: 4   最大值: 4294967295              最小值: 0
long:           所占字节数: 8   最大值: 9223372036854775807     最小值: -9223372036854775808
long int:       所占字节数: 8   最大值: 9223372036854775807     最小值: -9223372036854775808
long long:      所占字节数: 8   最大值: 9223372036854775807     最小值: -9223372036854775808
unsigned long:  所占字节数: 8   最大值: 18446744073709551615    最小值: 0
double:         所占字节数: 8   最大值: 1.79769e+308            最小值: 2.22507e-308
long double:    所占字节数: 16  最大值: 1.18973e+4932           最小值: 3.3621e-4932
float:          所占字节数: 4   最大值: 3.40282e+38             最小值: 1.17549e-38
size_t:         所占字节数: 8   最大值: 18446744073709551615    最小值: 0
string:         所占字节数: 8   最大值:                         最小值:
```
