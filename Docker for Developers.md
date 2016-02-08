#Docker for Developers
##Chris Tankersley [@dragonmantank](https://twitter.com/dragonmantank)

[slides](http://www.slideshare.net/ctankersley/docker-for-developers-57978920)

###basic docker

- docker machine is a bare metal provisioning tool
- docker swarm is a load-balancing deployment tools
- docker compose 
- - Docker toolbox uses docker2boot image VM

### docker API

- image: is a state of a binary
- container: is created from an image
- docker runs a root
	- when a container is booted it generates as root screwing permissions
	- mounting volumes exposes root from container to host
- docker volume requires full path 
	- must be careful when setting paths (`pwd` for `linux / osx`)

### why not run ssh inside docker

- Docker is designed for one command per container
- if toy need to modify data, then you need to chane tour setup
- if you have to run ssh, then you need a wat to tun ssh and your command

### go through the hassle

- data volumes are portable and safer
- saparetes the app container from data
	- production can use a data volume, dev can use vhost volume

### notes
- networkig to links containers
	- name of linke becomes hostname in container

### docker machine

- a provisioning tool that is used to ser up a box with Docker
- used in docker toolbox to create the VM
- ssh into docekr machine : `docker-machine ssh VM_NAME`

### swarm
- create a cluster
- uses tokens tp add to cluster
- must defined swarm master

### Docker compose
- multi-container orchestration
- config holds container info
- docker-compose.yml

### deploying to production
- with data volumes must deploy to one server, volumes dont exist on other swarm-nodes
- `Rancher` [deploy, app managing tool](http://rancher.com/)
	- allows volumes hsaring accross host
	- GUI
	- works with docker-compose file
	- export docker compose file
		- can pass ENV variables
	- Manage environments
