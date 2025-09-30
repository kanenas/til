# Direct `rsync` with custom port
`rsync -av --partial --progress --timeout=60 -e "ssh -p 22000" /home/USERNAME1/public_html/image/products/ demo@dev-server:/home/USERNAME2/public_html/image/products/`
- Added `-e "ssh -p 22000"` to specify the custom SSH port
- Kept `--partial` for resumable transfers
- Kept `--timeout=60` for better connection handling 

`SOURCE_DIR = "/home/USERNAME1/public_html/image/products/"`  
`DEST = "demo@dev-server:/home/USERNAME2/public_html/image/products/"`  
`PORT = 22000`

Run this from your **source** server! You'll be prompted for the password for user `demo` on the `dev-server`.
