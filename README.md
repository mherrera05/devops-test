# DevOps Project

This project allows you create your own CI tools and Docker Swarm orquestator using Vagrant Images in a network with DHCP (No Static IP)
***

### Requeriment

You should have installed this package:
* Vagrant. Installation Steps
* VirtualBox. Installation Steps

### Installation

### Step 1
Clone this repository using git

```bash
$ git clone repo
```
### Step 2
Go to project folder and deploy Vagrant Virtual Machine

```bash
$ cd <project>/
$ vagrant up
```
### Step 3
Once Vagrantfile has been deployed you can verified their status with:

```bash
$ vagrant global-status

1fb55dd  portainer virtualbox running <folder>
2ac2b74  drone     virtualbox running <folder>
```

### Step 4
Open new terminal and connect with these machines via ssh

```bash
$ vagrant ssh portainer
```

Once inside get IP address given by virtualbox, you can use this:

```bash
$ ifconfig | grep 172.28

inet addr:172.28.x.x  Bcast:172.28.x.x  Mask:255.255.255.0
```

The IP address of your virtual machine in network shared with your local machine will be `inet addr:172.28.x.x`

You can do the same connecting to drone
```bash
$ vagrant ssh drone
```

### Step 5
Request the service of each virtual machine, as the first machine deployed an Portainer stack in the cluster, the port used is `30000`, you can request your service via `http`

Open you web browser and go to `http://172.28.x.x:30000 <---- IP address getted from portainer virtual machine`

In the case of drone, the port used is `80`, open a new tab and go to `http://172.28.x.x <---- IP address getted from drone virtual machine`
