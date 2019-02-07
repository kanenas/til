# Search information_schema.columns and create queries to alter columns in tables

`SELECT CONCAT('ALTER TABLE ', TABLE_SCHEMA, '.', TABLE_NAME, ' CHANGE ', COLUMN_NAME, ' ', COLUMN_NAME, ' DATE NULL DEFAULT NULL;') AS EXEC_QUERY FROM information_schema.columns WHERE column_default = '0000-00-00';`  

**Notice**:  
- If you use **phpMyAdmin** you will have to select **Full texts** from *+ Options*
- Maybe you will have to add `LIMIT 100` at the end of the query, especially if you use **phpMyAdmin**.
