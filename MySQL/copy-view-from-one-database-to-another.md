# Copy view from one database to another

Use <a href="https://dev.mysql.com/doc/refman/8.0/en/views-table.html" target="_blank">INFORMATION_SCHEMA.VIEWS</a> to see the **VIEW** definition.  

1. Execute `SHOW CREATE VIEW VIEW-NAME` from **A** database to get the whole statement.  
2. Copy the whole statement for step **No1**.  
3. Execute the whole statement from step **No2** to database **B**.

**Error**: _#1227 - Access denied; you need (at least one of) the SUPER privilege(s) for this operation_  
**Solution**: Remove `DEFINER=databse-user@localhost SQL SECURITY DEFINER`
