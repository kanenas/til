# How to clean up Magento /var/session/ contents
First verify that it's really a problematic amount of session files.  

`ls -U1 | wc -l` **<<** *This is a fast command to give you the number of files in the current directory*

In your `var/session` folder  
`find . -mtime +30 -exec rm {} \;` **<<** *This will find all files older then 30 days and delete them*

Optionally you can run this as a **cronjob**, do remember to replace the dot with the full path to the session files `/path/to/magento/var/sessions/*`

`find /path/to/magento/var/sessions/* -mtime +30 -exec rm {} \;`

