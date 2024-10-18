# How to Use Cloudflare Firewall Rules to Protect Your Web Application
How to protect against a wide range of malicious requests, bad bots, automated attacks, spam, and many other types of threats and nonsense?  
- Enable **Bot Fight Mode**  
- **IP Access Rules**: Security > WAF > Tools > IP Access Rules
- **Firewall Rules**: https://blog.runcloud.io/cloudflare-firewall-rules/

WordPress Firewall Rule (GR > Greece)  
`((http.request.uri.path contains "/xmlrpc.php") or (http.request.uri.path contains "/wp-login.php") or (http.request.uri.path contains "/wp-admin/" and not http.request.uri.path contains "/wp-admin/admin-ajax.php" and not http.request.uri.path contains "/wp-admin/theme-editor.php")) and ip.geoip.country ne "GR"`
