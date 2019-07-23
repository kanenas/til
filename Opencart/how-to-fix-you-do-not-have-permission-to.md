Edit the file `/system/library/user.php` and add after `public function hasPermission($key, $value) {` the line `return true;`  
SAVE

Go to  
`Opencart > System > Users > User Group > Administrator > Select All (Access Permission & Modify Permission) > SAVE`

Then edit again the file `/system/library/user.php` and remove the line `return true;`  
SAVE
