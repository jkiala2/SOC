# TheHive and Cortex Setup with Docker Compose

This guide will walk you through setting up **TheHive** and **Cortex** using Docker Compose. These two services are commonly used for incident response and analysis. **TheHive** provides a security incident response platform, while **Cortex** offers various analyzers to assist in investigations.

## Prerequisites

- Docker installed on your machine
- Docker Compose installed on your machine

## Getting Started

Follow these steps to deploy **TheHive** and **Cortex** with Docker Compose.

### 1. Clone the Repository (if needed)

git clone https://github.com/jkiala2/SOC.git

cd Thehive-Cortex


### 2. Modify Configuration

Before proceeding with the installation, ensure you modify the following configurations in your `docker-compose.yml` file:

- **SECRET_KEY** for **TheHive** (`thehive` service).
- **CORTEX_SECRET_KEY** for **Cortex** (`cortex` service).

These secret keys must be replaced with your own strong secret keys for security purposes.

### 3. Start the Services

Once you have your `docker-compose.yml` configured, navigate to the directory containing the `docker-compose.yml` file and run the following command to start the containers:

docker-compose up -d

### 4. Check if Services Are Running
To verify that all services are running correctly, use the following command:

docker ps -a
This should display the running containers for TheHive, Cortex, Cassandra, Elasticsearch, and MongoDB.

### 5. Access TheHive
After the containers are up and running, you can access TheHive through your browser.

URL: http://yourIP:9001

Default credentials:

Username: admin

Password: admin
Once logged in, you can start managing incidents and investigations.

### 6. Access Cortex
You can access Cortex through your browser at the following URL:

URL: http://yourIP:9002

### 7. Stopping the Services
To stop the running services, use the following command:

docker-compose down
This will stop and remove the containers, but the data will remain on your system.

### 8. Restarting the Services
To restart the services, you can run the following command:

docker-compose up -d

# Troubleshooting

## Containers Not Starting:

Ensure that Docker is running properly.
Check the logs using docker-compose logs for more detailed error messages.

## Port Conflicts:

If another service is using ports 9001 or 9002, you can modify the port mappings in the docker-compose.yml file.
Customization
TheHive and Cortex are highly customizable. You can modify environment variables and configuration settings as needed to fit your requirements.

## Storage: You may want to configure persistent storage for Cassandra and Elasticsearch to retain data across container restarts. This can be done by mounting volumes in the docker-compose.yml.

# Useful Links
TheHive Documentation: https://thehive-project.org/docs/
Cortex Documentation: https://thehive-project.org/cortex/
Docker: https://www.docker.com/
Docker Compose: https://docs.docker.com/compose/
