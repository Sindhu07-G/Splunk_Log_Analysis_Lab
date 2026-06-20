# Splunk SIEM Log Analysis Lab

## Project Overview

This project demonstrates the installation, configuration, and use of Splunk Enterprise for security monitoring and log analysis on Ubuntu Linux.

The objective was to collect Linux authentication logs, ingest them into Splunk, perform security event analysis using SPL (Search Processing Language), and visualize log activity through statistical reports and charts.

This hands-on project helped develop practical SIEM skills commonly used by SOC Analysts for monitoring authentication events, privileged access activities, and system processes.

---

## Objectives

- Install and configure Splunk Enterprise on Ubuntu Linux
- Collect Linux authentication logs
- Import log data into Splunk
- Perform log analysis using SPL queries
- Monitor authentication and sudo activities
- Generate statistics and visualizations
- Gain hands-on experience with SIEM operations

---

## Technologies Used

- Ubuntu Linux
- Splunk Enterprise
- VirtualBox
- Linux Authentication Logs (auth.log)
- SPL (Search Processing Language)

---

## Lab Environment

| Component | Description |
|------------|------------|
| Operating System | Ubuntu Linux |
| SIEM Platform | Splunk Enterprise |
| Virtualization | Oracle VirtualBox |
| Log Source | /var/log/auth.log |

---

## Installation and Configuration

### Step 1: Install Splunk Enterprise

Downloaded and installed Splunk Enterprise on Ubuntu Linux.

### Step 2: Start Splunk Service

```bash
sudo /opt/splunk/bin/splunk start
```

Created an administrator account during the initial setup process.

### Step 3: Access Splunk Web Interface

Opened Splunk Web Interface:

```text
http://localhost:8000
```

Logged in using administrator credentials.

---

## Log Collection

Verified the Linux authentication log file:

```bash
sudo ls -lh /var/log/auth.log
```

Uploaded the auth.log file into Splunk using:

Add Data → Upload File → auth.log

---

## Data Analysis

### Search 1: View All Events

```spl
index=main
```

Purpose:
- Display all ingested log events.

---

### Search 2: Investigate Sudo Activity

```spl
index=main sudo
```

Purpose:
- Identify privileged command execution events.

---

### Search 3: Count Executed Commands

```spl
index=main sudo | stats count by COMMAND
```

Purpose:
- Display commands executed with sudo privileges.

---

### Search 4: Process Analysis

```spl
index=main session | stats count by process
```

Purpose:
- Identify processes generating authentication events.

Observed processes:

- sudo
- CRON
- systemd-logind
- sshd
- gdm-password
- useradd
- groupadd
- dbus-daemon

---

### Search 5: Event Trend Visualization

```spl
index=main | timechart count
```

Purpose:
- Visualize authentication activity over time.

---

### Search 6: Top Processes

```spl
index=main | top process limit=10
```

Purpose:
- Identify the most active processes within authentication logs.

---

## Key Findings

- Successfully collected Linux authentication logs.
- Detected sudo command executions.
- Identified login session activity.
- Observed CRON scheduled task events.
- Monitored SSH-related authentication records.
- Generated statistical reports and visualizations using Splunk.

---

## Skills Demonstrated

- SIEM Operations
- Security Monitoring
- Log Management
- Linux Administration
- Authentication Log Analysis
- Splunk Enterprise
- SPL Querying
- Event Investigation
- Data Visualization

---

## Learning Outcomes

This project provided practical experience with SIEM deployment, log ingestion, security monitoring, and SPL-based investigations. It strengthened foundational SOC Analyst skills related to authentication monitoring and event analysis using Splunk Enterprise.

---

## Author

**Sindhu Gajula**

Aspiring Cybersecurity Analyst | SOC Analyst Enthusiast

GitHub: https://github.com/Sindhu07-G
