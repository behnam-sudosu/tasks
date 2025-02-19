# nginx

## install nginx
    apt update && apt install nginx
    systemctl status nginx
    ss -ntlp
        default port open 80

### config file
    cd /etc/nginx
    sites-available ===>> config file here
    sites-enabled ===>> put link here to sites-available
    vim sites-enabled/default ===>> config here
        server{listen 8080 defaul_server;} ===>> change port
        server_name _; ===>> you can put your doman name instate of _
    nginx -t ===>> check your file is ok
    nginx -s reload or
    systemctl reload nginx
    welcome nginx ===>> cd /var/www/html

## reverse proxy
### server1
    cd /etc/nginx
    cd /etc/nginx/sites-enabled ===>> best practice unlink default
    cd /etc/nginx/site-available
    vim reverse.conf
        server {
            listen 80;
            server_name _;
            access_log /var/log/nginx/re-access.log;
            error_log /var/log/nginx/re-error.log;
            location /app1 {
                proxy_pass http://192.168.1.110/;
            }
            location /app1 {
                proxy_pass http://192.168.1.111/;
            }
        }
        or
        server {
            listen 80;
            server_name _;
            access_log /var/log/nginx/re-access.log;
            error_log /var/log/nginx/re-error.log;
            location /app1 {
                proxy_pass http://192.168.1.110:5000/; ===>> change vim /etc/nginx/sites-enabled to port 5000
            }
        }
    nginx -t
    ln -s /etc/nginx/sites-available/reverse.conf /etc/nginx/sites-enabled/reverse.conf
    nginx -t
    nginx -s reload

## load balance
    
















