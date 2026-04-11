---
title: Java操作数据库
markmap:
  colorFreezeLevel: 24
---

+ 数据库操作

+ REDIS

+ NoSql

+ TIPs

  + 主键

    + 自增主键问题

      + [描述] 为什么**不**推荐使用数据库自增主键，也不推荐UUID，雪花算法简论

      + [解释/解决]
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
                + UUID较长，占用空间更大大，Page(内存磁盘交换使用，空间固定)占用更多，索引树高度高，遍历次数越多，遍历Page更多，IO更多，影响IO性能
                + UUID是无序的，非趋势递增；但主键是有序的，需要排序。插入数据时，需要树的分裂与合并。
                  ==> 雪花算法
        + 雪花算法
          + 组成 (64位二进制 转化为 十进制ID)
            + 1 bit Sign
            + 41 bit timestamp
            + 10 bit MachineID
            + 12 bit SequenceID
          + [Problems]
            + 时间回拨问题
              + [问题]
                + 不再趋势递增
                + 时间戳重复
              + [解决]
                + 抛出异常，牺牲可用性
                + 等待时间恢复，(回拨时间跨度大?须:需) 设置等待时间
                + 备用方式生成

            + 机器码问题
              + [原因]机器集群
              + [解决]
                + 配置文件管理
                + 服务注册组件，使用服务ID
            + 序列号一直为0的问题
              + [原因] 同一机器同一时间并发，序列号才递增。大部分场景，不会触发这一机制。
              + [问题] 分库分表时，因取模，导致数据偏移(末尾为0，取模后为偶数，导致奇数表中无数据)，数据不均匀/数据倾斜
              + [解决]
                + 当序列号为0时，使用时间戳的最后一位
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


