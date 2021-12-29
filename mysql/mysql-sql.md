#### alter table

- https://dev.mysql.com/doc/refman/5.6/en/alter-table.html 官网地址

- 加/删索引

> 普通索引
>
> alter table test ADD INDEX idx_index  (column, column)
>
> 主键索引
>
> alter table test ADD PRIMARY KEY  (column)
>
> 唯一索引
>
> alter table test ADD UNIQUE idx_unique  (column)
>
> 删索引
>
> alter table test DROP INDEX idx_index
>
> //重建非主键索引
> alter table T drop index k;
> alter table T add index(k);
>
> //重建主键索引
> //重建主键索引会影响非主键索引(其他索引叶子节点存储为主键索引ID)，在操作时候要在业务低估时
> //alter table T drop primary key;
> //alter table T add primary key(id);
> alter table T engine=InnoDB
>
> //重新统计索引信息
> analyze table t

- 重建索引

>alter table test ENGINE=INNODB

#### select

- 强制使用索引

> https://dev.mysql.com/doc/refman/8.0/en/index-hints.html
>
> select * from test **FORCE INDEX(col1)/USE INDEX (col1, col2)/IGNORE INDEX (col1)** where id = 1

- 查询缓存

> query_cache_type 设置成 DEMAND，默认的sql语句不适用查询缓存，如下显示使用
>
> select SQL_CACHE * from T where ID=10；//mysql8.0禁用查询缓存

#### delete

> delete from  test
>
> truncate test 清空所有数据时，性能优于delete

## 维护DB

- mysql

```
命令连接mysql
mysql -h$ip -P$port -u$user -p
```

- analyze

```
重新生成索引统计信息
analyze table test 会加读锁
```

- optimize

```
碎片处理
optimize table test
```

- show index

```
返回表索引信息
show index from test

查看表有哪些索引
show index from test(表)
```

- show full

```
查询连接状态
show full processlist
```

- show variables

```
查看隔离级别
show variables like 'transaction_isolation'
```

