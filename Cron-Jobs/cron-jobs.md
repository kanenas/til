# Delete cached image files and Opencart Journal's (v3.x) theme cached files 
`5	2	*	*	* rm -rf /home/USERNAME/public_html/image/cache/* ; touch /home/USERNAME/public_html/image/cache/index.html`    
`7	2	*	*	* rm -rf /home/USERNAME/public_html/system/storage/cache/* ; touch /home/USERNAME/public_html/system/storage/cache/index.html`  

This cron job runs **every Monday** at **05:00 am**.  
`0   5   *   *   1   find /path-to-image-folder/image/cache/ -type f -not -name 'index.html' -delete >/dev/null 2>&1`
