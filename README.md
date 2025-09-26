# n8n-onPremise
Install n8n on_premsise
Add Rancher Helm Repository

EN LAS VM1 VM2 

sudo apt update && sudo apt upgrade -y
sudo apt install -y curl wget git unzip ufw

change ip static
cd /etc/netplan
vi 00-netplam.

#permisos solo root
sudo chmod 600 /etc/netplan/00-installer-config.yaml


network:
  version: 2
  renderer: networkd
  ethernets:
    ens33:
      dhcp4: no
      addresses:
          - 192.168.78.132/24
      routes:
        - to: default
          via: 192.168.78.2
      nameservers:
        addresses: [8.8.8.8,8.8.4.4]


##Instalar Docker y Docker Compose:
curl -fsSL https://get.docker.com | sh
sudo usermod -aG docker $USER
newgrp docker
sudo apt install -y docker-compose

#Base de datos y Redis (VM2)
mkdir -p ~/n8n_db && cd ~/n8n_db
nano docker-compose.yml

#levantar docker compose
docker-compose up -d

docker ps -a

cambio
cd ~/n8n
sudo chown -R 1000:1000 n8n_data
docker compose down
docker compose up -d

curl -I https://





