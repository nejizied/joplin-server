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

