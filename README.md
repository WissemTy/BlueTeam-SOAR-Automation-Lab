# Automated SOC with XDR/SOAR Stack (Home Lab)
![Category](https://img.shields.io/badge/Field-Cybersecurity-blue)
![Role](https://img.shields.io/badge/Role-Blue%20Team-blue)
![Status](https://img.shields.io/badge/Status-Work%20In%20Progress-orange)
<p align="center">
  <img src="diagrams/network-topology-transparent.png" alt="Lab Topology">
</p>

## 📌 Project Overview
This project focuses on building a functional Security Operations Center (SOC) to simulate real-world attack and defense scenarios. It demonstrates the integration of a SIEM for threat detection and a SOAR platform for automated incident response.

**Current Status:** 🚧 Work In Progress (Implementing SOAR workflows) !


## 🗺️ Network Addressing Plan
| Hostname | Role | OS / Distribution | Management (NAT) | Internal (SOC-NET) |
| :--- | :--- | :--- | :--- | :--- |
| **SOC-WAZUH-SRV-01** | Wazuh Manager | **Ubuntu Live Server 24.04** | SSH: 2222 | **10.0.5.2** |
| **WIN-SRV-01** | Windows Target | **Windows Server 2022** | RDP: 3389 | **10.0.5.10** |
| **PENTEST-NODE** | Red Team Node | **Kali Linux (64-bit)** | SSH: 2223 | **10.0.5.50** |



## 🛠️ Implementation Details
* **SIEM/XDR:** Wazuh installation for centralized log management and endpoint monitoring.
* **Storage:** Configured with **LVM (Logical Volume Management)** on the Ubuntu server to allow flexible disk resizing for log databases.
* **Telemetry:** Windows event collection via Wazuh Agent and **Sysmon**.
* **Automation (In Progress):** Integrating **Shuffle (SOAR)** for alert enrichment via APIs (VirusTotal) and automated response.

## ⚔️ Planned Scenarios
1. **Detection:** Identifying brute-force and credential dumping on Windows Server.
2. **Analysis:** Correlating logs to identify the source of the attack (PENTEST-NODE).
3. **Response:** Using Wazuh **Active Response** to block malicious IPs at the firewall level.

## 🧰 Tech Stack
* **Security:** Wazuh, Sysmon, Shuffle (SOAR).
* **OS:** Ubuntu Server, Windows Server 2022, Kali Linux.
* **Hypervisor:** VirtualBox.