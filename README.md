# DevOps Project

This project allows you create your own CI tools and [Docker Swarm](https://docs.docker.com/engine/swarm/) orquestator with just one Manager node in each cluster using [Vagrant](https://www.vagrantup.com/) Images provisioned with [Ansible](https://www.ansible.com/)

At the end you will have:

N° | VM | Docker | Cluster | IP
---------|---------|----------|---------|---------
vm-1 | docker-image | yes | yes | 172.28.128.100
vm-2 | drone-ci | yes | yes | 172.28.128.99
vm |  gitlab | yes | no | 172.28.128.98

![Diagram](https://raw.githubusercontent.com/mherrera05/devops-test/master/docs/diagram-vagrant.jpg)
***


### Requeriment

You should have installed this package:
* `Vagrant 2.0.2.` [Download](https://www.vagrantup.com/downloads.html)
* `VirtualBox 5.2.10.` [Download](https://www.virtualbox.org/wiki/Linux_Downloads)

### Installation

### Step 1
Clone this repository using git

```bash
$ git clone https://github.com/mherrera05/devops-test.git
```
### Step 2
Go to project folder and deploy Vagrant Virtual Machine in sequency

```bash
$ cd <project-folder>/
$ vagrant up gitlab
```

This machine will start with IP address 172.28.128.98

Request the service using http://172.28.128.98

### Step 3
Create a project in gitlab repository and setup application access for drone, go `Settings > Application > New Application`

In Authorization URL, add: `http://172.28.128.99/authorize`

### Step 4
Before start the CI virtual machine change `DRONE_GITLAB_CLIENT, DRONE_GITLAB_SECRET` for given by gitlab:

```yml
- DRONE_GITLAB=true
- DRONE_GITLAB_CLIENT=clientid
- DRONE_GITLAB_SECRET=secret
- DRONE_GITLAB_URL=http://172.28.128.98
- DRONE_GITLAB_SKIP_VERIFY=true
```

And start the virtual machine with

```bash
$ vagrant up drone
```

This machine will start with IP address 172.28.128.99

Request the service using http://172.28.128.99

### Step 5
To start the last virtual machine with docker image, just run:

```bash
$ vagrant up dockerimage
```

Request service using http://172.28.128.100

### Step 6
In the project folder

```bash
$ <project-folder>/
$ git remote add <repo> <url>
$ git add .
$ git push <repo> master
```
To push the project to the new repository and trigger the build

### Step 6
Triggering the pipeline, it will connect via ssh with docker-image virtual machine and run ansible code.

## Enjoy!