# Aliasgar Husain - 41161727 
# CST8919_lab3


# Grafana Installation & Azure Monitor Integration - Lab Report

<img width="1483" alt="SCR-20250401-tfxv" src="https://github.com/user-attachments/assets/a6c636a9-ab80-45b2-baec-66234eccc113" />

## Steps Taken

### 1. Ubuntu Server Preparation
- Started by updating the package list and upgrading the system using `sudo apt-get update && sudo apt-get upgrade` to ensure the server was up to date.

### 2. Grafana Installation
- Installed dependencies like `apt-transport-https`, `software-properties-common`, and `wget`.
- Added Grafana’s APT key and repository to the sources list securely using GPG and configured the `grafana.gpg` keyring.
- Installed Grafana using `sudo apt-get install grafana` and confirmed installation.
- Enabled and started the Grafana service with `systemctl` and verified that Grafana was running.
- Allowed access to port 3000 to reach the Grafana web UI in the browser.

### 3. Connecting Grafana to Azure Monitor
- Enabled Managed Identity on the Grafana VM from the Azure Portal.
- Assigned the **Monitoring Reader** role to the VM’s identity for Azure Monitor and **Reader** role on the subscription.
- Edited the `/etc/grafana/grafana.ini` file to enable managed identity authentication.
- Restarted the Grafana service to apply the changes.

### 4. Grafana Configuration and Dashboard Creation
- Accessed the Grafana web UI using the server's public IP and default credentials (admin/admin).
- Navigated to **Configuration > Data Sources**, added **Azure Monitor** as a data source, and authenticated using Managed Identity.
- Created a new dashboard and added a panel that visualized system performance metrics like CPU usage, memory usage, and disk I/O.
- Customized the panel with colors and thresholds and saved the dashboard.

## Issues Encountered

- Initially, I had trouble connecting to the Grafana web interface. It was resolved by checking firewall rules and ensuring port 3000 was open in the network security group.
- The Managed Identity authentication failed the first time. The problem was caused by forgetting to assign the **Monitoring Reader** role in Azure, which I corrected in the IAM section of the Azure portal.
- Another issue was the data source test failing in Grafana. This was resolved by verifying the `grafana.ini` file changes and making sure the file had no syntax errors before restarting the service.

---
