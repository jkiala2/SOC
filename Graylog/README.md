# Docker Setup for MongoDB, Elasticsearch, and Graylog

This repository provides a Docker setup to run MongoDB, Elasticsearch, and Graylog in a containerized environment using `docker-compose`. This setup is ideal for logging and monitoring systems.

## Prerequisites

Before you begin, ensure that you have the following installed:

- Docker: [Install Docker](https://docs.docker.com/get-docker/)
- Docker Compose: [Install Docker Compose](https://docs.docker.com/compose/install/)

## Installation

1. Clone this repository to your local machine:
   ```bash
   git clone https://github.com/your-username/your-repository.git
   cd your-repository
Build and start the containers using Docker Compose:

bash
Copier
Modifier
docker-compose up -d
This will start the following services:

MongoDB: Database for Graylog.
Elasticsearch: Search and indexing service for Graylog.
Graylog: Centralized logging interface.
To check if the services are running correctly, use the following command:

bash
Copier
Modifier
docker-compose ps
Configuration
The services are configured with the following environment variables:

MongoDB:
Image: mongo:6.0
Container Name: mongodb
Volumes: Data stored in mongo_data.
Elasticsearch:
Image: docker.elastic.co/elasticsearch/elasticsearch:7.10.2
Container Name: elasticsearch_graylog
Ports: Exposed on port 9202.
Environment Variables:
discovery.type=single-node: Single-node configuration.
ES_JAVA_OPTS=-Xms512m -Xmx512m: Memory settings for Elasticsearch.
Volumes: Data stored in es_data.
Graylog:
Image: graylog/graylog:5.0
Container Name: graylog1
Depends on: MongoDB and Elasticsearch.
Ports:
9008:9000: Access Graylog UI.
1514:1514 & 1514:1514/udp: Syslog input.
12201:12201 & 12201:12201/udp: GELF input.
Environment Variables:
GRAYLOG_PASSWORD_SECRET: Secret used for password encryption.
GRAYLOG_ROOT_PASSWORD_SHA2: SHA256 hash of the root password.
GRAYLOG_HTTP_EXTERNAL_URI: External URI for Graylog.
Accessing the Services
Graylog UI: Open your browser and navigate to http://localhost:9008 to access the Graylog web interface.

Default credentials:
Username: admin
Password: The value of GRAYLOG_ROOT_PASSWORD_SHA2 (SHA256 hash of "password").
Elasticsearch: Accessible at http://localhost:9202.

Troubleshooting
If the containers are not starting, check the logs for each service:

bash
Copier
Modifier
docker-compose logs <service-name>
To stop the containers, run:

bash
Copier
Modifier
docker-compose down
If you need to rebuild the images (after making changes), use:

bash
Copier
Modifier
docker-compose up --build -d
Volumes
The following Docker volumes are used to persist data across container restarts:

mongo_data: MongoDB data.
es_data: Elasticsearch data.
graylog_data: Graylog data.
