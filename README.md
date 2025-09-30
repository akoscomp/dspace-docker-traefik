# DSpace 9.1 in docker with traefik proxy

## Configure

Create from each env.sample file an .env file and set all variable to a valid hostname

## Start DSpace

### Create required networks

```bash
docker network create proxy
docker network create dspacenet
```

### Start the containers

```bash
cd traefik
docker compose up -d

cd api
docker compose up -d

cd ui
docker compose up -d
```

## Check it

With `https://api.example.com/server/` can check the backend.

With `https://ui.example.com/` can check the frontend.

## Create admin account

```bash
cd cli
docker-compose run --rm dspace-cli create-administrator -e test@example.com -f admin -l user -p admin -c en
```
