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
<img width="1000" height="600" alt="Lab Setup" src="https://github.com/user-attachments/assets/9044cc9f-6b50-4366-94a5-ed68fdccafed" />

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

📌 Refer to the below screenshot:

<img width="975" height="582" alt="image" src="https://github.com/user-attachments/assets/2467c5e9-c3d4-41e0-96d7-5c4f93e9e131" />

### 2. Wazuh Platform Deployment
- Installed Wazuh using the official installation script:
```KQL Query:
curl -sO https://packages.wazuh.com/4.14/wazuh-install.sh && sudo bash ./wazuh-install.sh -a
```
- Configured and accessed the Wazuh Dashboard following the successful installation.

📌 Refer to the below screenshots: (from left to right)

<img width="500" height="230" alt="image" src="https://github.com/user-attachments/assets/21610abb-e8a7-466e-87eb-2be112bbffd9" />
<img width="500" height="230" alt="image" src="https://github.com/user-attachments/assets/25aa62fb-588a-4732-b2a6-ba81b96b8f0c" />
<img width="330" height="230" alt="image" src="https://github.com/user-attachments/assets/c74b30cb-0683-4856-a29a-46082a890462" />
<img width="330" height="230" alt="image" src="https://github.com/user-attachments/assets/ae6ba271-a308-4f2f-ab97-dae35e9c82e5" />
<img width="330" height="230" alt="image" src="https://github.com/user-attachments/assets/7f2f9262-0aaa-49e3-9657-6e3df1ec864e" />


### 3. Wazuh Credential Management
- Located the generated Wazuh installation files.
- Extracted wazuh-install-files.tar.
- Accessed wazuh-passwords.txt.
- Verified the generated administrative credentials.

📌 Refer to the below screenshots:

<img width="975" height="578" alt="image" src="https://github.com/user-attachments/assets/e5c540e6-99bf-40c1-a2d6-e957be6b6575" />

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

📌 Refer to the below screenshots:

<img width="330" height="230" alt="image" src="https://github.com/user-attachments/assets/ccd61148-99e4-4394-80e8-a9992ddfedf2" />
<img width="330" height="230" alt="image" src="https://github.com/user-attachments/assets/c9dffe55-fb17-4422-bbe7-55a1e30f41ad" />
<img width="330" height="230" alt="image" src="https://github.com/user-attachments/assets/fd4ab041-852f-41b9-930e-3170e18bb3ed" />
<img width="330" height="230" alt="image" src="https://github.com/user-attachments/assets/95be5bf2-9f0c-4ef9-9bba-2fc2bdb2accc" />
<img width="330" height="230" alt="image" src="https://github.com/user-attachments/assets/c95fc332-c320-48b6-8269-db9399f69d9d" />
<img width="330" height="230" alt="image" src="https://github.com/user-attachments/assets/f8bd5dac-8f8c-4461-88c9-e79d53f5e83f" />
<img width="500" height="230" alt="image" src="https://github.com/user-attachments/assets/966d1e05-2b52-4071-8b55-a557eaa0b229" />
<img width="500" height="230" alt="image" src="https://github.com/user-attachments/assets/d11086df-c55c-4e46-9518-6c6484e77eaa" />


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
