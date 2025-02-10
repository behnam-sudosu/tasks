# nginx

## install nginx
    apt update && apt install nginx
    systemctl status nginx
    ss -ntlp
        default port open 80

### config file
    sites-available ===>> config file here
    sites-enabled ===>> put link here to sites-available
    vim sites-enabled/default ===>> config here
        server{listen 8080 defaul_server;} ===>> change port
    nginx -t ===>> check your file is ok
    nginx -s reload or
    systemctl reload nginx
    welcome nginx ===>> cd /var/www/html


## reverce proxy
    


















