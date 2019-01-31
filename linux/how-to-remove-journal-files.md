# How to remove journal files

#### How to remove archived journal files
`$ sudo journalctl --vacuum-time=1d`


#### How to remove all journal files
`$ sudo journalctl --rotate`  
`$ sudo journalctl --vacuum-time=1s`
