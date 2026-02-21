# linux-infrastructure-security-monitoring-wazuh

## Overview

This project consists of the deployment of a secured Linux infrastructure with a dedicated Wazuh Manager and multiple monitored endpoints.

The objective was to implement centralized security monitoring, attack detection, and automated incident response within an isolated virtual network.

---

## Architecture

The lab environment includes:

- **Wazuh Server (192.168.50.20)**
  - Wazuh Manager
  - Centralized log analysis
- **Infra Server – Debian 12 (192.168.50.10)**
  - DHCP (isc-dhcp-server)
  - DNS (BIND9)
  - GLPI
  - Wazuh Agent
- **Ubuntu Workstation**
  - Wazuh Agent

Internal network: `192.168.50.0/24` (Host-only)

DNS resolution:
`wazuh.library.lan → 192.168.50.20`

---

## Security Scenarios

### 1️⃣ SSH Brute Force Detection

- Multiple failed SSH attempts triggered Wazuh rule **5760**
- Alert generated on the Wazuh dashboard
- Active Response executed (`firewall-drop`)
- Attacker IP blocked for 300 seconds

Result: automatic containment validated.

---

### 2️⃣ YARA Malware Detection & Auto-Removal

- Custom YARA rule detects malicious IOC string
- Detection sent to syslog
- Custom Wazuh rule (ID 100100) triggered
- Active Response script executed
- Malicious file automatically deleted

Result: detection + remediation fully automated.

---

## Security Features Implemented

- Centralized log collection
- Event correlation
- Custom Wazuh rules
- Active Response customization
- Network-based attack containment
- Automated file removal

---

## Skills Demonstrated

- SIEM deployment (Wazuh)
- Linux system administration
- Incident detection & response
- Log analysis
- Security automation
- Network service configuration

---
