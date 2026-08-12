# Wazuh Platform Deployment & Endpoint Integration

## 🎯 Objective:
Deploy and configure the Wazuh security monitoring platform to establish centralized security visibility across Windows and Linux endpoints. The objective was to understand the Wazuh SIEM architecture, successfully deploy the Wazuh platform, integrate endpoints, and configure Sysmon to enhance endpoint telemetry, event collection, and security monitoring.

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
<img width="785" height="450" alt="Lab Setup" src="https://github.com/user-attachments/assets/9044cc9f-6b50-4366-94a5-ed68fdccafed" />

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

<img width="785" height="450" alt="image" src="https://github.com/user-attachments/assets/2467c5e9-c3d4-41e0-96d7-5c4f93e9e131" />

### 2. Wazuh Platform Deployment
- Installed Wazuh using the official installation script:
```KQL Query:
curl -sO https://packages.wazuh.com/4.14/wazuh-install.sh && sudo bash ./wazuh-install.sh -a
```
- Configured and accessed the Wazuh Dashboard following the successful installation.

📌 Refer to the below screenshots: (left to right)

<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/21610abb-e8a7-466e-87eb-2be112bbffd9" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/25aa62fb-588a-4732-b2a6-ba81b96b8f0c" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/c74b30cb-0683-4856-a29a-46082a890462" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/ae6ba271-a308-4f2f-ab97-dae35e9c82e5" />
<img width="785" height="230" alt="image" src="https://github.com/user-attachments/assets/7f2f9262-0aaa-49e3-9657-6e3df1ec864e" />


### 3. Wazuh Credential Management
- Located the generated Wazuh installation files.
- Extracted wazuh-install-files.tar.
- Accessed wazuh-passwords.txt.
- Verified the generated administrative credentials.

📌 Refer to the below screenshot:

<img width="785" height="450" alt="image" src="https://github.com/user-attachments/assets/e5c540e6-99bf-40c1-a2d6-e957be6b6575" />

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

📌 Refer to the below screenshots: (left to right)

<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/ccd61148-99e4-4394-80e8-a9992ddfedf2" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/c9dffe55-fb17-4422-bbe7-55a1e30f41ad" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/fd4ab041-852f-41b9-930e-3170e18bb3ed" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/95be5bf2-9f0c-4ef9-9bba-2fc2bdb2accc" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/c95fc332-c320-48b6-8269-db9399f69d9d" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/f8bd5dac-8f8c-4461-88c9-e79d53f5e83f" />
<img width="500" height="230" alt="image" src="https://github.com/user-attachments/assets/966d1e05-2b52-4071-8b55-a557eaa0b229" />
<img width="500" height="230" alt="image" src="https://github.com/user-attachments/assets/d11086df-c55c-4e46-9518-6c6484e77eaa" />

### 5. Wazuh Archives Index
- Created the wazuh-archives index pattern through the Wazuh Dashboard.
- Configured the timestamp field as the time field and verified archived events.
- Successfully confirmed that endpoint telemetry was being indexed and searchable.

📌 Refer to the below screenshots: (left to right)

<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/f9209f3a-fbd8-4693-a325-0c41d00cc340" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/3c343f46-54a4-4c6b-adbd-26fe88fb7bf3" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/6d660003-7f3c-4358-8604-53dba1e46843" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/0ff8e4cf-c070-4d78-9bd2-3c15b3eee384" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/c654b9ed-e293-41e0-b11a-48d55b058bc4" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/7e724d15-64bd-4a84-a21b-a6e4320b7bf2" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/769c7ccf-bbe9-415a-afbd-03ecf8a43258" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/a297f1ba-ac9c-4280-b8f1-25cc2b5e4985" />

### 6. Windows Endpoint Integration
- Deployed the Wazuh Agent on Windows 10.
- Configured the Wazuh Server IP and endpoint name.
- Installed the agent using the generated PowerShell command.
- Started the Wazuh Agent service.
- Verified successful endpoint registration in the Wazuh Dashboard.

📌 Refer to the below screenshots: (left to right)

<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/0332bfc1-b1cc-40fc-80eb-bc0d1cfbf6b3" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/9cbbc654-8bb5-4902-94cb-72e42e3e473a" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/a0db8c9b-8bff-4c30-85a0-63b5a167c793" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/20eedef3-f553-4a2e-8cb6-2e1f5425d7d2" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/31b48a42-8e18-4895-913f-6871b3b5b3ef" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/aba4d42f-37ea-45a5-862b-120bacf6e678" />


### 7. Linux Endpoint Integration
- Deployed the Wazuh Agent on Ubuntu 24.04.4.
- Configured the Wazuh Server IP and endpoint name.
- Installed the DEB AMD64 agent package.
- Started the Wazuh Agent service.
- Verified successful Linux endpoint registration.

📌 Refer to the below screenshots: (left to right)

<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/47d3fc28-0ead-4c8b-97c0-de93e30c09ea" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/3a05e364-fa07-4d38-b4d8-5f5cdd0903c7" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/be7ade1d-05ae-4b46-a9a3-c28f06dbfafe" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/9bba7970-4db4-402f-8568-c46c7ab7e3fb" />
<img width="785" height="230" alt="image" src="https://github.com/user-attachments/assets/ba01eb2e-3d37-4713-8ea1-bef0b480e6e7" />


### 8. Sysmon for Windows
- Downloaded Microsoft Sysmon.
- Obtained and configured a Sysmon configuration file. (Olaf’s 'sysmonconfig.xml' file)
- Installed Sysmon using an elevated PowerShell session.
- Verified the Sysmon service was running.

📌 Refer to the below screenshots: (left to right)

<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/9170c662-39a8-452b-a5cf-1bb8f4c0494f" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/9ae1e4ec-ca12-46f9-8787-dd2c2208d370" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/de2fc9dd-d472-4000-bcea-17ca53a08033" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/44df5736-9c53-4f0b-8336-d8818a4e7a80" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/23378f3f-ee39-4df8-9d02-d93eb9ad4665" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/b01b28b9-fbcd-4676-a97f-b9c529560832" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/26b47fb3-56d2-45db-a7bd-e99e3123c2a5" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/25523ebd-39a1-48c3-8d92-73544e576f7d" />
<img width="785" height="230" alt="image" src="https://github.com/user-attachments/assets/83e39a1a-e446-4cec-939b-1a105b20bc6c" />


### 9. Wazuh Sysmon Integration
- Identified the Windows Sysmon event channel through Event Viewer.
- Modified the Windows Wazuh Agent configuration:
```KQL Query:
C:\Program Files (x86)\ossec-agent\ossec.conf
```
- Configured the agent to collect:
```KQL Query:
Microsoft-Windows-Sysmon/Operational
```
- Restarted the Wazuh Agent and verified that Sysmon telemetry was successfully forwarded to Wazuh.

📌 Refer to the below screenshots: (left to right)

<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/00062929-0890-4cd4-8d3a-6deeff84dc14" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/ab638d30-b38d-4fe3-a01e-9c96c2882fe3" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/694cd7db-0b2a-48ac-b3a4-0ecb1f40868d" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/f97ed59c-59fb-4c8c-b2fb-b3a59888845a" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/2f9b3f1e-8910-45e2-8433-d2557ac53512" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/30c38c76-6a21-4025-8396-ab1c2a5f4354" />


### 10. Sysmon for Linux
- Installed Sysmon for Linux.
- Downloaded the collect-all.xml configuration.
- Configured Sysmon to use the supplied configuration.
- Verified Sysmon events were being written to /var/log/syslog.
- Confirmed Linux Sysmon telemetry was successfully received and displayed in Wazuh.

📌 Refer to the below screenshots: (left to right)

<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/71c45599-1156-4dca-8019-4d7a3f6fb29d" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/05b02680-a23e-4479-b7f0-4b80f56234bc" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/50a2205f-62f1-4077-b929-e97c9009102c" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/20c70bcc-a7fb-41cc-a512-c43983a26a52" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/f128e7ea-8bd9-48bd-96ac-2feeb75510ba" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/a99fdcec-1fa8-4062-8e0b-d7b45255de29" />
<img width="785" height="230" alt="image" src="https://github.com/user-attachments/assets/befcfb4f-5481-441c-97c6-5c5b4ad1d14a" />


