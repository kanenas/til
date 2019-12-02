# How to SET GLOBAL in MySQL temporarily

Connect with terminal to MySQL `>mysql -uroot`.  

`SHOW VARIABLES LIKE 'sql_mode';`  

`SET GLOBAL sql_mode = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION';`  

`SET SESSION sql_mode = 'ONLY_FULL_GROUP_BY,STRICT_TRANS_TABLES,ERROR_FOR_DIVISION_BY_ZERO,NO_AUTO_CREATE_USER,NO_ENGINE_SUBSTITUTION';`  

**Note**: https://dev.mysql.com/doc/refman/5.7/en/server-options.html#option_mysqld_sql-mode  


`SET GLOBAL innodb_buffer_pool_size = 10737418240;`  
`SET GLOBAL innodb_buffer_pool_instances = 10;`  
`-- SET GLOBAL innodb_log_file_size = 536870912;` << **CAUTION**  


Read more:  
- https://www.percona.com/blog/2014/01/28/10-mysql-performance-tuning-settings-after-installation/
- https://www.percona.com/blog/2016/10/12/mysql-5-7-performance-tuning-immediately-after-installation/
- https://dev.mysql.com/doc/refman/5.7/en/innodb-parameters.html#sysvar_innodb_buffer_pool_instances
- https://dev.mysql.com/doc/refman/5.7/en/innodb-buffer-pool-resize.html
- https://www.percona.com/blog/2016/05/03/best-practices-for-configuring-optimal-mysql-memory-usage/
