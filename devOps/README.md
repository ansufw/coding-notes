# Tools

- Docker
- Kubernetes
- Portainer
- Vagrant

## Portainer

Install portainer in docker:    

First, create the volume that Portainer Server will use to store its database

```sh
docker volume create portainer_data
```

create Portainer Server container

```sh
docker run -d -p 8000:8000 -p 9443:9443 --name portainer \
    --restart=always \
    -v /var/run/docker.sock:/var/run/docker.sock \
    -v portainer_data:/data \
    cr.portainer.io/portainer/portainer-ce:2.9.3
```

then, login via web browser `https://localhost:9443`