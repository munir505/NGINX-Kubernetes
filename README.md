# NGINX-Kubernetes
##### Run All YAML Files, First cluster YAML, then all folder YAML files
##### Bellow Command Runs all YAML files in folders (Jenkins Nginx)
``` bash
kubectl create -f cluster-admin-role-binding.yml
kubectl create -f jenkins/ -f nginx/
```
##### Update and Install Vim
``` bash
apt update
apt install vim -y
```
##### Edit nginx.conf File
``` bash
vim /etc/nginx/nginx.conf
```
##### Need to create Disk called jenkins-jobs
``` bash
gcloud compute disks create jenkins-jobs --size <size> --zone <zone>
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
##### Use Command to Reload NGINX conf file
``` bash
nginx -s reload
```
##### May Need to Change Owner Ship of Jobs File in Jenkins Container
``` bash
sudo chown Jenkins:Jenkins <Folder/File>
```
