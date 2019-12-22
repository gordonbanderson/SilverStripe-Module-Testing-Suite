# SilverStripe-Module-Testing-Suite
Run silverstripe module unit tests in a Dockerized environment

# How To Use
## Clone Your Repo
Your module must be cloned into a directory called module.  This is a small module you can use to get a feel of how
running tests work using this Docker setup

```bash
git clone https://github.com/gordonbanderson/silverstripe-sluggable.git module
```

Change branch if so required.

## Build The Docker Containers
```bash
sudo docker-compose build web
```

## Copy Environment File
This file contains the credentials for the mariadb container in order to access MySQL
```bash
cp .env module/
```


## Run The Containers
```bash
sudo docker-compose up -d web
```

## Get a Shell
```bash
sudo docker-compose exec web /bin/bash
```

## Prime Module
In the web container terminal

```bash
prime-module-for-testing
```

This$xslt install SilverStripe from recipe and all of the other dependencies from your composer.json file


## Run Tests With Coverage
```bash
generate-html-coverage
```

# Changing The Module Being Tested
On the host computer
```bash
docker stop $(docker ps -a -q)
sudo rm -rf module
```

This stops all docker containers running and removes the module.

Clone module as above, and execute steps to get a shell on the Docker web container.  Then run this to remove the previous
incarnation:

```bash
rm -rf /tmp/silverstripe-cache-php7.3.12-var-www-html/
```
