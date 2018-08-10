_work in progress!_

This aims to install Elasticstack via Docker on Xubuntu 18.04. YMMV.

## Install Docker from Official Repo
```
apt update
apt-get install curl
apt install apt-transport-https ca-certificates curl software-properties-common
echo 'deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable' >> /etc/apt/sources.list.d/docker.list
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
apt update
apt install docker-ce
```

## Install Docker-Compose
```
curl -L https://github.com/docker/compose/releases/download/1.20.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
```

## Pull Elasticstack Image
```
git clone https://github.com/elastic/stack-docker /user/share/elastic
sysctl -w vm.max_map_count=262144
```

## Prepare for install
Set the PWD Environment Variable
```
echo 'PWD=/usr/share/elastic/' >> /usr/share/elastic/.env
```

## Create Elasticstack Container
```
docker-compose -f .\setup.yml up
```