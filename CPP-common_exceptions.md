# Common Exceptions

## CONVERT

### ERROR, 'const_cast' on 'char' to 'char*'

`error: invalid 'const_cast' from type 'char' to type 'char*'`

### ERROR, 'const char*' to 'char*'

`error: invalid conversion from 'const char*' to 'char*' [-fpermissive]`

### ERROR, 'int' to 'const char*'

`error: invalid conversion from 'int' to 'const char*' [-fpermissive]`

### ERROR,  'void*' to '数据类型*'

`error: invalid conversion from 'void*' to 'sCOMMDATA*' {aka 'CommodityData*'} [-fpermissive]`

#### ex1-summit_customization

##### Original

```C++
    // sCOMMDATA *pCommData;
    pCommData = sGetListItem(pCommDataList,1);
```

##### Modified

```C++
    // sCOMMDATA *pCommData;
    pCommData = static_cast<sCOMMDATA*>(sGetListItem(pCommDataList,1));
```

### WARNING， 'string' to 'char*'

`warning: ISO C++ forbids convert a string constant to 'char*' [-Wwrite-strings]`  

#### ex1-summit_customization  

##### Original

```C++
    cWriteLog(__FILE__, __LINE__, "Expired trade won't be processed.");
```

##### Modified

```C++
    cWriteLog(__FILE__, __LINE__, (char*)("Expired trade won't be processed."));
```

#### ex2-summit_customization

##### Original

```C++
    char* tMapName = "PROTYPE_SY";
```

##### Modified

```C++
    char* tMapName = (char*)"PROTYPE_SY";
```

#### ex3-summit_customization

##### Orginal

```C++
    cWriteLog( __FILE__, __LINE__, "out CheckCreditLimits, and count is : [%d], output is [%s]", count, output)；
```

##### Modified

```C++
    char* tempString = (char*)"";
    sprintf(tempString, "out CheckCreditLimits, and count is : [%d], output is [%s]", count, output);
    cWriteLog( __FILE__, __LINE__, tempString)；
```

## undefined
