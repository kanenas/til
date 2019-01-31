# Alter two columns of a TABLE with one query

### Columns:  
- `date_start`  
- `date_end`

**Query**: `ALTER TABLE prefix_NameOfTheTable CHANGE date_start date_start DATE NULL DEFAULT NULL, CHANGE date_end date_end DATE NULL DEFAULT NULL;`

