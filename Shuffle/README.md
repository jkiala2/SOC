# Shuffle SOAR Installation Guide

## Prerequisites

Before you begin the installation of Shuffle SOAR, make sure you have the following prerequisites:

- **Docker**: to run the Shuffle SOAR containers.
- **Docker Compose**: to help manage multi-container services.

### Installing Docker and Docker Compose

On a Linux machine (Debian/Ubuntu), follow these steps:

1. **Update the packages**:
   
sudo apt update
   
### Install Docker and Docker Compose:

sudo apt install docker.io docker-compose

Verify the installation of Docker and Docker Compose:

docker --version

docker-compose --version

Ensure Docker and Docker Compose are installed correctly.

# Step 1: Download Shuffle SOAR

Clone the official Shuffle SOAR repository from GitHub:

git clone https://github.com/Shuffle/Shuffle.git

cd Shuffle

If you prefer to download a ZIP archive, you can do so from this GitHub link.

# Step 2 : Start the Services
To download the necessary images and start the services in the background, run:

- docker-compose up -d

This command will download the required images and launch the containers in detached mode.

Verify the running containers

After running docker-compose up -d, you can check that the containers are running with:

docker ps

You should see several containers running, including shuffle-server and shuffle-db.

# Step 4: Access Shuffle SOAR Web Interface
Once the services are started, you can access the Shuffle SOAR web interface at the following address:

http://<YOUR_SERVER_IP>:3001

Replace <YOUR_SERVER_IP> with the IP address of your machine. For example, if you are using a local machine, you can access it via:

# Step 5: Initial Setup
When you first log in, you will be prompted to set up an administrator user. Follow the on-screen instructions to complete the setup and begin using Shuffle SOAR.

