# DEBUGI INFO PRINT

## print info with DATA, TIME, and LINE-NUMBER

### libraries

`#include <iostream>`    针对普通std::cout输出

`#include <cstdlib>`     针对相关环境变量，如 DEBUG=1 等设置

`#include <fstream>`     针对程序的执行日期、时间、和代码行号

### header

```C++
/*
 * file name: test.h
 */

#include <iostream>
#include <cstdlib>
#include <fstream>

int _DEBUG_ = 0;
```

### source

```C++
/*
 * file name: test.cc
 */

# include "test.h"
int main()
{
    const char *envDebug = std::getenv("DEBUG");
    if ( envDebug != nullptr )
        _DEBUG_ = atoi(envDebug);
    else
        _DEBUG_ = 0;

    if ( _DEBUG_ ) std::cout << __DATE__ << " " << __TIME__ << " [test.cc " << __LINE__ << " / main()] Debug-info" << std::endl;
    return 0; 
}
```
