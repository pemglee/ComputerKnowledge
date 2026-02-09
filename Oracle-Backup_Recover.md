# Oracle Database的备份和恢复

## Overview

## 热备

## 冷备

### imp & exp

#### 全库备份和恢复

#### 部分数据表备份和恢复

##### 操作实例 - NJCB Summit

1. 备份/导出

   ```sh
   exp userid=${SUMMITDBNAME}/${SUMMITDBNAME}@${ORACLE_SID} file=/home/summit/temp/lipeng/DBData/dmBook_AppServ49.75_Dt260121.dmp tables=dmBook
   ```

2. 恢复

   1. 前处理

      ```sh
      sqlplus ${SUMMITDBNAME}/${SUMMITDBNAME}@${ORACLE_SID}
      ```

      ```sql
      drop index BOOK_IDX_1;
      drop index BOOK_IDX_2;
      drop table dmBook;
      ```

   2. 导入

      ```sh
      imp userid=${SUMMITDBNAME}/${SUMMITDBNAME}@${ORACLE_SID} file=/home/summit/temp/lipeng/DBData/dmBook_AppServ49.75_Dt260121.dmp tables=dmbook
      ```

### impdp & expdp

## Archive
