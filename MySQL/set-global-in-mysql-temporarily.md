# How to SET GLOBAL in MySQL temporarily

Connect with terminal to MySQL `>mysql -uroot`.  

`SHOW VARIABLES LIKE 'sql_mode';`  

`SET GLOBAL sql_mode = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION';`  

`SET SESSION sql_mode = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION';`  

**Note**: https://dev.mysql.com/doc/refman/5.7/en/server-options.html#option_mysqld_sql-mode  
