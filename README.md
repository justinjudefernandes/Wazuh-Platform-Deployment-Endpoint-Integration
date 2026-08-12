# Wazuh SIEM XDR Deployment and Endpoint Integration

🎯 Objective:
Deploy and configure a Wazuh SIEM/XDR platform and establish centralized security monitoring across Windows and Linux endpoints. The project focused on understanding the Wazuh architecture, deploying the core platform, onboarding endpoints, enabling telemetry collection, and integrating Sysmon for enhanced endpoint visibility.

📊 Project Overview:
Wazuh is an open-source security platform providing SIEM and XDR capabilities, including endpoint monitoring, File Integrity Monitoring (FIM), vulnerability detection, threat detection, and automated response.

The implementation covered the deployment and configuration of:

Wazuh Server
Wazuh Indexer
Wazuh Dashboard
Wazuh Agents
Windows 10 Endpoint
Ubuntu 24.04 Endpoint
Sysmon for Windows
Sysmon for Linux

The Wazuh architecture was explored across its four primary components:

Wazuh Agent → Collects endpoint telemetry
Wazuh Server → Analyzes events and generates alerts
Wazuh Indexer → Stores and indexes security data
Wazuh Dashboard → Provides visualization and investigation capabilities

Wazuh integrations with platforms and security tools such as Splunk, OpenSearch, VirusTotal, YARA, and Suricata were also explored.

🖥️ Lab Setup:
VMware Workstation Pro
Ubuntu Server 24.04.4 – Wazuh Server
Windows 10 – Monitored Endpoint
Ubuntu 24.04.4 – Monitored Endpoint
Wazuh Agent
Wazuh Server
Wazuh Indexer
Wazuh Dashboard
Microsoft Sysmon for Windows
Sysmon for Linux

🛡️ Skill Developed:
Wazuh SIEM/XDR architecture
Wazuh platform deployment and configuration
Windows and Linux endpoint onboarding
Security telemetry collection
Windows Event Log monitoring
Linux log monitoring
Sysmon deployment and configuration
Endpoint visibility and monitoring
File Integrity Monitoring fundamentals
Active Response fundamentals
Log indexing and searching
Security dashboard configuration
Security event investigation

📁 Key Deliverables:
Deployed Wazuh Server, Indexer and Dashboard
Configured Wazuh archive collection
Created and configured the wazuh-archives index
Successfully onboarded Windows 10 endpoint
Successfully onboarded Ubuntu Linux endpoint
Installed and configured Sysmon for Windows
Installed and configured Sysmon for Linux
Integrated Windows Sysmon events with Wazuh
Integrated Linux Sysmon events with Wazuh
Verified centralized telemetry collection through Wazuh Discover
Established centralized endpoint security visibility

🔍 Steps Performed:
1. Wazuh Architecture & Security Capabilities
Reviewed the architecture and functionality of Wazuh.
Studied the roles of the Agent, Server, Indexer and Dashboard.
Reviewed Wazuh SIEM/XDR capabilities.
Explored File Integrity Monitoring and Active Response.
Reviewed integrations with external security and threat intelligence platforms.
2. Infrastructure Preparation
Installed VMware Workstation Pro.
Deployed Ubuntu Server 24.04.4.
Created Windows 10 and Ubuntu endpoint virtual machines.
Installed VMware Tools.
Created VM snapshots for recovery and rollback.
3. Wazuh Platform Deployment

Installed Wazuh using the official installation script:

curl -sO https://packages.wazuh.com/4.14/wazuh-install.sh && sudo bash ./wazuh-install.sh -a

Configured and accessed the Wazuh Dashboard following the successful installation.

4. Wazuh Credential Management
Located the generated Wazuh installation files.
Extracted wazuh-install-files.tar.
Accessed wazuh-passwords.txt.
Verified the generated administrative credentials.
5. Wazuh Archive Configuration

Enabled full telemetry collection by modifying:

/var/ossec/etc/ossec.conf

Configured:

<logall>yes</logall>
<logall_json>yes</logall_json>

Restarted the Wazuh Manager service.

Configured Filebeat archives and enabled the archive collection functionality.

6. Wazuh Archives Index

Created the wazuh-archives index pattern through the Wazuh Dashboard.

Configured the timestamp field as the time field and verified archived events through:

Explore → Discover

Successfully confirmed that endpoint telemetry was being indexed and searchable.

7. Windows Endpoint Integration
Deployed the Wazuh Agent on Windows 10.
Configured the Wazuh Server IP and endpoint name.
Installed the agent using the generated PowerShell command.
Started the Wazuh Agent service.
Verified successful endpoint registration in the Wazuh Dashboard.
8. Linux Endpoint Integration
Deployed the Wazuh Agent on Ubuntu 24.04.4.
Configured the Wazuh Server IP and endpoint name.
Installed the DEB AMD64 agent package.
Started the Wazuh Agent service.
Verified successful Linux endpoint registration.
9. Sysmon for Windows
Downloaded Microsoft Sysmon.
Obtained and configured a Sysmon configuration file.
Installed Sysmon using an elevated PowerShell session.
Verified the Sysmon service was running.
Identified the Windows Sysmon event channel through Event Viewer.
10. Wazuh Sysmon Integration

Modified the Windows Wazuh Agent configuration:

C:\Program Files (x86)\ossec-agent\ossec.conf

Configured the agent to collect:

Microsoft-Windows-Sysmon/Operational

Restarted the Wazuh Agent and verified that Sysmon telemetry was successfully forwarded to Wazuh.

11. Sysmon for Linux
Installed Sysmon for Linux.
Downloaded the collect-all.xml configuration.
Configured Sysmon to use the supplied configuration.
Verified Sysmon events were being written to /var/log/syslog.
Confirmed Linux Sysmon telemetry was successfully received and displayed in Wazuh.
