### Magento MySQL Database Optimization with Log Cleaning
- https://www.mconnectmedia.com/blog/magento-mysql-database-optimization-with-log-cleaning/
- https://www.fastcomet.com/tutorials/magento/optimize-database
  - Create a php file called [`mg-cleanup.php`](https://github.com/kanenas/til/blob/master/Magento/mg-cleanup.php) in your Magento home.
  - When you have the file placed in your Magento folder you can access the php script via: 
    - http://www.domain.com/mg-cleanup.php?clean=log  --clean log tables
    - http://www.domain.com/mg-cleanup.php?clean=var  --clean cache files  
  - **OR** set a cron job:
    - `curl -s -o /dev/null http://www.domain.com/cleanup.php?clean=log`
    - `curl -s -o /dev/null http://www.domain.com/cleanup.php?clean=var`
