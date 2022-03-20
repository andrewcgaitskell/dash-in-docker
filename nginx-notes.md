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
    listen 80 default_server;
    listen [::]:80 default_server;
    root /var/www/html;
    server_name dmtools.info test.dmtools.info;
}


sudo certbot --nginx -d dmtools.info -d test.dmtools.info

