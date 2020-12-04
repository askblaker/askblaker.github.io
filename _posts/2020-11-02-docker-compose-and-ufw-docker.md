---
title: Docker-compose with ufw-docker in Ubuntu 20.04
categories:
- docker
- docker-compose
- ufw-docker
- ufw
---

## Introduction

During development using docker-compose on Ubuntu, I realized something weird was happening with my UFW. It just did not work as it should. Publishing ports in docker-compose just overrid any UFW settings.

Needless to say, this is not desirable. And it turns out it is not even that easy to solve. The current best solution i have found is [ufw-docker](https://github.com/chaifeng/ufw-docker)

### Quick Start

1. Download the script

   > sudo wget -O /usr/local/bin/ufw-docker \\  
   > https://github.com/chaifeng/ufw-docker/raw/master/ufw-docker  
   > sudo chmod +x /usr/local/bin/ufw-docker  
   > sudo ufw-docker install  
   > sudo ufw-docker allow traefik 443  
   > sudo ufw-docker delete allow traefik 443

   Note! If you use `docker-compose down` and `docker-compose up`, the ip-address of the container might change, and you need to repeat the process.
