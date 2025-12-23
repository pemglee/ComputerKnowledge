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
| numeric(p,s)     | number(p,s)   |           |        |                       |          |
| real             | binary_float  |           |        |                       |          |
| double precision | binary_double |           |        |                       |          |
| float(n)         | float         |           |        |                       |          | 


p -- precision
s -- scale

## Data Type in MySQL

### 数值类型

#### 整数类型

| Data Type | Range                                      | Size 1   | Size 2                   | 
| :-------- | :----------------------------------------: | :------- | -----------------------: | 
| tinyint   |                 -128 ~ 127                 | 1 Byte   | 0 ~                  255 | 
| smallint  |               -32768 ~ 32767               | 2 Bytes  | 0 ~                65535 | 
| mediumint |             -8388608 ~ 8388607             | 3 Bytes  | 0 ~             16777215 |
| int       |          -2147483648 ~ 2147483647          | 4 Bytes  | 0 ~           4294967295 |
| bigint    | -9223372036854775808 ~ 9223372036854775807 | 8 Bytes  | 0 ~ 18446744073709551615 |

#### 浮点类型

| Data Type    | Comments                                | Size 1           | Size 2                    | 
| :----------- | :-------------------------------------: | :--------------- | :------------------------ | 
| float        | single precision float                  |          4 Bytes |                           |
| double       | double precision float                  |          8 Bytes |                           |
| decimal(m,d) | Fixed  precision float                  | max(m,d)+2 Bytes |                           |

### 日期和时间类型

| Data Type    | Format                | Size 1   | Size 2                                            |
| :----------- | :-------------------- | :------- | :-----------------------------------------------: | 
| year         | YYYYY                 | 1 Byte   |                    1901 ~ 2155                    |
| time         | HH:MM:SS              | 3 Bytes  |              -838:59:59 ~ 838:59:59               |
| date         | YYYY-MM-DD            | 3 Bytes  |              1000-01-01 ~ 9999-12-31              |
| datetime     | YYYY-MM-DD HH:MM:SS   | 8 Bytes  |     1000-01-01 00:00:00 ~ 9999-12-31 23:59:59     |
| timestamp    | YYYY-MM-DD HH:MM:SS   | 4 Bytes  | 1980-01-01 00:00:00 UTC ~ 2040-01-19 03:14:07 UTC |

### 字符串类型

| Data Type    | comments              | Size 1   | Size 2                                            |
| :----------- | :-------------------- | :------- | ------------------------------------------------: | 
| char(m)      |                       |          | 0 ~        255                                    |
| varchar(m)   |                       |          | 0 ~      65535                                    |
| tinyblob     |                       |          | 0 ~        255                                    |
| tinytext     |                       |          | 0 ~        255                                    |
| blob         |                       |          | 0 ~      65535                                    |
| text         |                       |          | 0 ~      65535                                    |
| mediumblob   |                       |          | 0 ~   16777215                                    |
| mediumtext   |                       |          | 0 ~   16777215                                    |
| longblob     |                       |          | 0 ~ 4294967295                                    |
| longtext     |                       |          | 0 ~ 4294967295                                    |

### 枚举 & 集合

#### ENUM

#### SET

### 空间数据

用于存储空间数据(地理信息、几何图形)，如: GEOMETRY, POINT, LINESTRING, POLYGON, MULTIPOINT, MULTILINESTRING, MULTIPOLYGON, GEOMETRYCOLLECTION
