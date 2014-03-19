cbsd-wwwdoc
===========

cbsd documentation part for http://bsdstore.ru site

nginx-vhost.conf sample for site:

server {
        listen       *:80;
        server_name  bsdstore.ru www.bsdstore.ru;
        access_log /var/log/httpd/www.bsdstore.ru.acc main buffer=1m;
        error_log /var/log/httpd/move.err;

        root   /usr/home/web/www.bsdstore.ru;

        location ~* \.(css|txt|html|js|xsl)$ {
            ssi on;
            ssi_types text/css text/javascript application/x-javascript;
        }

        location ~* \.(jpg|jpeg|gif|png|swf|tiff|swf|flv|zip|rar|bz2|iso|xz|img)$ {
            add_header Cache-Control "public";
        }

        rewrite ^/$ /en/about.html permanent;

        error_page      404     /404.html;
}
