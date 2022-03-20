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
    server_name test.dmtools.info;
}


sudo certbot --nginx -d test.dmtools.info

Congratulations! Your certificate and chain have been saved at:
   /etc/letsencrypt/live/test.dmtools.info/fullchain.pem
   Your key file has been saved at:
   /etc/letsencrypt/live/test.dmtools.info/privkey.pem
   Your certificate will expire on 2022-06-18. To obtain a new or
   tweaked version of this certificate in the future, simply run
   certbot again with the "certonly" option. To non-interactively
   renew *all* of your certificates, run "certbot renew"


sudo ln -s /etc/nginx/sites-available/test.dmtools.info /etc/nginx/sites-enabled/

