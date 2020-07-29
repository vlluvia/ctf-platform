

# mysql
* 【原理】
> Mysql数据恢复

* 【目的】
> 了解MySQL数据恢复的工具

* 【环境】
> windows

* 【工具】
> Undrop for InnoDB

* 【步骤】
1. 使用Undrop for InnoDB(https://github.com/chhabhaiya/undrop-for-innodb)工具。

2. clone下来之后make安装。根据题目给出的文件，我们可以知道应该满足Recover after DROP TABLE, innodb_file_per_table is OFF(https://twindb.com/recover-after-drop-table- innodb_file_per_table-is-off/)这种恢复方式。

3. 按照教程操作。首先使用stream_parser

4. 在FIL_PAGE_INDEX目录下找到数据库页。

5. 首先探索一下SYS_TABLES这张表，这张表里记录有表的信息。搜索关于ctf的表

6. 所以我们知道了table_id是13。由13再去查找关于INDEX的信息。

7. 得到index_id是15。因此，应当到第15页查找，传入结构定义的SQL文件。

8. 得到了flag为71e55075163d5c6410c0d9eae499c977。
