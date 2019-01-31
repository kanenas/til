# Alter two columns of a table with one query

### Table:  
- `prefix_NameOfTheTable`  

### Columns:  
- `date_start`  
- `date_end`

**Query**: `ALTER TABLE prefix_NameOfTheTable CHANGE date_start date_start DATE NULL DEFAULT NULL, CHANGE date_end date_end DATE NULL DEFAULT NULL;`

