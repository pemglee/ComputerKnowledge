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
  
  +  1 F,
  +  2 S,
  +  3 UID,
  +  4 PID,
  +  5 PPID,
  +  6 C,
  +  7 PRI,
  +  8 NI,
  +  9 ADDR,
  + 10 SZ,
  + 11 WCHAN,
  + 12 STIME,
  + 13 TTY,
  + 14 TIME,
  + 15 CMD,

+ `-aux` 选项

  ```sh
  ps -aux
  ```
  
  +  1 USER,
  +  2 PID,
  +  3 %CPU,
  +  4 %MEM,
  +  5 VSZ, 虚拟内存
  +  6 RSS, 常驻内存
  +  7 TTY, 终端
  +  8 STAT, 运行状态
    + R
    + S
    + D
    + T
    + Z
    + X
    + I
    + P
  +  9 START,
  + 10 TIME,
  + 11 COMMAND,

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
