---
title: MySql数据类型
markmap:
  colorFreezeLevel: 24
---

# Data Type

## overview

DBSC7 -- Database System Concept 7th Edition

| DBSC7            | Oracle        | MySQL     | MS-SQL | Remark 1              | Remark 2 |
| :--------------- | :------------ | :-------- | :----- | :-------------------- | :------- |
| char(n)          | char()        |           |        | character             | 定长字符串，会用空格填充来达到其最大长度，默认为1。 |
|                  | nchar()       |           |        | unicode character     |          |
| varchar(n)       | ~~varchar()~~ |           |        | character varying     |          |
|                  | varchar2()    |           |        |                       |          |
|                  | nvarchar2()   |           |        | unicode var character |          |
|                  |               | tinyint   |        |                       |          |
| smallint         |               | smallint  |        |                       |          |
|                  |               | mediumint |        |                       |          |
| int              | integer       | int       |        |                       |          |
|                  |               | bigint    |        |                       |          |
| numeric(p,d)     | number(p,d)   |           |        |                       |          |
| real             | binary_float  |           |        |                       |          |
| double precision | binary_double |           |        |                       |          |
| float(n)         | float         |           |        |                       | 精度至少为n位的浮点数 | 


p -- 总位数
s -- 小数位数

## Data Type in MySQL

### 数值类型

#### 整数类型

| Data Type | Range (signed)                             | Size 1   | Range (unsigned)         | 
| :-------- | :----------------------------------------: | :------- | :----------------------: | 
| tinyint   |                 -128 ~ 127                 | 1 Byte   | 0 ~                  255 | 
| smallint  |               -32768 ~ 32767               | 2 Bytes  | 0 ~                65535 | 
| mediumint |             -8388608 ~ 8388607             | 3 Bytes  | 0 ~             16777215 |
| int       |          -2147483648 ~ 2147483647          | 4 Bytes  | 0 ~           4294967295 |
| bigint    | -9223372036854775808 ~ 9223372036854775807 | 8 Bytes  | 0 ~ 18446744073709551615 |

#### 浮点类型

| Data Type    | Comments                                | Size 1           | Size 2                    | Remark |
| :----------- | :-------------------------------------: | :--------------- | :------------------------ | :----- |
| float        | single precision float                  |          4 Bytes |                           | 用于近似激素       |
| double       | double precision float                  |          8 Bytes |                           | 用于近似计算       |
| decimal(m,d) | Fixed  precision float                  | max(m,d)+2 Bytes |                           | 最多65个数字；用于精确计算 |

m, 表示总位数
d, 表示小数位数

decimal 总共65位

### 日期和时间类型

+ 表格
  + [table]

    | Data Type    | Format                | Size 1   | Size 2                                            |
    | :----------- | :-------------------- | :------- | :-----------------------------------------------: | 
    | year         | YYYYY                 | 1 Byte   |                    1901 ~ 2155                    |
    | time         | HH:MM:SS              | 3 Bytes  |              -838:59:59 ~ 838:59:59               |
    | date         | YYYY-MM-DD            | 3 Bytes  |              1000-01-01 ~ 9999-12-31              |
    | datetime     | YYYY-MM-DD HH:MM:SS   | 8 Bytes  |     1000-01-01 00:00:00 ~ 9999-12-31 23:59:59     |
    | timestamp    | YYYY-MM-DD HH:MM:SS   | 4 Bytes  | 1980-01-01 00:00:00 UTC ~ 2038-01-19 03:14:07 UTC |

+ datetime vs timestamp

  + 表格
    + [table]

      |          |  datatime | timestamp |
      | :------- | :-------- | :-------- |
      | 时间长度   | 1000-01-01 00:00:00 ~ 9999-12-31 23:59:59 | 1980-01-01 00:00:00 UTC ~ 2038-01-19 03:14:07 UTC |
      | 存储空间   | 8 Bytes   | 4 Bytes |
      | 时间内容   | 不做时区转换 | 写，有时会从当前时区转为UTC；读，从UTC转换为当前时区 |  
      | 高并发问题 |            | 默认操作系统时间，每次读写要调用tz_convert，须加锁。高并发，性能抖动  |

  

### 字符串类型

+ 表格

  + [table]

    | Data Type    | comments              | Size 1   | Size 2                                            |
    | :----------- | :-------------------- | :------- | :-----------------------------------------------: | 
    | char(m)      | 定长，补空格            |          | 0 ~        255                                    |
    | varchar(m)   | 不定长                 |          | 0 ~      65535                                    |
    | tinyblob     |                       |          | 0 ~        255                                    |
    | tinytext     |                       |          | 0 ~        255                                    |
    | blob         |                       |          | 0 ~      65535                                    |
    | text         |                       |          | 0 ~      65535                                    |
    | mediumblob   |                       |          | 0 ~   16777215                                    |
    | mediumtext   |                       |          | 0 ~   16777215                                    |
    | longblob     |                       |          | 0 ~ 4294967295                                    |
    | longtext     |                       |          | 0 ~ 4294967295                                    |


+ 示例

  + [table] 

    | Value | CHAR(4) | size  | VARCHAR(4) | size  |
    | :---- | :------ | :---- | :--------- | :---- |
    | `''`    | `'    '`  | 4 B   | `''`        | 1 B   |
    | `'ab'`  | `'ab  '`  | 4 B   | `'ab'`       | 3 B   |
    | `'abcd'` | `'abcd'` | 4 B   | `'abcd'`    | 5 B   |
    | `'abcdefg'` | `'abcd'` | 4 B | `'abcd'`    | 5 B   |

  + VARCHAR需要1B存储长度

### 枚举 & 集合

#### ENUM

#### SET

### 空间数据

用于存储空间数据(地理信息、几何图形)，如: GEOMETRY, POINT, LINESTRING, POLYGON, MULTIPOINT, MULTILINESTRING, MULTIPOLYGON, GEOMETRYCOLLECTION
