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

int _DEBUG_UTL_ = 0;
```

### source

```C++
/*
 * file name: test.cc
 */

# include "test.h"
int main()
{
        const char *pDebugUTL = std::getenv("DEBUG_UTL");

        if ( pDebugUTL != nullptr )
                _DEBUG_UTL_ = atoi(pDebugUTL);
        else
                _DEBUG_UTL_ = 0;

        if (_DEBUG_UTL_) std::cout << __DATE__ << " " << __TIME__ << " [" << __FILE__ << " " << __FUNCTION__ <<" " << __LINE__ << "] DEGUB ON " << std::endl;

        return 0;
}
```

output:
```sh
┌──(edgar㉿ThinkPadT14P-23)-[/mnt/c/Workspace/workspaces/CppWrkspces/lessons/lin64/test]
└─$ export DEBUG_UTL=1

┌──(edgar㉿ThinkPadT14P-23)-[/mnt/c/Workspace/workspaces/CppWrkspces/lessons/lin64/test]
└─$ ./debugtest
Jan 20 2026 23:59:10 [AddDebugInfo.cc:15 main] DEGUB ON

┌──(edgar㉿ThinkPadT14P-23)-[/mnt/c/Workspace/workspaces/CppWrkspces/lessons/lin64/test]
└─$
```
