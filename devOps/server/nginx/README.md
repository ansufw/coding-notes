# Config file


```sh
server {
        listen 80;
        listen [::]:80;

        root /var/www/www;
        index index.html index.htm index.php;

        server_name halaldev.my.id www.halaldev.my.id;

        location / {
                try_files $uri $uri/ =404;
        }


}
~   
```
