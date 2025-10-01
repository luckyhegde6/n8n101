# n8n101
Getting started with n8n

# n8n with PostgreSQL and Worker

Starts n8n with PostgreSQL as database, and the Worker as a separate container.

to update the database edit the .env file in the current directory.

## Start

To start n8n simply start docker-compose by executing the following
command in the current folder.

**IMPORTANT:** But before you do that change the default users and passwords in the [`.env`](.env) file!

```
docker-compose up -d
```

To stop it execute:

```
docker-compose stop
```

## Configuration

The default name of the database, user and password for PostgreSQL can be changed in the [`.env`](.env) file in the current directory.

example command to get stared with n8n docker
refer this [link](https://docs.n8n.io/getting-started/installation/docker/) for more details.   
for timezone list refer this [link](https://en.wikipedia.org/wiki/List_of_tz_database_time_zones)
```
docker volume create n8n_data

docker run -it --rm \
 --name n8n \
 -p 5678:5678 \
 -e GENERIC_TIMEZONE="Asia/Kolkata" \
 -e TZ="Asia/Kolkata" \
 -e N8N_ENFORCE_SETTINGS_FILE_PERMISSIONS=true \
 -e N8N_RUNNERS_ENABLED=true \
 -v n8n_data:/home/node/.n8n \
 docker.n8n.io/n8nio/n8n
```

## Access

Once running, you can access n8n by opening: http://localhost:5678

To use n8n with PostgreSQL, execute the following commands, replacing the placeholders (depicted within angled brackets, for example <POSTGRES_USER>) with your actual values:
```
docker volume create n8n_data

docker run -it --rm \
 --name n8n \
 -p 5678:5678 \
 -e GENERIC_TIMEZONE="Asia/Kolkata" \
 -e TZ="Asia/Kolkata" \
 -e N8N_ENFORCE_SETTINGS_FILE_PERMISSIONS=true \
 -e N8N_RUNNERS_ENABLED=true \
 -e DB_TYPE=postgresdb \
 -e DB_POSTGRESDB_DATABASE=<POSTGRES_DATABASE> \
 -e DB_POSTGRESDB_HOST=<POSTGRES_HOST> \
 -e DB_POSTGRESDB_PORT=<POSTGRES_PORT> \
 -e DB_POSTGRESDB_USER=<POSTGRES_USER> \
 -e DB_POSTGRESDB_SCHEMA=<POSTGRES_SCHEMA> \
 -e DB_POSTGRESDB_PASSWORD=<POSTGRES_PASSWORD> \
 -v n8n_data:/home/node/.n8n \
 docker.n8n.io/n8nio/n8n
 ```

 You can also use the command line to pull the latest, or a specific version:
```
# Pull latest (stable) version
docker pull docker.n8n.io/n8nio/n8n

# Pull specific version
docker pull docker.n8n.io/n8nio/n8n:1.81.0

# Pull next (unstable) version
docker pull docker.n8n.io/n8nio/n8n:next
```

After pulling the updated image, stop your n8n container and start it again. You can also use the command line. Replace <container_id> in the commands below with the container ID you find in the first command:

```
# Find your container ID
docker ps -a

# Stop the container with the `<container_id>`
docker stop <container_id>

# Remove the container with the `<container_id>`
docker rm <container_id>

# Start the container
docker run --name=<container_name> [options] -d docker.n8n.io/n8nio/n8n
```

To use webhooks for trigger nodes of external services like GitHub, n8n has to be reachable from the web. n8n runs a tunnel service that can redirect requests from n8n's servers to your local n8n instance.

Start n8n with --tunnel by running:
```
docker volume create n8n_data

docker run -it --rm \
 --name n8n \
 -p 5678:5678 \
 -e GENERIC_TIMEZONE="Asia/Kolkata" \
 -e TZ="Asia/Kolkata" \
 -e N8N_ENFORCE_SETTINGS_FILE_PERMISSIONS=true \
 -e N8N_RUNNERS_ENABLED=true \
 -v n8n_data:/home/node/.n8n \
 docker.n8n.io/n8nio/n8n \
 start --tunnel
 ```

 # Getting Started with n8n workflows
This guide will show you how to construct a workflow in n8n,
link - https://docs.n8n.io/advanced-ai/intro-tutorial/
