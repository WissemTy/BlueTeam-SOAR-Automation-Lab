
# 🛡️ BlueTeam-SOAR-Automation-Lab

![Category](https://img.shields.io/badge/Field-Cybersecurity-blue)
![Role](https://img.shields.io/badge/Role-Blue%20Team-blue)
## # Work in Progress (NOT FINISHED)

## 🚀 Overview

This project is an evolution of my [Network-Security-Lab](https://github.com/WissemTy/Network-Security-Lab), shifting the focus from network segmentation to **Advanced Detection Engineering** and **Automated Incident Response (SOAR)**.

<p align="center">
  <img src="diagrams/network-topology-transparent.png" alt="Topology">
</p>

The goal is to simulate a modern Security Operations Center (SOC) capable of detecting threats on a **Windows Server** environment and reacting in real-time to neutralize attacks without human intervention.

### Key Objectives:
* **MTTR Reduction**: Automating the response to reduce the Mean Time To Respond.
* **Telemetery Analysis**: Ingesting Windows EventChannels and Sysmon logs.
* **Threat Intelligence**: Enriching alerts via external APIs (VirusTotal).
* **ChatOps Integration**: Real-time alerting for security analysts via Slack.


## 🏗️ Architecture & Workflow

The lab is built on a 3-VM architecture (32GB RAM dedicated) to ensure high performance and realistic data ingestion.

### 🌐 Technical Topology
* **Attacker (Kali Linux)**: Simulating real-world threats (Brute Force, Reverse Shells).
* **Target (Windows Server)**: Monitored via a **Wazuh Agent** and **Sysmon**.
* **Security Stack (Ubuntu Server)**:
    * **SIEM/XDR**: Wazuh Manager (Log analysis & Alerting).
    * **SOAR**: Shuffle (Automation & Orchestration).
    * **Docker**: Orchestrating the security stack.

### 🔄 The Detection & Response Loop
1. **Detection**: The Wazuh Agent pushes security logs (Sysmon/EventChannel) to the Manager.
2. **Trigger**: Wazuh triggers a **JSON Webhook** to Shuffle upon detecting a critical alert.
3. **Enrichment**: Shuffle queries the **VirusTotal API** to check IP/Hash reputation.
4. **Notification**: An incident report is sent to a **Slack** channel (ChatOps).
5. **Active Response**: Shuffle instructs Wazuh to **Isolate the Host** or **Block the IP** automatically.


## ⚔️ Implemented Attack Scenarios

| Scenario | Attack Vector | Detection Rule | Automated Action |
| :--- | :--- | :--- | :--- |
| **Brute Force** | RDP / SSH | Multiple Failed Logins | IP Blacklisted (Firewall) |
| **Malware Execution** | Reverse Shell (Python) | Sysmon Process Creation | Host Isolation |
| **Data Exfiltration** | DNS Tunneling | Unusual DNS Traffic | Alert + Admin Notification |


## 🛠️ Technologies Used

* **SIEM**: [Wazuh](https://wazuh.com/)
* **SOAR**: [Shuffle](https://shuffler.io/)
* **Infrastructure**: Ubuntu Server, Windows Server 2022.
* **Tools**: Docker, Docker-Compose, Sysmon, VirusTotal API.
* **Communication**: Slack Webhooks.


## 📁 Project Structure

* `/configs`: Docker-Compose files and Wazuh custom rules.
* `/docs`: Technical diagrams and the full PDF Project Report.
* `/scripts`: Custom Python/Bash scripts for active response.


## 📄 Full Project Report

For a deep dive into the technical configurations, JSON mappings, and detailed audit results, read the full documentation here:
👉 **[View Full PDF Report](./docs/SOC_Lab_Report.pdf)**
