# NGINX-Kubernetes
##### Run All YAML Files

##### Update and Install Vim
``` bash
apt update
apt install vim -y
```
##### Edit nginx.conf File
``` bash
vim /etc/nginx/nginx.conf
```
##### NGINX Config File
```
events{}

http {
        server {
                listen 80;
                location / {
                        proxy_pass http://jenkins:8080/;
                }
        }
}
```
