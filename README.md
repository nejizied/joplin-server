# Joplin Server Deployment with Docker-Compose

This repository provides a Docker Compose setup for deploying [Joplin Server](https://joplinapp.org/), an open-source note-taking and to-do application. The setup includes a PostgreSQL database and the Joplin Server, all configured to run seamlessly with Docker Compose.

## Prerequisites

Before deploying the Joplin Server with Docker Compose, ensure that you have the following installed on your machine:

- Docker ([Install Docker](https://docs.docker.com/get-docker/))
- Docker Compose ([Install Docker Compose](https://docs.docker.com/compose/install/))

## Project Structure

The repository contains the following files and directories:

- `docker-compose.yml`: The Docker Compose configuration file to start the services.
- `.env`: The environment variables file used to configure the Docker containers (see details below).
- `data/`: A directory for persisting the PostgreSQL data.

## Environment Variables

The `.env` file is used to set the environment variables needed by both the Joplin Server and the PostgreSQL database. 

Create a `.env` file in the root directory of this repository and define the following variables:

```dotenv
POSTGRES_PASSWORD=your_postgres_password
POSTGRES_USER=your_postgres_user
POSTGRES_DB=your_postgres_database
APP_URL=http://your-domain-or-ip:22300
````

# Deploying Joplin Server

To deploy the Joplin Server with Docker Compose, follow these steps:

## 1. Clone this repository:

```bash
git clone https://github.com/yourusername/joplin-server-docker.git
cd joplin-server-docker
```

## 2. Create a .env file in the root of the project and fill in your environment variables as described above.

## 3. Build and start the Docker containers:

```bash
docker-compose up -d
```

This will pull the necessary images (if not already pulled), create the containers, and start them in the background.

## 4. Verify that the services are running:
```bash
docker-compose ps
OR
docker ps -a
```
You should see the db and app containers running.

Access Joplin Server by visiting http://your-domain-or-ip:22300 in your browser.

# Backups

The PostgreSQL database is configured to persist its data in the ./data/postgres directory on your host machine. You can back up this directory to ensure that your notes and data are safe.

# Customization

You can modify the docker-compose.yml file and the ``.env`` file to customize the Joplin server deployment further. For example:

Modify the ports if you have conflicts or want to expose the services differently.

Adjust the resource limits or add additional services as needed.

# Troubleshooting

## 1. Cannot connect to PostgreSQL database:

Make sure the ``POSTGRES_PASSWORD``, ``POSTGRES_USER``, and ``POSTGRES_DB`` are correctly set in the **``.env``** file and match the ones in the Docker Compose file.

## 2. App is not accessible

Check the logs for any errors by running:

```bash

docker-compose logs app
OR docker logs -f <container_name/container_id>
```

## 3. Out of storage

Ensure that the data/postgres directory has enough space for the database.

# Reverse Proxy

If you want to use a reverse proxy (ex: Nginx) with your domain, please make sure to update ``Line 3`` in the **`nginx_joplin_server.conf`** and ``line 23`` in **``docker-compose.yml``* with your custom domain, otherwise you will not be able to access your application and you will encounter. ``Invalid origin: http://ip-addr:22300`` Error
