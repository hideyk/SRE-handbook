---
title: Configure
tags: 
 - docker
description: Configure server for Docker
---

# Server configuration for Docker

## Manage Docker as a non-root user
The Docker daemon binds to a Unix socket instead of a TCP port. By default that Unix socket is owned by the `root` user and other users can only access it using `sudo`. The Docker daemon always run as the `root` user. 

Create a `docker` group and add your non-root user to it to manage your Docker services. 

1. Create the `docker` group
```bash
sudo groupadd -f docker
```

2. Add your user to the `docker` group
```bash
sudo usermod -aG docker $USER
```

3. On Linux, run the following command to activate changes to groups
```bash
newgrp docker
```

4. Verify that you can run `docker` commands without sudo
```bash
docker -version
```


## Configure Docker to start on boot

```bash
sudo systemctl enable docker.service
sudo systemctl enable containerd.service
```

## Configure default logging driver
Docker provides the capability to collect and view log data from all containers running on a host via a series of logging drivers. The default logging driver, json-file, writes log data to JSON-formatted files on the host filesystem. Over time, these log files expand in size, leading to potential exhaustion of disk resources.

To alleviate such issues, either configure the json-file logging driver to enable log rotation, use an alternative logging driver such as the “local” logging driver that performs log rotation by default, or use a logging driver that sends logs to a remote logging aggregator.

## Configure remote access 
It is possible to allow Docker to accept requests from remote hosts by configuring it to listen on an IP address and port as well as the UNIX socket. 


### Configure remote access with `systemd` unit file
1. Open an override file for `docker.service` in a text editor
```bash
sudo systemctl edit docker.service
```

2. Add or modify the following lines, substituting your own values, then save the file
```bash
[Service]
ExecStart=
ExecStart=/usr/bin/dockerd -H fd:// -H tcp://127.0.0.1:2375
```

3. Reload the `systemctl` configuration and restart Docker
```bash
sudo systemctl daemon-reload
```
```bash
sudo systemctl restart docker.service
```

4. Check to see whether the change was honored by reviewing the output of `netstat` to confirm `dockerd` is listening on the port
```bash
sudo netstat -lntp | grep dockerd
```



### Configure remote access with `daemon.json` 
1. Set the `hosts` array in the `/etc/docker/daemon.json` to connect to the UNIX socket and an IP address:
```json
{
  "hosts": ["unix:///var/run/docker.sock", "tcp://127.0.0.1:2375"]
}
```

2. Restart Docker

3. Check to see whether the change was honored by reviewing the output of `netstat` to confirm `dockerd` is listening on the port
```bash
sudo netstat -lntp | grep dockerd
```