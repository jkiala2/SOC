# Wazuh Single-Node Deployment with Docker

This guide provides step-by-step instructions to deploy Wazuh in a single-node setup using Docker.

## 📌 Prerequisites

Docker and Docker Compose installed on your system.

Git installed to clone the repository.

(Optional) Your own SSL certificates for secure communication.

## 🚀 Installation Steps

1️⃣ Clone the Repository

Clone the official Wazuh Docker repository:

git clone https://github.com/jkiala2/SOC.git

cd wazuh

## 2️⃣ Generate SSL Certificates

Wazuh requires SSL certificates to secure communication between its components.

### Option 1: Generate Self-Signed Certificates (Recommended)

Run the following command to create the necessary certificates:

docker-compose -f generate-indexer-certs.yml run --rm generator

This will generate certificates in the config/wazuh_indexer_ssl_certs/ directory.

### Option 2: Use Your Own Certificates

Copy your existing SSL certificates into config/wazuh_indexer_ssl_certs/ with the following structure:

config/wazuh_indexer_ssl_certs/

├── root-ca.pem

├── wazuh.indexer-key.pem

├── wazuh.indexer.pem

├── admin.pem

├── admin-key.pem

├── root-ca-manager.pem

├── wazuh.manager.pem

├── wazuh.manager-key.pem

├── wazuh.dashboard.pem

├── wazuh.dashboard-key.pem

## 3️⃣ Start the Wazuh Stack

After setting up the certificates, start the Wazuh stack using Docker Compose:

Run in foreground (shows logs):

docker-compose up

Run in background (detached mode):

docker-compose up -d

## 4️⃣ Access the Wazuh Dashboard

Once the deployment is complete, open your web browser and go to:

🔗 https://localhost

Default login credentials:

Username: admin

Password: SecretPassword

(For security reasons, change the default password after installation.)

## 5️⃣ Troubleshooting

If you encounter issues, check the logs:

docker-compose logs -f

Common issues:

Connection errors to Wazuh Indexer (port 9200): Normal during startup, wait for a few minutes.

SSL certificate errors: Ensure certificates are correctly placed and configured.

📜 License

This project follows the Wazuh GPLv2 License.

📖 Documentation

For more details, check the official Wazuh Docker documentation.

💡 Feel free to contribute or suggest improvements!


