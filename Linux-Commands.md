# linux命令

## Overview

`command [options] [op-objects]`
+ ex `ls -lah /home ./`

  + "command": `ls`

  + "options": `-lah`

  + "op-objects": `/home ./`

## linux command list

### `head`

见 `tail` 命令

### `ls`

**L**i**S**t directory contents

#### options

+ `-a`, all

+ `-l`, long listing name

+ `-t`, 按时间排序

+ `-r`, 反向排序

### `ps`

#### 命令实例

+ `-elf` 选项

  ```sh
  ps -elf
  ```
  
  1. F,
  1. S,
  1. UID,
  1. PID,
  1. PPID,
  1. C,
  1. PRI,
  1. NI,
  1. ADDR,
  1. SZ,
  1. WCHAN,
  1. STIME,
  1. TTY,
  1. TIME,
  1. CMD,

+ `-aux` 选项

  ```sh
  ps -aux
  ```
  
  1. USER,
  1. PID,
  1. %CPU,
  1. %MEM,
  1. VSZ, 虚拟内存
  1. RSS, 常驻内存
  1. TTY, 终端
  1. STAT, 运行状态
    + R
    + S
    + D
    + T
    + Z
    + X
    + I
    + P
  1. START,
  1. TIME,
  1. COMMAND,

### `pwd`

**P**rint current **W**orking **D**irectory

### `shutdown`

#### windows

```cmd
shutdown /r /f /t 1200
```

+ `/r` 重启, `/s` 关机, `/h` 休眠/挂起
+ `/f` 强制
+ `/t 1200` 等待1200秒之后执行

### `tail`
