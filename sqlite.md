### introduce

SQLite是一个C语言实现的，开源的，嵌入式的关系型数据库。

### Embedded

它对数据库的操作集成在操作数据库的程序之中，而不是有一个独立的数据库管理程序。所以你不用像操作MySQL一样一开始要配置服务器啊，管理帐号什么的东西。所有的操作都是通过调用SQLite的API实现

### install

### start

打开/新建数据库

	sqlite3 test.db

新建一张表，有两列，一列是叫id的，类型为integer的主键，一列是叫value的text类型的数据。

	sqlite> create table test (id integer primary key, value text);
	
插入一些数据

	sqlite> insert into test (id,value) values(1,'fda');
	sqlite> insert into test (id,value) values(2,'ffdda');
	sqlite> insert into test (value) values('ffdda');
	sqlite> insert into test (value) values('no');
	
看看表是怎么样的
	
	sqlite> .mode column　// 以列模式显示	sqlite> .headers on 	sqlite> select * from test;
	
可以用SQL函数列出最后一行的id

	select last_insert_rowid();
	
可以添加索引

	sqlite> create index test_idx on test (value);	sqlite> create view schema as select * from sqlite_master;	
	
可以列出索引
	sqlite> .indices test	
可以查看创建的模式
	sqlite> .schema test
sqlite_master　是数据库系统本身的信息
	sqlite> .mode column	sqlite> .headers on	sqlite> select type, name, tbl_name, sql from sqlite_master order by type;	type name tbl_name sql	---------- ---------- ---------- 	index test_idx test CREATE INDEX test_idx on test (value)	table test test CREATE TABLE test (id integer primary	view schema schema CREATE VIEW schema as select * from s
	
可以输出SQL
	
	sqlite> .dump
	
输出之前可以重定向

	sqlite> .output file.sql	sqlite> .dump	sqlite> .output stdout
可以查看当前命令行的设置
	.show
可以从SQL读入表格
	sqlite> drop table test;	sqlite> drop view schema;	sqlite> .read file.sql
	
如果想输出CSV文件，可以这样
	sqlite3> .output file.csv	sqlite3> .separator ,	sqlite3> select * from test;	sqlite3> .output stdout
	
也可以用内置的CSV模式
	sqlite3> .output file.csv	sqlite3> .mode csv	sqlite3> select * from test;	sqlite3> .output stdout
			
可以进行选择，只输出value为m开头的值

	sqlite> .output text.csv	sqlite> .separator ,	sqlite> select * from test where value like 'm%';	sqlite> .output stdout
	
可以将输出的数据导入另外一个表

	sqlite> create table test2(id integer primary key, value text);	sqlite> .import text.csv test2
	
可以通过系统命令导入或者导出
	sqlite3 test.db .dump		sqlite3 test.db .dump > test.sql		sqlite3 test.db "select * from test"		sqlite3 test2.db < test.sql		sqlite3 –init test.sql test3.db
	
备份之前可以先清空那些已经删除的元素的空间
	sqlite3 test.db vacuum	cp test.db test.backup	
可以分析数据库的情况
	sqlite3_analyzer test.db
	
SQL语句的语法是这样的
	select id from foods where name= JujyFruit ;
	分别对应verb subject predicate