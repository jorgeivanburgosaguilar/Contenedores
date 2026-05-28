# Comandos de docker

## Docker compose

### Arrancar
docker compose up -d

### Apagar
docker compose down

### Iniciar instancia
docker compose exec [nombre-instancia] bash


## Docker images

### Build an image
docker build -t my-image .

### Run a container
docker run -p 3000:3000 my-image

### Get a shell inside a running container (use docker ps to find the ID)
docker exec -it <container_id> /bin/bash

### Stop a container
docker stop <container_id>

### Clean up old images and containers
docker system prune -f

### Get a shell inside a running container
docker exec -it <container_id> /bin/bash

### Get a shell in a fresh container from an image
docker run -it your-image /bin/bash

### See what containers are running
docker ps

### See logs from a container
docker logs <container_id>

### Copy a file out of a container
docker cp <container_id>:/app/output.log ./output.log

### Pin a commit for reproducibility
RUN git clone https://github.com/org/repo.git /app && \
    cd /app && git checkout abc123def

### Install system packages
RUN apt-get update && apt-get install -y \
    postgresql redis-server curl && \
    rm -rf /var/lib/apt/lists/*

### Pin Python dependencies
COPY requirements.pinned.txt .
RUN pip install --no-cache-dir -r requirements.pinned.txt

### Make scripts executable
COPY startup.sh /startup.sh
RUN chmod +x /startup.sh

### Set defaults that can be overridden
ENV DATABASE_URL=postgresql://postgres:postgres@localhost:5432/appdb
ENV REDIS_URL=redis://localhost:6379