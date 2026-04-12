---
title: MySQL学习
markmap:
  colorFreezeLevel: 24
---

# Overview

+ 应用
  + 联机事务处理 online transaction processing
  + 数据分析 data analytics

+ 目的

  + 非数据库系统的问题

    + 数据冗余和不一致性 -- data redundancy and inconsistency
    + 数据访问困难 -- difficulty in accessing data
    + 数据孤立 -- data isolation
    + 完整性 和 一致性 -- integrity & consistency constraint
    + 原子性 -- atomicity
    + 并发访问异常 -- concurrent-access anomaly
    + 安全性 -- security 

+ 数据视图

  + 数据模型 -- data model
    + 关系模型 -- relational model
    + 实体-联系模型 -- entity-relationship model, ER
    + 半结构化数据模型 -- semi-structured data model
    + 基于对象数据模型 -- object-based data model
  + 关系数据模型
  + 数据抽象 -- data abstraction
    + 物理层 -- physical level
      数据是怎样存储的，详细描述复杂的底层数据结构。
    + 逻辑层 -- logical level
      描述存储了什么样的数据，以及这些数据的关系。  
      具有物理独立性。  
    + 视图层 -- view level
      描述数据库的某个部分。  

+ 实例(database instance) 和 模式(database schema)
  + 数据库模式， 数据库的逻辑设计

    + 模式图 schema diagram

  + 数据库实例， 给定时刻数据库中数据的一个快照

+ 数据库语言

  + 数据库定义语言 -- data-definition language, DDL
    + 数据存储和定义 -- data storage and definition
      + 域约束 -- domain constratint, 如 字段数据类型 等
      + 引用完整性 -- referential integrity  
      + 授权 -- authorization
        + 读权限 -- read authorization
        + 插入权限 -- insert authorization
        + 更新权限 -- update authorization
        + 删除权限 -- delete authorization
        + 数据字段 和 元数据 -- data dictionary & metadata
  + 数据库操纵语言 -- data-manipulation language, DML

    + 过程化DML -- procedural DML
    + 声明式DML -- declarative DML

    + 关系查询语言 -- query language

      + 命令式查询语言 imperative query language
      + 函数式查询语言 functional query language
        + 关系代数 relational-algebra
          + 选择 select

            + 代数表示

              + [Diagram]
                ![algebra select](./images2/algebra-select-260412a.svg)

            + SQL
              + [code]

                ```sql
                select * 
                from instructor 
                where dept_name = 'Physics'
                  and salary > 9000;
                ```

          + 投影 project

            + 代数表示

              + [Diagram]
                ![algebra project](./images2/algebra-project-260412a.svg)

            + SQL
              + [code]

                ```sql
                select ID, name, salary
                from instructor 
                where dept_name = 'Physics'
                  and salary > 9000;
                ```

          + 笛卡尔积 Cartesian-product

            + 代数表示
              + [Diagram]
                ![algebra Cartesian-product](./images2/algebra-CartesianProduct-260412a.svg)

            + SQL
              + [code]

                ```sql
                select *
                from instructor, teaches
                where instructor.ID = teaches.ID;
                ```


          + 连接 Join

            + 代数表示
              + [Diagram]
                ![]()

            + SQL
              + [code]

          + 集合

            + 合

            + 交

            + 差

          + 赋值

          + 更名

          + 聚集

          + 等价查询


      + 声明式查询语言 declarative query language

+ 数据库引擎

  + 存储管理器 -- storage manager

    + 组成
      + 权限即完整性管理器 -- authorization and integrity manager
      + 事务管理器 -- transaction manager
      + 文件管理器 -- file manager
      + 缓冲区管理器 -- buffer manager

    + 数据结构
      + 数据文件 -- data file
      + 数据字典 -- data dictionary
        存储数据结构的元数据，尤其是数据库模式
      + 索引 -- index
  
  + 查询处理器 -- query processor

    + DDL解释器 -- DDL interpreter
    + DML编译器 -- DML compiler
      + 查询优化 -- query optimization
    + 查询执行引擎 -- query evaluation engine

  + 事务管理
    + 事务，原子性和一致性的单元，即一组操作要么全部执行，要么全部不执行
    + 恢复管理器
    + 并发控制器

# 数据库概念

+ 概念

  + 关系数据库
    + 产品
      MySQL, Oracle, DB2, MS SQLServer, SyBase, etc.

    + 数据表/关系

    + 行/元组

    + 列/属性

  + 非关系型数据库， NoSql(Not Only SQL)

    + 产品
      Redis, MongoDB, Memcached, HBase, etc.

+ 关系数据库 Database -- 关联表(database tables)的集合
  
  + 简单概念
    + Data, 对客观事物进行描述并可以鉴别的符号(抽象)。
    + Database
    + RDBMS (Relational Database Management System), 关系数据库管理系统
    + DBAS (Database Application System) 数据库应用程序/系统
    + DBA (Database Administrator) 数据库管理员
      + 职责
        + 模式定义 -- schema definition
        + 存储结构和存取方法定义 -- storage structure and access-method definition
        + 模式及物理组织修改 -- schema and physical-organization modification
        + 数据访问授权 -- granting of authorization for data access
        + 日常维护 -- routine maintenance

  + 数据表, Database Table, 数据的矩阵

    + 列, column, 包含相同类型的数据
    + 行 / 元组 / 记录, row, 一组相关的数据
      + 表头, header, 列的名称
    + 主键, PK (Primary Key)

      + Problems / Questions

        + 自增主键问题

          + 描述: 为什么**不**推荐使用数据库自增主键，也不推荐UUID，雪花算法简论

          + 解释/解决
            + 自增主键问题
              + 在分库分表时会有问题
                + 单表时，可以有独立(唯一)ID
                + 横向分表时，每个逻辑子表都有一个自增主键，不能保证唯一
                  + 使用步长增加ID，在扩容时会有问题
                    ==> UUID
            + UUID
              + InnoDB的索引结构
                + B+-Tree 索引即数据，数据即索引。主键索引树的叶子节点，会保存完整的行数据
                  + UUID负面影响
                    + UUID较长，占用空间更大大，Page(内存磁盘交换使用，空间固定)占用更多，索引    树高度高，遍历次数越多，遍历Page更多，IO更多，影响IO性能
                    + UUID是无序的，非趋势递增；但主键是有序的，需要排序。插入数据时，需要树的分    裂与合并。
                      ==> 雪花算法
            + 雪花算法
              + 组成 (64位二进制 转化为 十进制ID)
                + 1 bit Sign
                + 41 bit timestamp
                + 10 bit MachineID
                + 12 bit SequenceID
              + Problems
                + 时间回拨问题
                  + 问题
                    + 不再趋势递增
                    + 时间戳重复
                  + 解决
                    + 抛出异常，牺牲可用性
                    + 等待时间恢复，(回拨时间跨度大?须:需) 设置等待时间
                    + 备用方式生成

                + 机器码问题
                  + 原因: 机器集群
                  + 解决
                    + 配置文件管理
                    + 服务注册组件，使用服务ID
                + 序列号一直为0的问题
                  + 原因: 同一机器同一时间并发，序列号才递增。大部分场景，不会触发这一机制。
                  + 问题: 分库分表时，因取模，导致数据偏移(末尾为0，取模后为偶数，导致奇数表中    无数据)，数据不均匀/数据倾斜
                  + 解决：
                    + 当序列号为0时，使用时间戳的最后一位

    + 外键, FK (Foreign Key),  
    + 复合建, ,
    + 索引, Index,  
      + 


  + 冗余, , 存储多倍数据， 冗余降低了_性能_，但提高了_安全性_

  + Normal form - 范式
    + 示意图
      + [Diagram]
        ![DBNF](./images2/DBNormalForm.webp)

    + 码，足以区分实体(记录)的属性或属性集/组。
      一个元组(行)的所有属性必须能唯一标识元组。即，不能出现两个元组的属性完全相同。

      + 超码 superkey
        一个或多个属性，将这些属性组合在一起可以在一个关系(表)中唯一标识一个元组(行)。
      + 候选码 candidate key
        最小的超码  
      + 主码 primary key / 主码约束 primary key constraint
        数据库设计者选出的候选码  
      + 外码 foreign key / 外码约束 foreign key constraint / 被引用关系 referenced relation
        + 引用完整性 referential integrity constraint

    + 1NF - 第一范式
      + 定义: 所有域都是原子性的，即数据库表的每一列都是不可分割的原子数据项
      + 示例
        + 错误

          + [Table]

            | reader_id | name | Dept_id | Book | Borrowing_Date | Return_date |
            | :-------- | :---- | :---- | :---- | :------------: | :---------: |
            | 001       | Bob   | 100   | 101 DB Conceptions | 2021/08/20 |  |
            | 002       | Auth  | 200   | 102 C++ Programing | 2021/08/21 |  |

          + 说明
            Book字段可以拆分为 Book_ID 和 Book_Name

        + 纠正

          + [Table]

            | reader_id | name | Dept_id | Book_ID | Book_Name | Borrowing_Date | Return_date |
            | :-------- | :---- | :---- | :---- | :---- | :------------: | :---------: |
            | 001       | Bob   | 100   | 101 | DB Conceptions | 2021/08/20 |  |
            | 002       | Auth  | 200   | 102 | C++ Programing | 2021/08/21 |  |



    + 2NF - 第二范式
      + 定义: 在1NF的基础上，非码属性必须完全依赖于候选码（在1NF基础上消除非主属性对主码的部分函数依赖）
      + 要求: 数据库表中的每个实例或记录必须可以被唯一地区分。选取一个能区分每个实体的**属性**或**属性组**，作为实体的唯一标识。
      + 示例
        + 错误
        + 纠正

      + Problems

        + 数据冗余
        + 操作(更新、插入、删除)异常


    + 3NF - 第三范式
      + 定义: 在2NF基础上，任何非主属性不依赖于其它非主属性（在2NF基础上消除传递依赖）
      + 要求: 一个关系中不包含已在其它关系已包含的非主关键字信息。
      + 示例
        + 错误
        + 纠正


    + BCNF(Boyce-Codd Normal Form) - 巴斯-科德范式 / 修正第三方式
      + 定义: 在3NF基础上，任何主属性不能对主键子集依赖（在3NF基础上消除主属性对主码子集的依赖）
      + 说明: 任何决定因素都是超键
      + 示例
        + 错误
        + 纠正


    + 4NF - 第四范式
      + 定义
      + 示例
        + 错误
        + 纠正


    + 5NF - 第五范式
      + 定义
      + 示例
        + 错误
        + 纠正

+ 数据库操作
  + 数据库结构 / 数据表结构
  + Select -- Query 查询
  + Update -- 更新
  + Insert -- 插入
  + Delete -- 删除
  + Truncate -- 截断/删节
  + Drop -- 抛弃

+ Trouble Shoot
