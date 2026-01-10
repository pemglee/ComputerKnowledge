# C/C++ Input and Output

## C++

### std::cout & related

iostream库，istream + ostream，i.e. input stream & output stream。 

stream，流，i.e. 字符序列，随着时间的推移，字符是顺序生成或消耗的。  

#### IO对象  

**注意**是对象，**不**是类

+ cout

+ cerr

+ clog

+ cin

  `>>`， 运算符，格式化函数

#### headers

`#include <iostream>`
`#include <iomanip>`

#### examples

```C++
cout << setiosflags(ios::fixed) << setprecision(2);
cout << fixed << setprecision(2);
cout << setprecision(2);
```

## C

### printf

#### parameters

+ 小数，浮点数
  + `%a` / `%A`, 十六进制浮点数  
  + `%f`, 浮点数。ex. `%.6f`保留小数点后6位的小数
  + `%e` / `%E`, 指数形式
  + `%g` / `%G`, 根据数值大小自动选择十进制或科学计数法输出浮点数

+ 整数
  + `%o`, 八进制__无符号__整数  
  + `%d`, 十进制__带符号__整数  
  + `%u`, 十进制__无符号__整数
  + `%x` / `%X`, 十六进制__无符号__整数
  + `%lu`, 32位__无符号__整数
  + `%llu`, 64位__无符号__整数

+ 字符，字符串
  + `%c`, 单个字符
  + `%s`, 字符串

+ 其他
  + `%p`, 地址，指针
