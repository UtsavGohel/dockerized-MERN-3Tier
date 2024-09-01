# MERN Stack Application Dockerization

This repository contains a sample MERN (MongoDB, Express, React, Node.js) stack application configured to run inside Docker containers. The application is divided into three main tiers:

```sh
Backend - Node.js and Express
Frontend - React
Database - MongoDB
```

- ## Prerequisites/Tools
- Before you begin, ensure you have the following installed on your machine:

- Docker (including Docker Compose)
- Node.js (for development and testing)

- ## Project Structure
```sh
/mern
  /backend
    - Dockerfile
    - package.json
    - server.js
    - routes
    - db
  /frontend
    - Dockerfile
    - package.json
    - src/
  - docker-compose.yml
  - README.md
```


### Create a network for the docker containers

`docker network create demo`

### Build the client 

```sh
cd mern/frontend
docker build -t mern-frontend .
```

### Run the client

`docker run --name=frontend --network=demo -d -p 5173:5173 mern-frontend`

### Verify the client is running

Open your browser and type `http://localhost:5173`

### Run the mongodb container

`docker run --network=demo --name mongodb -d -p 27017:27017 -v data:/data/db mongodb:latest`

### Build the server

```sh
cd mern/backend
docker build -t mern-backend .
```

### Run the server

`docker run --name=backend --network=demo -d -p 5050:5050 mern-backend`

## Using Docker Compose

`docker compose up -d`

## Access the Application

```sh
Frontend: Open your browser and go to http://localhost:5173.
Backend API: Access it at http://localhost:5050.
```

## Stopping the Containers
- To stop and remove the containers, use:

```sh
docker-compose down
docker-compose down -v (To remove volumes)
```

