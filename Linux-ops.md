# linux操作

## linux命令

[linux命令学习笔记](./Linux-Commands.md)

## shell

`echo $SHELL`

+ Bourne Shell - `sh`

+ Bourne Again Shell - `bash`

+ C Shell - `csh`

+ TENEX C Shell - `tcsh`

+ Z Shell - `zsh`

+ Friendly Interactive Shell - `fish`

### 参数，返回值

`$0` 脚本名  
`$$` 进程ID  
`$!` 后台进程PID。如未使用&，则`$!`返回空或错  
`$?` 上一命令返回值  
`${1}` ...... `{$n}` 传入参数  
`$#` 参数个数  
`$@` 以列表形式返回参数列表。`“$@"`返回保留参数中`"`对包裹的空格；`$?@: -1}`取最后一个参数  

### 判断

`[ ! -d 目录路径 ] && mkdir -p 目录路径`
`[ -f 文件路径 ] && rm -f 文件路径`

## 专题讨论

### 查找

### `grep`, `sed`, `awk`
