# Oracle Database Error-Code

## code list

### "ORA-00933: SQL command not propertly ended"

执行SQL语句时，命令没有被正确地结束，从而导致语法错误。

### "ORA-00936: Missing Expression"

缺乏表达式，如
+ 函数，`chr(38)` 写成了 `char(38)`
+

### "ORA-01034: ORACLE not available"

数据实例未启动

### "ORA-01406: fetched column value was truncated"

`$ oerr ora 1406`

```text
01406, 00000, "fetched column value was truncated"
// *Cause: The fetched column values were truncated.
// *Action: Use the right data types to avoid truncation.
```

提示为，使用一致的字符类型避免被截断。

出现这种情况，也比较好判断，建议客户检查如下信息
1.变量值和表字段类型是否一致
2.数据库字符集与客户端字符集是否一致

### "ORA-01465: invalid hex number"

无效的十六进制数字

### "ORA-01756: quoted string no properly terminated"

“引号字符串未正确终止”  
