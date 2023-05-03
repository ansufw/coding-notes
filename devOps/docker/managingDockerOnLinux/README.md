# Managing Docker on Linux Server

highlightnote:
- docker socket is a dependency of the docker service
- containerd service is also a dependency of the docker service

## Installing docker for your distro

- read docs https://docs.docker.com/engine/
- choose your distro!
    - centos-8
    - ubuntu-22
- check running service `ls /var/run`, if there is no docker running, then
- check version `docker version` and
- check status
    - docker service `systemctl status docker.service`
    - docker socket `systemctl status docker.socket`
- if the statuses not running, start
    - docker service `systemctl start docker.service`
    - docker socket `systemctl start docker.socket`
- if system asked for password, run `sudo passwd ubuntu`
- check the permision `ls -al /var/run/docker.sock`, you may see the access only for user root and group docker
- check current group `groups` 
- check again version but with sudo `sudo docker version`
- add vagrant to docker group with `sudo usermod -aG docker $USER`, and `sudo groupadd docker` if docker group is not exist yet.
- restrart user `su -l $USER` and type password `vagrant`, then check again `groups` and `docker version`
- check all status `systemctl list-unit-files`
- check inside list `cat /etc/systemd/system/multi-user.target.wants/docker.service`
- check docker and containerd by running `rpm -ql [docker-ce|containerd.io|docker-ce-cli]` for centos or `dpkg -L [docker-ce|containerd|docker-ce-cli]` for ubuntu

## Using Docker Context

### Command to Container

- 🖥️ docker command
- 🔌 unix socket (IPC) to API, root:docker
- 🔗 docker engine API (create container, list image, etc)
- 🐳 docker engine daemon (dockerd) execute the incoming API task / query
- 📦  containers (isolated process) & associated resources: images, mounts/filesytem, networking, processes, cgroups, security.
