# Find all tables with a specific column name

`SELECT DISTINCT TABLE_NAME FROM INFORMATION_SCHEMA.COLUMNS WHERE COLUMN_NAME IN ('column-to-find') AND TABLE_SCHEMA='database-name' LIMIT 100;`
