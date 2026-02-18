# Oracle数据库通识

## 数据库连接

### 直接连接

实例 1： `sqlplus cgb632/cgb632@192.168.3.36:1521/osum1`

### 利用客户端配置连接

实例 1： `sqlplus $SUMMITDBNAME/$SUMMITDBPASSWD@${ORACLE_SID}`

配置信息：[NJCB] 


## 一些配置

### 密码复杂度

## 字符/字符串 处理

### 常用函数

#### 

### 转义问题

一般特殊字符可使用前加'\'来进行转义

几种特殊情况

+ '&'
  
  ex.

  ```sql
  update dmBook 
  set cdmProdType2='即期（CFETS'||chr(38)||'金交所）', 
      dmUserID2='徐毓', 
      cdmTrdPolicy='自营、平盘交易。', 
      cdmMngRegmnt='该业务纳入交易账户进行管理',
      cdmBelL1Dept='资金运营中心',
      cdmInUsing='',
      cdmAcctType2='交易类',
      cdmBusMode2='交易账户'
  where book = 'PMPT_SPTT02';
  ```

  也可使用 `'即期（CFETS'||'&'||'金交所）'`替代。
  注意前后字串需要用**`**引住，即，不要写成'即期（CFETS||chr(38)||金交所）'
  
### BLOB, CLOB, etc

+ CLOB（Character Large Object）：

  + 存储大量的字符数据，可以存储多达4 GB的文本。
  + 适用于需要存储大段文本信息的场景，如文档、日志记录等。

+ BLOB（Binary Large Object）：  

  + 存储大量的二进制数据，可以存储多达4 GB的二进制信息。
  + 常用于存储图片、音频、视频等媒体文件。

+ NCLOB（National Character Large Object）：

  + 类似于CLOB，但用于存储多字节字符集（如Unicode字符集）的数据。
  + 适用于需要存储多国语言文本的应用。

+ BFILE（Binary File）：

  + 存储外部文件的引用，而不是将文件内容直接存储在数据库中。
  + BFILE可以存储在数据库外部文件系统中，数据库只存储其路径和文件名。
