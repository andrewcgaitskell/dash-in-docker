
# Resisting Installing Docker on Local Machine

I did not want to develop and deploy containers on my local Linux or Mac machine.

I considered creating ubuntu vm with vnc running.

I was getting there, but a wise chap told me about the following:

https://code.visualstudio.com/remote/advancedcontainers/develop-remote-host

# VM Setup

    sudo apt update
    sudo apt upgrade

# Add SSH key to VM using Console



https://docs.docker.com/engine/install/ubuntu/#prerequisites

https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository

curl -fsSL https://get.docker.com -o get-docker.sh

sudo sh get-docker.sh

# Install nginx


https://www.nginx.com/blog/deploying-nginx-nginx-plus-docker/

sudo docker run --name mynginx1 -p 80:80 -d nginx

docker ps



http://35.214.9.0/
