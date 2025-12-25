# Oracle数据库通识

## 字符/字符串 处理

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
  