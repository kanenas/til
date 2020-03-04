# How to extract a table from a MySQL dump

Determine the table structure from the decompressed MySQL database dump:  
`grep -n "Table structure" [MySQL_dump_filename].sql`

The next step is to extract the table from the MySQL database dump file:  
`sed -n '[starting_line_number],[ending_line_number] p' [MySQL_dump_filename].sql > [table_output_filename].sql`
