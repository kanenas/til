
```
SET
  @DATABASE_NAME = 'write-the-correct-db_name-here';
SELECT
  CONCAT(
    'ALTER TABLE `',
    TABLE_NAME,
    '` ENGINE=InnoDB;'
  ) AS sql_statements
FROM
  information_schema.tables AS tb
WHERE
  table_schema = @DATABASE_NAME AND `ENGINE` = 'MyISAM' AND `TABLE_TYPE` = 'BASE TABLE'
ORDER BY TABLE_NAME
DESC;
```
