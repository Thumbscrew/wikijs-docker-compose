# Wiki.js (Docker Compose)

Docker Compose file for Wiki.js with PostgreSQL backend

## Docker Images Used

|image|link|
|-----|----|
|requarks/wiki|https://hub.docker.com/r/requarks/wiki|
|postgres|https://hub.docker.com/_/postgres|

## Prerequisites

1. [Docker](https://docs.docker.com/engine/install/)
2. [Docker Compose](https://docs.docker.com/compose/install/)
3. A reverse proxy on its own Docker network (optional)

### <a id="ReverseProxy">Reverse Proxy Docker Network</a>

This Docker Compose file assumes you have a reverse proxy (like Nginx) in a Docker container on another Docker network. If you are not using a reverse proxy or do not wish to use the Docker network to connect the reverse proxy, you can set the `DOCKER_PROXY_EXT` environment variable to `false` in your `.env` file. You may also need to expose the HTTP port on the `wiki` service.

## Setup

1. Create a copy of `.env.example`:

```bash
cp .env.example .env
```

2. Replace the `DOCKER_PROXY_NETWORK` variable with the Docker network where your reverse proxy sits (see [Reverse Proxy Docker Network](#ReverseProxy))

3. Replace `VOLUME_PATH` variable if you wish to change where volume data is stored

4. Modify other variables as needed

5. Create the following required secrets files (you should consider restricting access to these files):

- `secrets/postgres_password.txt`

6. Bring up the containers!

```bash
sudo docker-compose -p wiki up -d
```

7. Browse to the Wiki.js server and complete initial setup
