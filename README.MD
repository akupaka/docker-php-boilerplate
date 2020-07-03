# Utility project to dockerize local PHP development environment

## Commands to work with Docker

### Building or rebuilding containers

    $ docker-compose build --parallel

### Starting containers

    $ docker-compose up -d

### Stopping containers temporarily

    $ docker-compose stop

### Stopping and removing containers

    $ docker-compose down

### Removing volumes when project is removed

Listing volumes

    $ docker volume ls
    
Removing volumes by name or id

    $ docker volume rm id

Removing all unused volumes (use carefully)

    $ docker volume prune
    
### Connecting to shell

Connecting as default user

    $ docker exec -it containerId bash

Connecting as root user

    $ docker exec -u 0 -it containerId bash

