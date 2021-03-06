# Installation instructions

This usecase shows configuration using Docker.

## Assumptions
1. This repository is cloned and docker-config is in working directory. 
2. Azure or AWS subscription is available
3. Docker, Docker-compose and Docker-machine is installed 

## Steps to run via CLI 

### 1. Create docker-machine in cloud provider 
```shell
docker-machine create -d azure \
  --azure-ssh-user dockeruser \
  --azure-subscription-id <Your AZURE_SUBSCRIPTION_ID> \
  --azure-open-port 443 \
  identitybpa
```
### 2. Check the ip address of new docker-machine 
```shell
docker-machine ls
```
### 3. Configure local shell for new docker-machine by running following comand and following instructions
```shell
docker-machine env machine
```
### 4. Point subdomain to ip addrress of new docker-machine
### 5. Bring up docker containers 
```shell
docker-compose -f .\docker-compose-identity.yml -f .\docker-compose-proxy.yml up
```
