# Network Security Findings

## Overview

A network scan was conducted using Nmap to identify active hosts, enumerate services, and assess potential security risks within a local network environment.

All data has been anonymized to avoid exposure of sensitive information.

---

## Network Discovery

- Subnet analyzed: 192.168.X.0/27
- Active hosts detected: 7

The scan revealed multiple devices including a network gateway, a Windows-based host, and restricted devices with minimal exposure.

---

## Gateway Analysis (192.168.X.1)

### Open Ports
- 53/tcp (DNS)
- 80/tcp (HTTP/HTTPS - Web Interface)

### Filtered Ports
- 21/tcp (FTP)
- 22/tcp (SSH)
- 23/tcp (Telnet)
- 8022/tcp (Unknown)
- 8899/tcp (Unknown)

### Security Analysis
- The HTTP service suggests that the gateway management interface is accessible via web.
- This represents a potential attack vector if authentication mechanisms are weak or misconfigured.
- DNS service is expected but may be abused if improperly secured.
- Filtering of critical services indicates the presence of firewall protections.
- Additional filtered ports suggest restricted or internal services not exposed externally.

---

## Windows Host Analysis (192.168.X.X)

### Open Ports
- 135/tcp (MSRPC)
- 139/tcp (NetBIOS)
- 445/tcp (SMB)
- 5432/tcp (PostgreSQL)

### Security Analysis
- SMB (port 445) is a high-risk service commonly targeted in internal network attacks.
- NetBIOS may expose system and user-related information.
- MSRPC can be leveraged for service enumeration and remote procedure calls.
- PostgreSQL exposure suggests a database service accessible over the network, which could lead to unauthorized access if not properly secured.
- This host represents a strong candidate for lateral movement in case of compromise.

---

## Restricted Device Analysis (192.168.X.X)

### Findings
- No open ports detected
- All scanned ports are closed

### Security Analysis
- The absence of exposed services significantly reduces the attack surface.
- The behavior is consistent with modern mobile devices or hardened endpoints.
- The device likely implements firewall rules and may use MAC randomization for privacy.
- This reflects a default-deny security posture.

---

## Comparative Analysis

The analysis of different devices highlights varying levels of exposure within the same network:

- The gateway exposes essential services required for network operation, representing a moderate attack surface.
- The Windows host exposes multiple services, including SMB and a database, significantly increasing risk.
- The restricted device does not expose services, indicating a minimal attack surface.

This demonstrates how different device types contribute differently to the overall network security posture.

---

## Risk Summary

| Device Type        | Risk Level | Reason                                      |
|-------------------|-----------|---------------------------------------------|
| Gateway           | Medium    | Web interface exposed                       |
| Windows Host      | High      | SMB and database services exposed           |
| Restricted Device | Low       | No open ports                               |

---

## Conclusion

The analysis highlights the importance of asset visibility and service exposure in network security.

While some devices maintain a minimal attack surface, others expose services that could be leveraged for internal attacks, particularly in scenarios involving lateral movement.

Implementing network segmentation, restricting unnecessary services, and enforcing strong authentication mechanisms are recommended to improve the overall security posture.