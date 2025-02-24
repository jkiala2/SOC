# Suricata Installation and Integration with Wazuh

This guide provides the steps to install Suricata, configure it with custom rules, and integrate it into Wazuh for monitoring network traffic and detecting threats.

## Prerequisites

- A server running Ubuntu or a similar Debian-based distribution.
- `sudo` privileges.
- Wazuh already installed and configured on the server.

## Step 1: Install Suricata

### Add Suricata Repository and Install the Package

First, add the Suricata stable repository and install the software package.

`sudo add-apt-repository ppa:oisf/suricata-stable`

`sudo apt-get update`

`sudo apt-get install suricata -y`

This will install Suricata and all its dependencies.

## Step 2: Download and Install Suricata Rules
Suricata uses a rule-based system to detect various types of attacks. You can download the Emerging Threats (ET) rules to enable Suricata to detect the latest threats.

Download Emerging Threats Rules

`cd /tmp/ && curl -LO https://rules.emergingthreats.net/open/suricata-6.0.8/emerging.rules.tar.gz`

Extract and Install the Rules

Now, extract the downloaded rules and move them to the proper directory for Suricata to use.

`mkdir -p /etc/suricata/rules/`

`sudo tar -xvzf emerging.rules.tar.gz && sudo mv rules/*.rules /etc/suricata/rules/`

Set Proper Permissions

Ensure the rules are readable only by Suricata to maintain security.

`sudo chmod 640 /etc/suricata/rules/*.rules`

### Step 3: Configure Suricata

Edit the Suricata configuration file to set up important variables like HOME_NET, EXTERNAL_NET, and the rule file locations.

`Edit suricata.yaml`

`sudo nano /etc/suricata/suricata.yaml`

Modify the following parameters according to your network setup:

HOME_NET: Set this to your local network's IP range (e.g., 192.168.1.0/24).

EXTERNAL_NET: Set this to "any" to allow Suricata to monitor all external traffic.

Add rule files configuration:

rule-files: 

  - "*.rules"
  - "/etc/suricata/rules/*.rules"
    
### Configure High-Speed Capture (Optional)
If you're using a high-speed network interface, configure Suricata to capture packets efficiently using af-packet.

af-packet:
  - interface: enp0s8  (Change to your network interface name)

Enable Stats

Ensure Suricata is configured to gather and send statistics:

stats:
  enabled: yes

## Step 4: Restart Suricata
After making the changes, restart Suricata to apply the new configurations.

sudo systemctl restart suricata

# Step 5: Integrate Suricata with Wazuh
To send Suricata logs to Wazuh for analysis, configure the ossec.conf file.

Edit Wazuh Agent Configuration

Edit the Wazuh agent's ossec.conf file to include Suricata's log file.

sudo nano /var/ossec/etc/ossec.conf

Add the following <localfile> entry:

<ossec_config>
  
  <localfile>
    
    <log_format>json</log_format>
    
    <location>/var/log/suricata/eve.json</location>
    
  </localfile>
  
</ossec_config>

Ensure the path to Suricata's eve.json log file is correct. This log file is where Suricata outputs event and alert data in JSON format.

# Step 6: Restart Wazuh Agent
Finally, restart the Wazuh agent to apply the changes.

sudo systemctl restart wazuh-agent

# Step 7: Verify the Integration
Check Suricata logs (/var/log/suricata/eve.json) to ensure Suricata is running and generating events.

Verify that Wazuh is receiving Suricata alerts by checking the Wazuh dashboard or log data.
