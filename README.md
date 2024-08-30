# platon
Bu Realsoft korxonasining Platon konstruktor platformasini dockerda o'rnatish uchun.
Birinchi o'rinda shu sahifadagi ma'lumotlar bilan tanishib chiqing.
bug-1 formadan file yuklaganda nginx 405 beradi shunda. nginx conf ni update qilish kerak.
```
upstream project {
    server 127.0.0.1:7001;
}

server {
    access_log  /var/log/nginx/access.log;
    error_log  /var/log/nginx/error.log;

    server_name _;

    proxy_buffers 8 32k;
    proxy_buffer_size 64k;
    client_max_body_size 64m;

    location /api/ {
        include proxy_params;
        proxy_pass         http://project/api/;
    }

    location / {
      root   /app/frontend/dist;
      index  index.html;
      try_files $uri $uri/ /index.html;
    }

    location /info {
        include proxy_params;
        proxy_pass         http://project/info;
    }

    location /web/ {
        include proxy_params;
        proxy_pass         http://project/web/;
    }

    location /utils/ {
        include proxy_params;
        proxy_pass         http://project/utils/;
    }
    location /mobile/ {
        include proxy_params;
        proxy_pass         http://project/mobile/;
    }
    location /common/ {
        include proxy_params;
        proxy_pass         http://project/common/;
    }
    location /export/ {
        include proxy_params;
        proxy_pass         http://project/export/;
    }
    location /import/ {
        include proxy_params;
        proxy_pass         http://project/import/;
    }
    location /auth/ {
        include proxy_params;
        proxy_pass         http://project/auth/;
    }
    location /instructions/ {
        include proxy_params;
        proxy_pass         http://project/instructions/;
    }
    location /sms/ {
        include proxy_params;
        proxy_pass         http://project/sms/;
    }
    location /document/ {
        include proxy_params;
        proxy_pass         http://project/document/;
    }
    location /uploads/ {
        include proxy_params;
        proxy_pass         http://project/uploads/;
    }
    location /files/upload/ {
        include proxy_params;
        proxy_pass         http://project/files/upload/;
    }
    listen 8080;
}
```
asosiy o'zgarish bu bilan bo'ladi:
```
    location /files/upload/ {
        include proxy_params;
        proxy_pass         http://project/files/upload/;
    }
```
