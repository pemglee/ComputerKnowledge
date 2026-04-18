---
title: Java学习 练习项目
markmap:
  colorFreezeLevel: 24
---

## Develop Environment

+ JDK
  + URL
    + Eclipse 
      + [Download URL](https://adoptium.net/installation/)
    + Oracle JDK 

  + Environment Variables
    + $JAVA_HOME / %JAVA_HOME%
      + windows

        ```batch
        set JAVA_HOME=C:\Workspace\ProgramFiles\openjdk-17
        set JRE_HOME=%JAVA_HOME%\jre
        set CLASSPATH=.;%JAVA_HOME%\lib;%JRE_HOME%\lib;%JAVA_HOME%\lib\tools.jar;%JAVA_HOME%\src.zip    
        ```

    + $PATH / %PATH%
      + linux 
        `export PATH=$JAVA_HOME/bin:$PATH`  
      + windows
        `set PATH=%JAVA_HOME%\bin;%PATH%`  

  + check version
    `java -version`

+ Maven
  + URL
    + [Apache]
  + Environment Variables
    + $MAVEN_HOME / %MAVEN_HOME%
      + windows
        `set MAVEN_HOME=C:\Workspace\JavaProjects\apache-maven-3.9.14`
    + $PATH
      + windows
        `set PATH=%MAVEN_HOME%\bin;%PATH%`
  + check version
    set java environment
    `mvn -v`

+ ~~Spring~~

+ IDE: 

  + About

    ```text
    IntelliJ IDEA 2026.1
    Build #IU-261.22158.277, built on March 25, 2026
    Source revision: 89c647576f1d2
    Licensed to Trial User
    Subscription is active until May 13, 2026.
    Runtime version: 25.0.2+1-b329.72 amd64137.0.17-261-b65
    VM: OpenJDK 64-Bit Server VM by JetBrains s.r.o.
    Toolkit: sun.awt.windows.WToolkit
    Windows 11.0
    Exception reporter ID: 24032619524298a-bc8d-4329-bbde-474211fefe90
    GC: G1 Young Generation, G1 Concurrent GC, G1 Old Generation
    Memory: 2048M
    Cores: 20
    Registry:
      ide.experimental.ui=true
      trace.state.event.service.url=https://api.jetbrains.cloud/trace-status
    Non-Bundled Plugins:
      intellij.jupyter (261.22158.354)
      com.intellij.spring (261.22158.354)
      Subversion (261.22158.354)
      hg4idea (261.22158.185)
      IdeaVIM (2.30.0)
      PerforceDirectPlugin (261.22158.185)
      Docker (261.22158.299)
      com.jetbrains.plugins.webDeployment (261.22158.299)
      org.jetbrains.plugins.remote-run (261.22158.354)
    Kotlin: 261.22158.277-IJ
    ```

  + 设置
    + edit "idea64.exe.vmoptions"
      + content
        + [code]
          ```text
          -Xms1024m
          -Xmx4096m
          -XX:JbrShrinkingGcMaxHeapFreeRatio=40
          -XX:ReservedCodeCacheSize=512m
          -XX:+HeapDumpOnOutOfMemoryError
          -XX:-OmitStackTraceInFastThrow
          -XX:CICompilerCount=2
          -XX:+IgnoreUnrecognizedVMOptions
          -XX:+UnlockDiagnosticVMOptions
          -XX:TieredOldPercentage=100000
          -ea
          -Dsun.io.useCanonCaches=false
          -Dsun.java2d.metal=true
          -Djbr.catch.SIGABRT=true
          -Djdk.http.auth.tunneling.disabledSchemes=""
          -Djdk.attach.allowAttachSelf=true
          -Djdk.module.illegalAccess.silent=true
          -Djdk.nio.maxCachedBufferSize=2097152
          -Djava.util.zip.use.nio.for.zip.file.access=true
          -Dkotlinx.coroutines.debug=off
          -Dskiko.rendering.useScreenMenuBar=false
          -Djava.nio.file.spi.DefaultFileSystemProvider=com.intellij.platform.core.nio.fs.MultiRoutingFileSystemProvider
          ```

  + plugins

## 《Java核心编程 12Ed / 机械工业出版社 / ISBN:978-7-111-70641-0》

## 《Spring Boot 3核心技术与最佳实践 / 电子工业出版社 / ISBN:978-7-121-45290-1》

### 章节1.3 项目

#### Spring Boot

+ 步骤

  + 创建项目

    + Server URL: "start.spring.io"
    + Name: "boot3chapter1_3"
    + Location: "C:\Workspace\workspaces\JavaWrkspces\SpringExercise\Book-SpringBoot3"
    + Language: "Java"
    + Type: "Maven"
    + Group: "net.edgarworld.book.springboot3"
    + Aritfact: "boot3chapter1_3"
    + Package name: "net.edgarworld.book.springboot3.boot3chapter1_3"
    + JDK: "17 _Oracle OpenJDK 17_"
    + Java: "17 - Sealed types, always-strict floating-point semantics"
    + Packaging: "Jar"

    + Dependencies
      + Developer Tools
        + Spring Boot DevTools
        + Lombok
        + Spring Configuration Processor
      + Web
        + Spring Web

    + 项目目录
      + 结构
        + [DirTree]

          ```text
          C:\Workspace\workspaces\JavaWrkspces\SpringExercise>tree Book-SpringBoot3
          Folder PATH listing
          Volume serial number is A60C-E80B
          C:\WORKSPACE\WORKSPACES\JAVAWRKSPCES\SPRINGEXERCISE\BOOK-SPRINGBOOT3
          └───boot3chapter1_3
              ├───.idea
              ├───.mvn
              │   └───wrapper
              └───src
                  ├───main
                  │   ├───java
                  │   │   └───net
                  │   │       └───edgarworld
                  │   │           └───book
                  │   │               └───springboot3
                  │   │                   └───boot3chapter1_3
                  │   └───resources
                  │       ├───static
                  │       └───templates
                  └───test
                      └───java
                          └───net
                              └───edgarworld
                                  └───book
                                      └───springboot3
                                          └───boot3chapter1_3
          
          ```

        + 说明
          + [R] /
            + [D] .idea
            + [D] .mvn
            + [D] src
              + [D] main
                + [D] java
                  + [D] net
                    + [D] edgarworld
                      + [D] book
                        + [D] springboot3
                          + [D] boot3chapter1_3
                            + [f] Boot3chapter13Application.java
              + [D] test
                + [D] java
                  + [D] net
                    + [D] edgarworld
                      + [D] book
                        + [D] springboot3
                          + [D] boot3chapter1_3
                            + [f] Boot3chapter13ApplicationTest.java
            + [f] .gitattributes
            + [f] .gitignore
            + [f] HELP.md
            + [f] mvnw
            + [f] mvnw.cmd
            + [f] pom.xml

## 《bilibili，动力节点，SpringBoot4从入门到精通，适合小白的SpringBoot4视频教程》

+ [视频教程](https://www.bilibili.com/video/BV1iykjB1Ewc?spm_id_from=333.788.videopod.episodes&vd_source=38fc599412349dcfe60484e3ff320c66&p=4)

### 章节 

+ 步骤

  + 创建项目

    + Generators
      + "Spring Boot"
    + --
    + Project
      + Server URL: "start.spring.io"
      + Name: "demo01"
      + Location: "C:\Workspace\workspaces\JavaWrkspces\SpringExercise\Bili-SpringBoot4"
      + Language: "Java"
      + Type: "Maven"
      + Group: "net.edgarworld.book.springboot4"
      + Artifact: "demo01"
      + Package name: "net.edgarworld.book.springboot4.demo01"
      + JDK: "Oracle OpenJDK 17 _c:/workspace/ProgramFiles/openjdk-17_"
      + Java: "17 - Sealed types, always-strict floating-point semantics"
      + Packaging: "Jar"
    + --
    + Dependencies
      + Developer Tools
        + Spring Boot DevTools
        + Lombok
        + Spring Configuration Processor
      + Web
        + Spring Web

## 参考

+ [jetbrains.com.cn](https://www.jetbrains.com.cn/)
  + [JVM 框架]()
    + [Spring]()
      + [Spring Boot](https://www.jetbrains.com.cn/help/idea/spring-boot.html)