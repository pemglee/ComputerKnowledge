# Oracle Database的备份和恢复

## Overview

## 热备

## 冷备

### imp & exp

#### 全库备份和恢复

#### 部分数据表备份和恢复

##### 操作实例 - NJCB Summit IMA

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

#### 全库备份和恢复

##### 操作实例 - NJCB Summit IMA

1. 备份/导出

2. 恢复

   1. Session检查

      `sqlplus / as sysdba`

      ```sql
      select SID, SERIAL#
        from V$SESSION
       where lower(USERNAME) = 'bonjimaprod';
      ```

   2. (optional) 强迫关闭

      `sqlplus / as sysdba`

      ```sql
      select 'alter system kill session '''||SID\\ ',' ||SERIAL#||''' immediate' from V$SESSION where username = '&username';
      ```

   3. 前处理 1, drop用户

      `sqlplus / as sysdba`

      ```sql
      drop user bonjimaprod cascade;
      drop role bonjimaprodrole;
      ```

   4. 前处理 2，创建用户

      `sqlplus / as sysdba` 或 `sqlplus system/O_racle_1234_@osumima`

      ```sql
      create user bonjimaprod
      identified by bonjimaprod
      default tablespace SUMMIT
      temporary tablespace TEMP
      quota unlimited on SUMMIT;
      ```

      ```sql
      grant connect, resource, alter tablespace to bonjimaprod;

      alter user bonjimaprod quota unlimited on SUMMIT_IX;

      create role bonjimaprodrole;
      ```

   5. 导入

      ```sh
      nohup impdp system/O_racle_1234_@OSUMIMA remap_schema=bonjimaprod:bonjimaprod dumpfile=ima20251231_%u.dmp logfile=ima_expdp_20251231.log directory=EXPDP parallel=8 table_exists_action=replace job_name=imp_ima &
      ```

## Archive
