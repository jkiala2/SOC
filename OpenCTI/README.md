# OpenCTI: Installation and Usage of Connectors

## 1. Installation of OpenCTI

OpenCTI relies on several main components: a web user interface, a backend (API), and a database. It is recommended to use Docker to simplify the installation process.

## Steps to install OpenCTI using Docker:

Clone the OpenCTI repository:

git clone https://github.com/jkiala2/SOC.git

cd OpenCTI

Launch the services with Docker Compose: OpenCTI comes with a **docker-compose.yml** file to manage the necessary services. 

Simply run the following command:

docker-compose up -d

Access the web interface: Once the services are running, you can access the OpenCTI user interface at the following address: **http://localhost:8080** (by default).

# 2. Connector Configuration

OpenCTI allows the integration of several connectors to retrieve Threat Intelligence data from different sources. These connectors enable the platform to be fed with real-time threat information.

git clone https://github.com/OpenCTI-Platform/connectors.git


