# telegram-webhook

### NGINX setup
```
location /webhooks/telegram/api/ {
    proxy_pass http://localhost:3223;
    proxy_http_version 1.1;
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection 'upgrade'; 
    proxy_cache_bypass $cookie_nocache $arg_nocache;
    alias /var/www/telegram-webhook/dist/;
    autoindex on; 
}

location /webhooks/telegram/ {
    alias /var/www/telegram-webhook/dist/; 
    try_files $uri $uri.html /$uri /index.html;
    index  index.html index.htm;
}
```
