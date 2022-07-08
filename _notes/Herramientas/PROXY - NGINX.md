---
title: NGINX Proxy
season: summer
tags: AWS Cloud Devops EC2 proxy nginx
toc: true
comments: true
---
### Archivo server

#### https://techexpert.tips/es/nginx-es/nginx-configuracion-de-proxy/
solo http
``` 
server {

    if ($http_x_forwarded_proto = "https") {
        return 301 https://$server_name$request_uri;
  }

    listen 80 default_server;
    listen [::]:80 default_server;
    listen 443 default_server;
    listen [::]:443 default_server;

    server_name proxy.hrbotfactory.com;
    #if ($request_filename ~ /*){
     #   rewrite ^ https://stg-api.hrbotfactory.com/docs? permanent;
     #}    
     #root /var/www/html;

    location / {
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $host;
            proxy_pass https://stg-api.hrbotfactory.com/docs;
            #proxy_pass http://hrbotfactory-stg-alb-1226904802.eu-west-1.elb.amazonaws.com;
            #proxy_set_header Authorization a2luZzppc25ha2Vk;
            #proxy_pass_header Authorization;
            #proxy_set_header Authorization "Basic usuariostg:passwordSTG";
            proxy_set_header X-NginX-Proxy true;
            proxy_set_header X-Forwarded-Proto https;
            proxy_redirect off;
            #set_real_ip_from    54.73.217.181;
            #real_ip_header      X-Forwarded-For;
            auth_basic "Restricted";
            auth_basic_user_file /etc/nginx/htpasswd;
        }
} 
```

https
```
server {

    if ($http_x_forwarded_proto = "http") {
        return 301 https://$server_name$request_uri;
  }

    server_name proxy.hrbotfactory.com;
    ssl_certificate /etc/letsencrypt/live/proxy.hrbotfactory.com/fullchain.pem; # managed by Certbot
    ssl_certificate_key /etc/letsencrypt/live/proxy.hrbotfactory.com/privkey.pem; # managed by Certbot
    include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot
     #root /var/www/html;

    location / {
            proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header X-Forwarded-For $host;
            proxy_pass https://stg-api.hrbotfactory.com/docs;
            #proxy_pass http://hrbotfactory-stg-alb-1226904802.eu-west-1.elb.amazonaws.com;
            #proxy_set_header Authorization a2luZzppc25ha2Vk;
            #proxy_pass_header Authorization;
            #proxy_set_header Authorization "Basic usuariostg:passwordSTG";
            proxy_set_header X-NginX-Proxy true;
            proxy_set_header X-Forwarded-Proto http;
            proxy_redirect off;
            #set_real_ip_from    54.73.217.181;
            #real_ip_header      X-Forwarded-For;
            auth_basic "Restricted";
            auth_basic_user_file /etc/nginx/htpasswd;
        }

    #if ($host = proxy.hrbotfactory.com) {
     #  return 301 https://$host$request_uri;
    #} # managed by Certbot



    #listen 80 default_server;
    #listen [::]:80 default_server;
    listen 443 default_server;
    listen [::]:443 default_server;

    #server_name proxy.hrbotfactory.com;
   # return 404; # managed by Certbot


}

```
proxy cambio encabezado 
HRBOT funciono
```
server {

    if ($http_x_forwarded_proto = "http") {
        return 301 https://$server_name$request_uri;
  }

    server_name proxy.hrbotfactory.com;
    ssl_certificate /etc/letsencrypt/live/proxy.hrbotfactory.com/fullchain.pem; # managed by Certbot
    ssl_certificate_key /etc/letsencrypt/live/proxy.hrbotfactory.com/privkey.pem; # managed by Certbot
    include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot
     #root /var/www/html;


    location /api/ {
            #proxy_set_header Accept-Encoding "";
            ##proxy_set_header Host $host;
            proxy_set_header X-Real-IP $remote_addr;
            #proxy_set_header X-Real-IP $host;
            ##proxy_set_header Upgrade $http_upgrade;
            ##proxy_set_header Connection "upgrade";
            ##proxy_set_header    X-Forwarded-Server      $host;
            ##proxy_set_header X-Forwarded-For $host;
            ##proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_pass https://api.hrbotfactory.com/api/;
            #proxy_pass http://hrbotfactory-stg-alb-1226904802.eu-west-1.elb.amazonaws.com;
            #proxy_set_header Authorization a2luZzppc25ha2Vk;
            #proxy_pass_header Authorization;
            #proxy_set_header Authorization "Basic usuariostg:passwordSTG";
            proxy_set_header X-Forwarded-Host $host;
            proxy_set_header X-Forwarded-Port $server_port;
            ##proxy_set_header X-NginX-Proxy true;
            ##proxy_set_header X-Forwarded-Proto $scheme; 
            ##proxy_redirect off;
            ##set_real_ip_from    10.35.11.230;
            ##real_ip_header      X-Forwarded-For;
            auth_basic "Restricted";
            auth_basic_user_file /etc/nginx/htpasswd;
        }

    #if ($host = proxy.hrbotfactory.com) {
     #  return 301 https://$host$request_uri;
    #} # managed by Certbot



    #listen 80 default_server;
    #listen [::]:80 default_server;
    listen 443 default_server;
    listen [::]:443 default_server;

    #server_name proxy.hrbotfactory.com;
   # return 404; # managed by Certbot


}
```

#nginx
[[Instalar Nginx]]
[[Cómo proteger Nginx con Let´s Encrypt en Ubuntu 20.04]]