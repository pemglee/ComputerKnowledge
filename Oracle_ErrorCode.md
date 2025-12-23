# Oracle Database Error-Code

## code list

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
