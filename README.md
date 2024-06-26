# azure-vm-agent

Azure Pipelines virtual machine deployment agent running as a Docker container, replicated using Swarm.

## System requirements

- Docker
- Docker Compose

## Build

You only need to build if you change the source.
Otherwise, the image will be pulled automatically.

```bash
docker-compose build
```

## Configure

Fill in missing configuration in the `environment` section of `docker-compose.yaml`.
Create a directory on the host to host jobs data and Docker tasks volumes:

```bash
sudo mkdir -p /azvm/_work
```

`AZVM_TOKEN` can be obtained from User settings -> Personal Access Token -> + New Token (Read+Write+Manage permission)

## Run

```bash
docker swarm init # for the first time only
docker stack deploy -c docker-compose.yaml azvmagent
```
