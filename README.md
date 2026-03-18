# Network Security Analysis with Nmap

## Overview

This project demonstrates a practical approach to network security analysis using Nmap. The objective is to identify active devices, enumerate exposed services, and assess potential security risks within a local network from a Blue Team perspective.

The analysis focuses on understanding the network attack surface and evaluating how different devices contribute to overall security posture.

---

## Objectives

* Perform network discovery to identify active hosts
* Enumerate open ports and running services
* Analyze potential security risks
* Compare exposure levels between different device types
* Document findings in a professional and structured format

---

## Tools & Environment

* Nmap (Network Scanner)
* Windows 11
* Local Network Environment

---

## Methodology

The analysis was conducted in three main phases:

### 1. Network Discovery

A ping scan was performed to identify active hosts within the subnet:

```bash
nmap -sn 192.168.X.0/27
```

---

### 2. Service Enumeration

Targeted scans were executed on selected devices to identify open ports and services:

```bash
nmap -sS -sV 192.168.X.X
```

---

### 3. Analysis

Results were analyzed to determine:

* Exposed services
* Potential vulnerabilities
* Attack surface per device
* Risk level classification

---

## Key Findings

### Gateway 

* Open ports: DNS (53), HTTP (80)
* Filtered ports: FTP, SSH, Telnet

**Analysis:**

* Web interface exposed → potential attack vector
* Firewall filtering detected → basic protection in place

---

### Windows Host

* Open ports: 135 (MSRPC), 139 (NetBIOS), 445 (SMB), 5432 (PostgreSQL)

**Analysis:**

* SMB exposure → high risk for lateral movement
* NetBIOS → potential information disclosure
* PostgreSQL → database accessible over network

---

### Mobile / Restricted Device

* No open ports detected

**Analysis:**

* Minimal attack surface
* Default-deny behavior
* Likely uses firewall and MAC randomization

---

## Comparative Analysis

Different devices present different levels of exposure:

| Device Type   | Exposure Level | Risk   |
| ------------- | -------------- | ------ |
| Gateway       | Moderate       | Medium |
| Windows Host  | High           | High   |
| Mobile Device | Minimal        | Low    |

This highlights the importance of asset visibility and service management in network security.

---

## Security Insights

* Internal devices can represent significant risk (not only external threats)
* SMB and database services increase attack surface
* Network segmentation is critical to prevent lateral movement
* Default-secure configurations (like mobile devices) reduce exposure

---

## Data Anonymization

All IP addresses and hardware identifiers have been anonymized to protect sensitive information and avoid exposing real network infrastructure.

---

## Conclusion

This project demonstrates how basic network scanning techniques can provide valuable insights into security posture.

The results emphasize the importance of:

* Monitoring active devices
* Reducing exposed services
* Implementing proper access controls
* Understanding internal network risks

