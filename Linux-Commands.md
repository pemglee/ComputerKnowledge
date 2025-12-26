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

### `tail`
