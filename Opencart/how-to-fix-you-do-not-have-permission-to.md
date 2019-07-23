- Edit the file `/system/library/user.php`, add after `public function hasPermission($key, $value) {` the line `return true;` and save it.

- Go to  
`Opencart > System > Users > User Group > Administrator > Select All (Access Permission & Modify Permission) > SAVE`

- Then edit the file `/system/library/user.php` again and remove the line `return true;`. Save it and you are done.
