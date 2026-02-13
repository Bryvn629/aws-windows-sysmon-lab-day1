# AWS Windows Sysmon Lab – Day 1

## 📌 Lab Objective
Deploy a Windows Server instance in AWS, install Sysmon, apply a production-grade configuration, and validate endpoint telemetry through Event Viewer.

---

## 🧱 Environment Setup

- Cloud Provider: AWS EC2
- Instance Type: t3.micro
- OS: Windows Server
- Remote Access: RDP (Microsoft Remote Desktop from Chromebook)
- Security Monitoring Tool: Sysinternals Sysmon v15.x
- Configuration Used: SwiftOnSecurity sysmon-config

---

## 🔧 Actions Performed

### 1️⃣ Launched AWS EC2 Windows Instance
- Created Windows Server instance (t3.micro)
- Configured security group for RDP (3389)
- Connected via Microsoft Remote Desktop

### 2️⃣ Installed Sysmon
Downloaded Sysmon from Microsoft Sysinternals and executed:sysmon64.exe-accepteula-i sysmoncofig-export.xml

Verified installation via: 
sysmon64.exe


Result:
- Sysmon Service Installed
- Sysmon Driver Installed
- Service Running

---

### 3️⃣ Applied SwiftOnSecurity Configuration
- Downloaded sysmonconfig-export.xml
- Enabled file name extensions
- Verified XML format
- Successfully loaded configuration

Confirmation Output:
- Configuration file validated
- Sysmon service started

---

### 4️⃣ Generated Test Activity
Executed test commands in Command Prompt:

net user testuser P@ssword123 /add
net localgroup administrators testuser /add


---

### 5️⃣ Validated Logs in Event Viewer

Navigated to:
Event Viewer → Applications and Services Logs → Microsoft → Windows → Sysmon → Operational

Confirmed:
- Event ID 1 (Process Creation)
- Full command-line logging enabled
- User context captured
- Timestamps logged
- Parent process visibility

---

## 🔎 Key Findings

Sysmon successfully captured:
- cmd.exe execution
- net user command
- net localgroup command
- Account creation activity

This demonstrates:
- Endpoint telemetry visibility
- Process creation monitoring
- Command-line auditing capability

---

## 🛡️ Security Relevance

In a real SOC environment, this configuration enables detection of:
- Unauthorized account creation
- Privilege escalation attempts
- Lateral movement preparation
- Living-off-the-land activity

Sysmon provides high-fidelity logging beyond default Windows logs.

---

## 📚 Skills Demonstrated

- AWS EC2 deployment
- Windows Server administration
- RDP remote management
- Sysmon installation and configuration
- Endpoint telemetry validation
- Basic detection engineering validation

---

## 🚀 Day 1 Outcome

Successfully deployed and validated a cloud-hosted Windows monitoring environment with enhanced endpoint visibility.

Ready for log forwarding and centralized monitoring (Day 2).

## Screenshots

### EC2 Instance Running
![EC2 Running](screenshots/01-ec2-instance-running.png)

### Sysmon Configuration Loaded
![Sysmon Config](screenshots/02-sysmon-config-loaded.png)

### Sysmon Installation Verified
![Sysmon Installed](screenshots/03-sysmon-installed-cmd.png)

### Sysmon Events in Event Viewer
![Event Viewer](screenshots/04-event-viewer-sysmon-events.png)

## 🔎 Key Skills Demonstrated

- AWS EC2 provisioning and remote Windows administration
- Sysmon installation and configuration validation
- Windows Event Viewer navigation for security telemetry
- Endpoint logging setup used in SOC workflows
- Basic threat detection visibility preparation






