---
title: Java异常
markmap:
  colorFreezeLevel: 24
---

## Java Exception

+ [diagram]
  + ![Java Error and Exceptions](./images2/JavaErrExcep.drawio.260410.svg)

+ Error, 严重错误，一般无法处理

  + OutOfMemoryError
  + NoClassDefFoundError
  + StackOverflowError

+ Exception，运行时错误，可以捕获并被处理

  + RuntimeException
    + NullPointerException (NPE,空指针异常。实为 Null Reference， 对象为空)
    + IndexOutOfBoundsException
    + SecurityException
    + IllegalArgumentException
  + IOException 
    + UnsupportedCharsetException
    + FileNotFoundException
    + SocketException
  + ParseExcepton
  + GeneralSecurityException
  + SQLException
  + TimeoutException

  + NumberFormatException

## Java Error/Exceptions explain

+ java

  + lang

    + ClassNotFoundException
      指定路径下没有相关的 .class 文件
