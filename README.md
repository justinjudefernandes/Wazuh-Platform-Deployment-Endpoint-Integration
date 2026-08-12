# Wazuh SIEM XDR Deployment and Endpoint Integration

## 🎯 Objective:
Build and configure a Wazuh-based security monitoring environment to understand its SIEM/XDR architecture and establish centralized visibility across Windows and Linux systems. The objective was to deploy the Wazuh platform, onboard endpoints, and integrate Sysmon to enhance security telemetry and endpoint monitoring.

## 📊 Project Overview:
The implementation covered the complete setup of the Wazuh security monitoring platform, including the Wazuh Server, Indexer, Dashboard, and endpoint Agents. Windows 10 and Ubuntu 24.04 endpoints were onboarded, with Sysmon integrated to collect detailed endpoint activity and centralized telemetry for monitoring and investigation.

Key areas covered:
- Wazuh Server, Indexer and Dashboard deployment
- Windows and Linux endpoint onboarding
- Wazuh Agent configuration
- Windows Sysmon integration
- Linux Sysmon integration
- Centralized security telemetry collection
- Wazuh archive and index configuration
- Security event monitoring and investigation
- SIEM/XDR capabilities and architecture
- FIM and Active Response fundamentals
- Integration capabilities with Splunk, OpenSearch, VirusTotal, YARA and Suricata

## 🖥️ Lab Setup:
<img width="1536" height="1024" alt="Lab Setup" src="https://github.com/user-attachments/assets/9044cc9f-6b50-4366-94a5-ed68fdccafed" />
<img width="974" height="355" alt="image" src="https://github.com/user-attachments/assets/158dae1d-297f-4f66-a3c1-0cfd1481b748" />
<img width="974" height="355" alt="image" src="https://github.com/user-attachments/assets/cfe4a396-3ba3-430a-a280-ab46c1f694d0" />

## 🧰 Tools Used:
- VMware Workstation Pro
- Ubuntu Server 24.04.4 – Wazuh Server
- Windows 10 – Monitored Endpoint
- Ubuntu 24.04.4 – Monitored Endpoint
- Wazuh Agent
- Wazuh Server
- Wazuh Indexer
- Wazuh Dashboard
- Microsoft Sysmon for Windows
- Sysmon for Linux

## 🛡️ Skill Developed:
- Wazuh SIEM/XDR architecture
- Wazuh platform deployment and configuration
- Windows and Linux endpoint onboarding
- Security telemetry collection
- Windows Event Log monitoring
- Linux log monitoring
- Sysmon deployment and configuration
- Endpoint visibility and monitoring
- File Integrity Monitoring fundamentals
- Active Response fundamentals
- Log indexing and searching
- Security dashboard configuration
- Security event investigation

## 📁 Key Deliverables:
- Deployed Wazuh Server, Indexer and Dashboard
- Configured Wazuh archive collection
- Created and configured the wazuh-archives index
- Successfully onboarded Windows 10 endpoint
- Successfully onboarded Ubuntu Linux endpoint
- Installed and configured Sysmon for Windows
- Installed and configured Sysmon for Linux
- Integrated Windows Sysmon events with Wazuh
- Integrated Linux Sysmon events with Wazuh
- Verified centralized telemetry collection through Wazuh Discover
- Established centralized endpoint security visibility

## 🔍 Steps Performed:

### 1. Infrastructure Preparation
- Installed VMware Workstation Pro.
- Deployed Ubuntu Server 24.04.4.
- Created Windows 10 and Ubuntu endpoint virtual machines.
- Installed VMware Tools.
- Created VM snapshots for recovery and rollback.

### 2. Wazuh Platform Deployment
- Installed Wazuh using the official installation script:
```KQL Query:
curl -sO https://packages.wazuh.com/4.14/wazuh-install.sh && sudo bash ./wazuh-install.sh -a
```
- Configured and accessed the Wazuh Dashboard following the successful installation.

### 3. Wazuh Credential Management
- Located the generated Wazuh installation files.
- Extracted wazuh-install-files.tar.
- Accessed wazuh-passwords.txt.
- Verified the generated administrative credentials.

### 4. Wazuh Archive Configuration
- Enabled full telemetry collection by modifying:
```KQL Query:
/var/ossec/etc/ossec.conf
```
- Configured:
```KQL Query:
<logall>yes</logall>
<logall_json>yes</logall_json>
```
- Restarted the Wazuh Manager service.
- Configured Filebeat archives and enabled the archive collection functionality.

### 5. Wazuh Archives Index
- Created the wazuh-archives index pattern through the Wazuh Dashboard.
- Configured the timestamp field as the time field and verified archived events.
- Successfully confirmed that endpoint telemetry was being indexed and searchable.

### 6. Windows Endpoint Integration
- Deployed the Wazuh Agent on Windows 10.
- Configured the Wazuh Server IP and endpoint name.
- Installed the agent using the generated PowerShell command.
- Started the Wazuh Agent service.
- Verified successful endpoint registration in the Wazuh Dashboard.

### 7. Linux Endpoint Integration
- Deployed the Wazuh Agent on Ubuntu 24.04.4.
- Configured the Wazuh Server IP and endpoint name.
- Installed the DEB AMD64 agent package.
- Started the Wazuh Agent service.
- Verified successful Linux endpoint registration.

### 8. Sysmon for Windows
- Downloaded Microsoft Sysmon.
- Obtained and configured a Sysmon configuration file.
- Installed Sysmon using an elevated PowerShell session.
- Verified the Sysmon service was running.
- Identified the Windows Sysmon event channel through Event Viewer.

### 9. Wazuh Sysmon Integration
- Modified the Windows Wazuh Agent configuration:
```KQL Query:
C:\Program Files (x86)\ossec-agent\ossec.conf
```
- Configured the agent to collect:
```KQL Query:
Microsoft-Windows-Sysmon/Operational
```
- Restarted the Wazuh Agent and verified that Sysmon telemetry was successfully forwarded to Wazuh.

### 10. Sysmon for Linux
- Installed Sysmon for Linux.
- Downloaded the collect-all.xml configuration.
- Configured Sysmon to use the supplied configuration.
- Verified Sysmon events were being written to /var/log/syslog.
- Confirmed Linux Sysmon telemetry was successfully received and displayed in Wazuh.
