https://pentacent.medium.com/nginx-and-lets-encrypt-with-docker-in-less-than-5-minutes-b4b8a60d3a71

# install nginx on main vm

https://ubuntu.com/tutorials/install-and-configure-nginx#2-installing-nginx

# test

# install letsencrypt

apt-get update
sudo apt-get install certbot
python3 --version
sudo apt install python3-certbot-nginx


server {
    listen 80;
    listen [::]:80;

    root /var/www/test.dmtools.info/public_html;

    index index.html;

    server_name test.dmtools.info;

    access_log /var/log/nginx/test.dmtools.info.access.log;
    error_log /var/log/nginx/test.dmtools.info.error.log;

    location / {
        try_files $uri $uri/ =404;
    }
}


sudo ln -s /etc/nginx/sites-available/test.dmtools.info /etc/nginx/sites-enabled/

sudo certbot --nginx -d test.dmtools.info

## after certbot


server {
    listen 80;
    listen [::]:80;

    root /var/www/test.dmtools.info/public_html;

    index index.html;

    server_name test.dmtools.info;

    listen [::]:443 ssl ipv6only=on; # managed by Certbot
    listen 443 ssl; # managed by Certbot
    ssl_certificate /etc/letsencrypt/live/test.dmtools.info/fullchain.pem; # managed by Certbot
    ssl_certificate_key /etc/letsencrypt/live/test.dmtools.info/privkey.pem; # managed by Certbot
    include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot

    access_log /var/log/nginx/test.dmtools.info.access.log;
    error_log /var/log/nginx/test.dmtools.info.error.log;

    location / {
        try_files $uri $uri/ =404;
    }
}

server {
    if ($host = test.dmtools.info) {
        return 301 https://$host$request_uri;
    } # managed by Certbot


    listen 80;
    listen [::]:80;
    server_name test.dmtools.info;
    return 404; # managed by Certbot
}

server {
    root /var/www/html;
    server_name test.dmtools.info;

    listen [::]:443 ssl ipv6only=on; # managed by Certbot
    listen 443 ssl; # managed by Certbot
    ssl_certificate /etc/letsencrypt/live/test.dmtools.info/fullchain.pem; # managed by Certbot
    ssl_certificate_key /etc/letsencrypt/live/test.dmtools.info/privkey.pem; # managed by Certbot
    include /etc/letsencrypt/options-ssl-nginx.conf; # managed by Certbot
    ssl_dhparam /etc/letsencrypt/ssl-dhparams.pem; # managed by Certbot

}
server {
    if ($host = test.dmtools.info) {
        return 301 https://$host$request_uri;
    } # managed by Certbot


    listen 80;
    listen [::]:80;
    server_name test.dmtools.info;
    return 404; # managed by Certbot


}



Congratulations! Your certificate and chain have been saved at:
   /etc/letsencrypt/live/test.dmtools.info/fullchain.pem
   Your key file has been saved at:
   /etc/letsencrypt/live/test.dmtools.info/privkey.pem
   Your certificate will expire on 2022-06-18. To obtain a new or
   tweaked version of this certificate in the future, simply run
   certbot again with the "certonly" option. To non-interactively
   renew *all* of your certificates, run "certbot renew"



# useful system commands

        sudo nginx -t
        sudo nginx -s reload

        sudo systemctl stop nginx
        sudo systemctl start nginx
        sudo systemctl status nginx
        

