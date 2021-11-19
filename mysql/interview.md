## 问题

#### 如何避免长事务对业务的影响？

- 首先去掉事务中不必要的select

- 通过 SET MAX_EXECUTION_TIME 命令，来控制每个语句执行的最长时间

- 监控 information_schema.Innodb_trx 表，设置长事务阈值，超过就报警 / 或者 kill

- 其他 https://time.geekbang.org/column/article/69236

#### 优化sql中，出现 explain 的结果预估的 rows 值跟实际情况差距比较大，如何处理？

- analyze table t (线上低谷时期使用)

#### mysql选错索引如何处理？

- force index(A)

- 分解sql语句，拆分或子查询优化

- 新建合适索引或删除索引

#### 优化慢sql时候，注意优化器选择索引问题？

- 影响优化器选择索引三要素：扫描行数、是否使用临时表、是否排序

