# linux命令

## Overview

`command [options] [op-objects]`
+ ex `ls -lah /home ./`

  + "command": `ls`

  + "options": `-lah`

  + "op-objects": `/home ./`

## linux command list

### `alias`

### `cd`

**C**hange **D**irectory

### `chmod`

### `chown`

### `date`

+ 显示日期
  ```bash
  # date
  Sat Dec 13 01:06:43 AM CST 2025
  ```
  ```bash
  # cal 02 2028
     February 2028
  Su Mo Tu We Th Fr Sa
         1  2  3  4  5
   6  7  8  9 10 11 12
  13 14 15 16 17 18 19
  20 21 22 23 24 25 26
  27 28 29
  ```
  + 日期格式化
    ```bash
    # date +%y%m%d
    251213
    
    # date +%Y%m%d
    20251213
    
    # date +%Y-%m-%d
    2025-12-13
    ```
    ```sh
    # date +%D
    12/13/25
    # date +%m/%d/%y
    12/13/25
    ```
    `date +%D` <==> `date +%m/%d/%y`

+ 日期计算
  ```bash
  # date -d "2 day" +%Y-%m-%d
  2025-12-15
  
  # date -d "-2 day" +%Y-%m-%d
  2025-12-11
  ```
  ```bash
  # date -d "20260301 -2 day" +%Y-%m-%d
  2026-02-27
  
  # date -d "20280301 -2 day" +%Y-%m-%d
  2028-02-28
  ```
  ```bash
  # date -d "20280301 -2 day" +%w
  1
  ```
  1 for Monday

+ 设置日期
  ```bash
  # date -s 250325
  ```
  设置当前日期为 2025 Mar 25

#### windows下

    `date /T` <==> `echo %date%`
    `time /T` <==> `echo %time%`


### `dirname`

### `file`

### `find`

文件/目录查找

### `echo`

### `getfacl`

### `head`

见 `tail` 命令

### `history`

### `host`

### `hostname`

### `ifconfig`

### `ip`

### `kill`

### `ls`

**L**i**S**t directory contents

### `mkdir`

**M**ake **D**irectory.

+ `-p`

### `netstat`

#### options

+ `-a`, all

+ `-l`, long listing name

+ `-h`, 以可读性较高的方式展示

+ `-t`, 按时间排序

+ `-r`, 反向排序

### `pkill`

### `ps`

#### 命令实例

+ `-elf` 选项

  ```sh
  ps -elf
  ```
  
  + " 1"-"F",
  + " 2"-"S",
  + " 3"-"UID", 用户
  + " 4"-"PID", 进程
  + " 5"-"PPID", 父进程
  + " 6"-"C",
  + " 7"-"PRI",
  + " 8"-"NI",
  + " 9"-"ADDR",
  + "10"-"SZ",
  + "11"-"WCHAN",
  + "12"-"STIME",
  + "13"-"TTY",
  + "14"-"TIME",
  + "15"-"CMD",

+ `-aux` 选项

  ```sh
  ps -aux
  ```
  
  + " 1"-"USER",
  + " 2"-"PID",
  + " 3"-"%CPU",
  + " 4"-"%MEM",
  + " 5"-"VSZ", 虚拟内存
  + " 6"-"RSS", 常驻内存
  + " 7"-"TTY", 终端
  + " 8"-"STAT", 运行状态
    + R, Running
    + S, Sleeping
    + D, Uninterruptible Sleep
    + T, Stopped
    + Z, Zombied
    + X, Dead
    + I, Idle 空闲
    + P, Paging 分页

  + " 9"-"START",
  + "10"-"TIME",
  + "11"-"COMMAND",

  实例 1, 内存排序前20
  ```sh
  ps -aux | sort -rnk 4 | head -20
  ```

  实例 2, CPU占用前20
  ```sh
  ps -aux | sort -rnk 3 | head -20
  ```

  实例 3, 每隔1分钟打印java进程信息
  ```sh
  for ((;;)) do ps -aux | grep -v grep | grep -i java; sleep 60; done
  ```
  或
  ```sh
  for ((;;)) do clear; ps -aux | grep -v grep | grep -i java; date; sleep 60; done
  ```

#### windows

`tasklist`

```cmd
for /L %N in () do cls & tasklist | findstr /i java & TIMEOUT /T 30 /NOBREAK
```

### `pwd`

**P**rint current **W**orking **D**irectory

### `rm`

**R**e**M**ove.

+ `-r`

+ `-f`, force, 强制删除

### `shutdown`

+ `  ` `--help`
+ `-H` `--halt`, Halt the machine
+ `-P` `--poweroff`
+ `-r` `--reboot`
+ `-h` `        `, Equivalent to `--poweroff`, overridden by `--halt`
+ `-k` `        `, Don't halt/power-off/reboot, just send warnings
+ `  ` `--no-wall`, Don't send wall message before halt/power-off/reboot
+ `-c` `        `, Cancel a pending shutdown
+ `  ` `--show`, Show pending shutdown

```sh
shutdown -h 20
```

20分钟后，系统关机。

#### windows

```cmd
shutdown /r /f /t 1200
```

+ `/r` 重启, `/s` 关机, `/h` 休眠/挂起
+ `/f` 强制
+ `/t 1200` 等待1200秒之后执行

### `split`

示例: `split -l 行数 文件名`

### `tail`

### `tar`

### `tee`

### `timeout`

须在指定时间(秒)内完成。 如 `timeout 900 ping baidu.com`

### `top`

### `touch`

### `tree`

### `unalias`

### `vi` & `vim`

### `w`

### `wc`

  + 参数`-l`, line counts

  + 参数`-w`, word counts

  + 参数`-c`, byte counts
  
  + 参数`-m`, character counts

### `who`
