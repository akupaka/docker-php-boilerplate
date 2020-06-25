# Utility project to dockerize local PHP development environment

## Commands to work with Docker

Replace `project_name` with suitable value so containers included in projects displayed separately

### Building or rebuilding containers

    $ docker-compose -p project_name -f docker/docker-compose.yml build --parallel

### Starting containers

    $ docker-compose -p project_name -f docker/docker-compose.yml up -d

### Stopping containers temporarily

    $ docker-compose -p project_name -f docker/docker-compose.yml stop

### Stopping and removing containers

    $ docker-compose -p project_name -f docker/docker-compose.yml down

### Removing volumes when project is removed

Listing volumes

    $ docker volume ls
    
Removing volumes by name or id

    $ docker volume rm id

Removing all unused volumes (use carefully)

    $ docker volume prune
    
