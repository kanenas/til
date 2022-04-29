# Export database from one server & import to another
Export the database `example_livedb` and use gzip to compress it bacause it is too large  
`mysqldump -h localhost -u root --port 3306 -p example_livedb | gzip > /home/example/db-backup/2022-04-29_00_example_livedb.sql.gz`  

Import structure & data -as they are- from `example_livedb` to `another_example_livedb` using the user `another_example_liveusr` and the extracted `2022-04-29_00_example_livedb.sql` from `2022-04-29_00_example_livedb.sql.gz`  
`mysql -u another_example_liveusr -p another_example_livedb < /home/another-example/db-backup/2022-04-29_00_example_livedb.sql`

For security reasons I used the following rules in the `.htaccess` file in `/home/example/db-backup/` and `/home/another-example/db-backup/` folders.
```
order deny,allow
Deny from all 
# whitelist custom IP address
allow from 111.112.113.114 #my.custom.IP.address
```
