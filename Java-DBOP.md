---
title: Java操作数据库
markmap:
  colorFreezeLevel: 24
---

+ 数据库操作

+ REDIS

+ NoSql

+ TIPs


  + 查询去重
    + `distinct`
    + `group by`

  + count

    + count(*) vs count(1)/count(0)

      + [功能]
      + [性能]
        + [MySql] 
          + 无区别
          + 从查询计划来看，`count(*)`略胜，因为MySql会在在底层做优化

    + count(field_name)
      + 会排除值为NULL的记录

  + 循环查询
    + 为什么**不**能循环查库

      + [描述]
      + [故障]
        1+N查询/级联查询(分库分表) 引发雪崩，会抽干连接池，导致网络I/O阻塞和接口大范围超时


  + 多表查询

    + 为什么**不**能多表join
      负载大
      后期维护难度大，涉及分库分表

  + SQL优化

    + **不**使用 `select *`

      + [原因]

        + 增加查询解析器的成本，
        + 走的是全表扫描，没有用到任何索引，或者不走覆盖索引，会产生大量的回表查询，效率低。
        + 无用的字段增加资源占用
        + 无用字段增加网络消耗，尤其说text类型字段
        + 删减字段易与resultMap配置不一致

    + 应小表驱动大表
      用数据量较小、索引较完备的表，然后使用其索引和条件对大表进行数据筛选，从而减少数据计算量，提高效率。

      + [原因]
        连接缓冲区的工作机理(Block nested-loop join)
      + [示例]
        student表中有30条数据，scores表中有10w条数据，则应

        ```sql
        select * from student
        left join scores 
        on student.student_id = scores.student_id;
        ```

    + 应使用连接查询代替子查询

    + 为'group by'字段设置索引

    + 使用批量插入替代循环插入

    + 使用'limit'

      + [示例]
        比如大查询结果集翻页，查找10000条之后的10条

        ```sql
        select * from table_name where id in
        ( select id from table_name where (条件) order by ... limit 10000 );
        ```

        或

        ```sql
        select * from table_name where id 
        inner join 
        ( select id from table_name where (条件) order by ... limit 10000 )；
        ```

    + 尽量使用 'union all'，而非 'union'(不执行去重)

  + Redis
    + [Question] Redis为什么快
      + [Answer] 
        + 纯内存访问
        + 单线程避免上下文切换
        + 渐进式ReHash
          Redis采用全局hash表，使用key-value结构  
          ReHash采用两张表  

        + 缓存时间戳
          采用读时间方法会耗费资源，所以每毫秒更新时间戳供程序使用。

    + [Question] Redis如何实现IO多路复用


