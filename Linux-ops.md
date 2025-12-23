# linux操作

## linux命令

+ `alias`

+ `chmod`

+ `chown`

+ `date`

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

  + windows下

    `date /T` <==> `echo %date%`
    `time /T` <==> `echo %time%`

+ `dirname`

+ `file`

+ `find`
  文件/目录查找命令。

  + 参数

  + 示例

+ `echo`

+ `getfacl`

+ `head`

+ `history`

+ `host`

+ `hostname`

+ `ifconfig`

+ `ip`

+ `kill`

+ `ls`
  罗列指定目录下的文件和子目录

  常用参数
  + `-a` -- all

  + `-l` -- long listing name

  + `-t` -- 按修改时间排序

  + `-r` -- 倒序排列

+ `netstat`

+ `split`

  示例：`split -l 行数 文件名`

+ `pkill`

+ `ps`

+ `tail`

+ `tar`

+ `tee`

  + 参数 `-a`, `--append`。 追加到文件末尾
  + 参数 `-i`, `--ignore-interrupts`。 忽略中断信号，如 Ctrl+C
  + 参数 `-p`, `--output-error`。 诊断写入错误的行为模式

+ `timeout`

  须在指定时间(秒)内完成，如`timeout 900 ping baidu.com`

+ `top`

+ `unalias`

+ `vi`

+ `vim`

+ `w`

+ `wc`

  + 参数`-l`, line counts
  + 参数`-w`, word counts
  + 参数`-c`, byte counts
  + 参数`-m`, character counts

+ `who`

## shell

`echo $SHELL`

+ Bourne Shell - `sh`

+ Bourne Again Shell - `bash`

+ C Shell - `csh`

+ TENEX C Shell - `tcsh`

+ Z Shell - `zsh`

+ Friendly Interactive Shell - `fish`

## 参数，返回值

`$0` 脚本名
`$$` 进程ID
`$!` 后台进程PID。如未使用&，则`$!`返回空或错
`$?` 上一命令返回值
`${1}` ...... `{$n}` 传入参数
`$#` 参数个数
`$@` 以列表形式返回参数列表。`“$@"`返回保留参数中`"`对包裹的空格；`$?@: -1}`取最后一个参数

## 判断

`[ ! -d 目录路径 ] && mkdir -p 目录路径`
`[ -f 文件路径 ] && rm -f 文件路径`

## 专题讨论

### `grep`, `sed`, `awk`
