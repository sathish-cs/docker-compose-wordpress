## Containerizing wordpress website with docker compose

### Prerequisites

* Install docker

* Install docker-compose

### Docker compose

Version is defined in docker compose file to use

`Version: '3'`


Services are used to define types of containers to run. Below containers are using in docker compose

* Ngnix
* Wordpress
* Mysql

### Mysql

* Passing mysql credentials using .env file
* Creating mysql container in app-network
* Mounting DB volume into dbdata


### Wordpress

* Wordpress depends on database, without that it cant be come up. So `depends_on` ensures container only starts services once it depends are running
* Passed database credentials to wordpress
* Mounted wordpress volume in to wordpress

### Webserver

* Using nginx we route traffic to wordpress
* Mounting customized nginx config to /etc/nginx/conf.d # defined localhost as server name, in production it has to replace with domain.
* Exposing container port to host

### Volumes

* `dbdata` and `wordpress` volume will be stored under /var/lib/docker/volumes in host machine.

### Initialize docker containers

* `docker-compose up -d`

Finally its can be accessible using `localhost:8080` to setup wordpress site.
