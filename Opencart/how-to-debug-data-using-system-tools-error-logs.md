# How to debug data using `System > Tools > Error Logs`
**Opencart** provides the **library file(log.php)** for debugging.  
You can debug data in any **controller** or **model** file.  
Use the code below in any of your files:

`$this->log->write($data); // $data variable contains the data to be debug`

See the output of debug data in Opencart’s dashboard `System > Tools > Error Logs`.
