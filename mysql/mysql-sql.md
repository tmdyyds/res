#### explain

- Extra

> Using union 索引合并(高性能mysql中第五章(194页))，需要优化，应该检查查询语句和表结构，也可以ignore index让优化器忽略某些索引
>
> Using index 覆盖索引

#### alter table 

- https://dev.mysql.com/doc/refman/5.6/en/alter-table.html 官网地址

- 加/删索引

> //普通索引
>
> alter table test ADD INDEX idx_index  (column, column)
>
> //主键索引
>
> alter table test ADD PRIMARY KEY  (column)
>
> //唯一索引
>
> alter table test ADD UNIQUE idx_unique  (column)
>
> //删索引
>
> alter table test DROP INDEX idx_index

