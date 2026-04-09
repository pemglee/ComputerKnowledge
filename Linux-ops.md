# linux操作

## linux命令

[linux命令学习笔记](./Linux-Commands.md)

## linux启动过程

+ BIOS (Basic Input Output System) / EFI (Extensible Firmware Interface)
  + [说明] 
  + [动作]
    硬件检查，查找或加载硬盘上的MBR

+ MBR (Master Boot Record)
  + [说明] 
  + [动作]
    存储 BootLoader信息，加载GRUB

+ GRUB (GRand Unified Bootloader)
  + [说明]
  + [动作]
    查找并加载kernel
  
+ Kernel
  + [说明] 内核
  + [动作]
    + 加载驱动
    + 挂载 rootfs
    + 执行 /sbin/init

+ Init
  + [说明] 初始化
  + [动作]
    + OS初始化
    + 执行runlevel相关程序

+ Runlevel
  + [说明]
  + [动作] 
    启动指定级别的服务

 
## shell

`echo $SHELL`

+ Bourne Shell - `sh`

+ Bourne Again Shell - `bash`

+ C Shell - `csh`

+ TENEX C Shell - `tcsh`

+ Z Shell - `zsh`

+ Friendly Interactive Shell - `fish`

### 参数，返回值

+ `$0` 脚本名  
+ `$$` 进程ID  
+ `$!` 后台进程PID。如未使用&，则`$!`返回空或错  
+　`$?` 上一命令返回值  
+ `${1}` ...... `{$n}` 传入参数  
+ `$#` 参数个数  
+ `$@` 以列表形式返回参数列表。
  + `“$@"` 返回保留参数中`"`对包裹的空格, 即以字符串的形式返回；
  + `$?@: -1}`取最后一个参数  

### 判断

+ `[ ! -d 目录路径 ] && mkdir -p 目录路径`
+ `[ -f 文件路径 ] && rm -f 文件路径`

## 专题讨论

### 巡检

1. 查状态
   + 系统版本
   + CPU
   + 内存
   + 硬盘
   + 网络

2. 打补丁
3. 关root
   采用“普通用户 + 临时授权” 方式

4. 开密钥
   只开密钥登录，关闭密码登录，即关闭“ssh”

5. 开防火墙

6. 配置(基础)环境
   + 配置基础环境
   + 安装基础工具/命令
   + 时间同步

### 系统版本

### CPU + MEM

### DISK

### Network

+ 端口数量
  + [默认] 65535
  +

+ 连接数量

  + 文件描述符
    linux下，一切皆文件；TCP连接数<-->文件描述符数量
    + [默认] 1024
    + [调整] 理想值 = 65535+ 
    + [ErrorMsg] too many open files

  + 内存
    每个连接约占用4K内存

  + 端口号
    
  + CPU限制
    可使用高性能CPU + Epoll技术，即多路复用
    
### 查找

### `grep`, `sed`, `awk` 

### 负载均衡

#### LVS

#### nginx