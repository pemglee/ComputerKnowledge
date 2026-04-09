# Linux Directory Descriptions

## Overview

+ "/", 根目录

  + "afs"

  + "bin", Binary, 可执行的二进制文件。

  + "boot", 启动Linux的核心文件，包括链接文件和镜像文件

  + "dev", 设备目录（主要是**外接设备**），挂载后可使用。

  + "etc", 系统配置文件等

  + "home", "root"外的用户目录

  + "lib", 系统动态链接库

  + "lib64"

  + "lost+found"

  + "media", 自动识别设备

  + "mnt", 挂载设备

  + "opt", 可选软件

  + "proc", Linux运行时的进程文件

  + "root", root用户的目录

  + "run"

  + "sbin", super binary, 供*root权限用户*执行的可执行文件

  + "selinux"

  + "srv", 系统服务

  + "sys"

  + "tmp", 临时目录

  + "usr", 用户自己安装的应用程序

    + "bin"

    + "sbin"

    + "src"

  + "var", 系统程序日志的存放目录

## linux file


### soft-link v.s. hard-link


  |  | hard-link | soft-link |
  | :---- | :---- | :----    |
  | brief | 同一个文件，不同文件名 | 快捷方式，指向统一文件 |
  | mechanism | 和原文件共用同一个inode(文件索引) | 独立文件，其内容为原文件路径，类似Windows的快捷方式 |
  | 跨分区/磁盘 | 否。 inode只对本分区有效；跨分区，indoe会重复，无法建立 | 可。 存放的是文件路径 |
  | 作用于目录 | 否。 防止循环目录结构 | 可。 `ls -s real_dir link_dir` |
  | deleted | 删除原文件，链接文件依然可用，数据不会丢失。所有硬链接删除后，文件才会被真正删除 | 删除原文件，链接失效，成为坏链接 |
  | `ls -l` | 文件类型标记为 '-'，和普通文件一样 | 文件类型标记为 'l'，标识为link |
  | 占用空间 | 几乎不占用，只是多一个目录项 | 占用极少，保存了路径信息 |
  | 使用场景 | 防止误删文件；同一文件，多处使用，保持严格的一致且保证有效；节省空间 | 给目录做快捷方式；跨分区引用文件；版本切换(ex, ln -s jdk jdk-1.8) | 

