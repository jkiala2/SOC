# TheHive and Cortex Setup with Docker Compose

This guide will walk you through setting up **TheHive** and **Cortex** using Docker Compose. These two services are commonly used for incident response and analysis. **TheHive** provides a security incident response platform, while **Cortex** offers various analyzers to assist in investigations.

## Prerequisites

- Docker installed on your machine
- Docker Compose installed on your machine

## Getting Started

Follow these steps to deploy **TheHive** and **Cortex** with Docker Compose.

### 1. Clone the Repository (if needed)




### 2. Modify Configuration

Before proceeding with the installation, ensure you modify the following configurations in your `docker-compose.yml` file:

- **SECRET_KEY** for **TheHive** (`thehive` service).
- **CORTEX_SECRET_KEY** for **Cortex** (`cortex` service).

These secret keys must be replaced with your own strong secret keys for security purposes.

### 3. Start the Services

Once you have your `docker-compose.yml` configured, navigate to the directory containing the `docker-compose.yml` file and run the following command to start the containers:

```bash
docker-compose up -d
