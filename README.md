# FortiGate Enterprise Network Security — Final Project

**Engineer:** Bishoy Gerges
**Course instructor:** Eng. Mahmoud Sabry  
**Project type:** Individual, hands-on FortiGate firewall administration lab  
**Scope:** 50 integrated practical tasks (as reported by the project author)

## Overview

This project documents my individual FortiGate Firewall final assessment, where I built and configured an integrated enterprise-style network security lab from scratch. It combines network segmentation, identity-aware access control, security inspection, multi-WAN routing, remote connectivity, monitoring, and redundancy.

> **Evidence note:** The accompanying 28 screenshots show selected configuration screens and an HA cluster state. They are not a screenshot for every one of the 50 tasks, nor do they independently demonstrate end-to-end verification for every feature. See [Validation and Evidence](#validation-and-evidence).

## Technologies and areas covered

| Area | Implementation topics |
| --- | --- |
| Network foundations | LAN/WAN interfaces, VLANs, DHCP, IP reservations, link aggregation, static routing |
| Firewall access control | Firewall policies, address objects, schedules, DNAT/VIPs, policy-based routing |
| Identity | Admin roles, trusted hosts, local users, LDAP server integration, captive portal |
| Threat protection | Antivirus, web filtering, application control, IPS, certificate/SSL inspection |
| WAN resilience | Multi-ISP SD-WAN, performance SLA, steering/load balancing |
| Secure remote connectivity | SSL VPN and IPsec site-to-site VPN |
| Availability and operations | Active-passive HA, Security Fabric automation, email alerting, encrypted backup |

The scope table summarizes the author's completed final-assessment work. Screenshots substantiate a subset of these configurations.

## Architecture overview

The lab connects segmented internal networks and a Windows Server environment through FortiGate, applying centralized security policies and using multiple WAN interfaces for SD-WAN. A second FortiGate device participates in an HA cluster. Logical layout (not a verified port-to-port wiring diagram):

```text
                  ISP / WAN connections
                        |
                [ FortiGate SD-WAN ]
                        |
                [ Firewall Policies ]
                        |
          +-------------+-------------+
          |             |             |
     VLAN / LANs   Windows Server   Remote access
     + DHCP        / LDAP           (VPN)

         [ FortiGate HA peer (active-passive) ]
```

## Selected configuration evidence

### Network and identity
- [Network interfaces](screenshots/netwrok%20interfaces.png) — interfaces and segmented LAN/WAN entries shown in the FortiGate UI.
- [LDAP server object](screenshots/serverr%20connect.png) — Windows Server LDAP integration entry.
- [Administrator settings](screenshots/users.png) — administrator list and profiles.
- [Static routing](screenshots/static%20route.png) and [policy routes](screenshots/policyroute.png).

### Firewall and security inspection
- [Firewall policies and security profiles](screenshots/polices%20with%20security%20prof.png).
- [Web filter URL rules](screenshots/webfilter.png) and [category quota](screenshots/quota%2Bwebfilter.png).
- [Application control](screenshots/Application%20control.png), [antivirus](screenshots/antivirus.png), [client IPS](screenshots/IPS-CLIENT.png), and [server IPS](screenshots/IPS-SERVER.png).
- [Certificate / CSR view](screenshots/create%20csr.png).

### Availability, WAN and monitoring
- [SD-WAN members](screenshots/sd-wan.png), [performance SLA](screenshots/performance-SLA.png), and [SLA rules](screenshots/SLA%20Rules.png).
- [HA configuration view](screenshots/HA.png) and [HA cluster state](screenshots/HA%20successfully.png).
- [Security Fabric automation example](screenshots/securityfabric4.png) and [email alerts](screenshots/email%20log%20alert.png).
- [Encrypted backup setup](screenshots/backup-sys.png) and [SSL VPN settings](screenshots/ssl%20vpn.png).

The complete image set is in [`screenshots/`](screenshots/). More detailed grouping is available in [`EVIDENCE_INDEX.md`](EVIDENCE_INDEX.md).

## Validation and evidence

The project author reports completing all 50 tasks successfully. The screenshot archive contains **28 images**, primarily configuration screens. In particular, `HA successfully.png` shows the cluster membership and primary/secondary state. A complete verification package could additionally include sanitized connectivity tests, DHCP lease evidence, policy hit/log results, VPN tunnel status, and SD-WAN failover checks. These are suggested **additional evidence**, not results claimed to be in this archive.

## Skills practiced

FortiGate firewall administration · VLANs/DHCP · network access policies · LDAP integration · UTM profiles · SD-WAN · VPN · HA · monitoring and secure backups.

## Publication / safety

This repository represents a **training lab**, not production infrastructure. Before publishing publicly, review every screenshot for login names, email addresses, network topology details, hostnames, identifiers, tokens, and other sensitive information; redact anything you do not wish to disclose. **Never upload a real firewall backup or private key.**

## Credits

Independent project by **Bishoy Gerges**. Course instruction: **Eng. Mahmoud Sabry**.
