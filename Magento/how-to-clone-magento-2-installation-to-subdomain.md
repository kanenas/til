# How to clone a Magento v.2.3.x installation to subdomain

- Create folder _clone
- Create subdomain clone.example.com
- Apply php v.7.2.x
- Create DB ( name: example_clonedb, user: example_cloneusr, pass: xxxxxx )
- Copy example_livedb > example_clonedb
- Change web/unsecure/base_url & web/secure/base_url in TABLE core_config_data
- Copy files from /home/example/public_html/ > /home/example/_clone/
- Edit /home/example/_clone/app/etc/env.php, /home/example/_clone/.htaccess
- Clear ALL caches, pub/static included and the Magento cache and compiled files in var/
- Re-deploy static files
- Reindex
- Change admin URL from https://clone.example.com/admin_12345/ > https://clone.watobject.com/clone_admin_12345/

CLI  
`cd /home/example/public_html/`  
`sudo -u example /usr/local/bin/php -c /home/example/public_html/_clone/php.ini bin/magento cache:clean`  
`sudo -u example /usr/local/bin/php -c /home/example/public_html/_clone/php.ini bin/magento indexer:reindex`  
`sudo -u example /usr/local/bin/php -c /home/example/public_html/_clone/php.ini bin/magento indexer:reset`  
`sudo -u example /usr/local/bin/php -c /home/example/public_html/_clone/php.ini bin/magento indexer:reindex`  
`sudo -u example /usr/local/bin/php -c /home/example/public_html/_clone/php.ini bin/magento setup:static-content:deploy en_US el_GR`  
