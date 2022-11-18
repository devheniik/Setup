# Install Docker
```bash
sudo apt-get update 
sudo apt-get install \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
 ```
 
 ```bash
 sudo mkdir -p /etc/apt/keyrings
 curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

```bash
 echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

```bash
sudo apt-get update
```

```bash
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

 ### Check docker
 
```bash
sudo docker run hello-world
``` 



# Install nginxproxymanager

```bash docker volume create nginxproxymanager-data
docker volume create nginxproxymanager-letsencrypt

docker run -d \
  --restart=unless-stopped \
  --net=host \
  -p 80:80 \
  -p 443:443 \
  -p 81:81 \
  -v nginxproxymanager-data:/data \
  -v nginxproxymanager-letsencrypt:/etc/letsencrypt \
  --name nginxproxymanager \
  jc21/nginx-proxy-manager:latest
```
  
  # Install Firewall
  
  ```bash
    apt install ufw && ufw deny 81 && ufw allow ssh
  ```
  
  ### Write in new console
  
  ```bash 
    ufw enable
  ```