# Docker Setup for MongoDB, Elasticsearch, and Graylog

This repository provides a Docker setup to run MongoDB, Elasticsearch, and Graylog in a containerized environment using `docker-compose`. This setup is ideal for logging and monitoring systems.

## Prerequisites

Before you begin, ensure that you have the following installed:

- Docker: [Install Docker](https://docs.docker.com/get-docker/)
- Docker Compose: [Install Docker Compose](https://docs.docker.com/compose/install/)

## Installation

1. Clone this repository to your local machine:
   ```bash
   git clone https://github.com/jkiala2/SOC.git.git
   cd Graylog

### Build and start the containers using Docker Compose:

docker-compose up -d

This will start the following services:

- MongoDB: Database for Graylog.
- Elasticsearch: Search and indexing service for Graylog.
- Graylog: Centralized logging interface.

To check if the services are running correctly, use the following command:

- docker ps 

## Accessing the Services
### Graylog UI: 
Open your browser and navigate to http://yourIP:9008 to access the Graylog web interface.

Default credentials:

- Username: admin

- Password: The value of GRAYLOG_ROOT_PASSWORD_SHA2 (SHA256 hash of "password").

Elasticsearch: Accessible at http://yourIP:9202.

## Troubleshooting
If the containers are not starting, check the logs for each service:

- docker-compose logs <service-name>

To stop the containers, run:

- docker-compose down

If you need to rebuild the images (after making changes), use:

- docker-compose up --build -d

### Volumes
The following Docker volumes are used to persist data across container restarts:

mongo_data: MongoDB data.

es_data: Elasticsearch data.

graylog_data: Graylog data.
