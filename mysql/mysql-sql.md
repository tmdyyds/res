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

- 重建索引

>alter table test ENGINE=INNODB

#### select

- 强制使用索引

> https://dev.mysql.com/doc/refman/8.0/en/index-hints.html
>
> select * from test **FORCE INDEX(col1)/USE INDEX (col1, col2)/IGNORE INDEX (col1)** where id = 1