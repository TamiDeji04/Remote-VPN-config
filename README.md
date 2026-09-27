# pfSense OpenVPN Remote Access Lab

## Overview

This project documents a pfSense OpenVPN Remote Access (User Auth) lab configured in a TestOut-style network environment.

## Objectives

- Configure certificate infrastructure for the VPN server.
- Configure pfSense for authenticated OpenVPN remote access.
- Define a dedicated VPN tunnel network and internal network.
- Configure DNS delivery to VPN clients.
- Apply WAN and OpenVPN firewall controls.
- Document the configuration as portfolio evidence.

## Architecture

```text
Remote VPN User
      |
      | Username / Password
      v
pfSense WAN
      |
      | OpenVPN / UDP 1194
      v
VPN Tunnel: 198.28.20.0/24
      |
      | Firewall-controlled traffic
      v
Internal Network: 198.28.56.18/24
```

## Certificate Configuration

- Certificate Authority: `CorpNet-CA`
- Server certificate: `CorpNet`
- Country: GB
- State/Province: Cambridgeshire
- Locality: Woodwalton
- Organization: CorpNet

## OpenVPN Server Configuration

- Mode: Remote Access (User Auth)
- Authentication backend: Local Database
- Interface: WAN
- Protocol: UDP on IPv4 only
- Port: 1194
- Description: CorpNet-VPN
- Tunnel network: 198.28.20.0/24
- Local network: 198.28.56.18/24
- Concurrent connections: 4
- DNS Server 1: 198.28.56.1
- Tunnel type: TUN / Layer 3

## User Authentication

Two local VPN users were configured for the lab:

- `blindley`
- `jphillips`

Passwords are intentionally omitted from this repository.

## Firewall Configuration

The lab includes firewall controls for:

1. Allowing the OpenVPN service on the WAN interface.
2. Controlling traffic arriving through the OpenVPN interface.

## Security Concepts Demonstrated

- Certificate-based server identity
- Local VPN user authentication
- Network segmentation
- Remote-access VPN architecture
- Firewall access control
- DNS configuration for remote clients
- Separation of VPN service access from tunneled traffic

## Verification Scope

The screenshots document the server-side configuration and final settings. They do not claim end-to-end OpenVPN client connectivity because a dedicated OpenVPN client validation was not captured for this lab.

## Skills Demonstrated

pfSense, OpenVPN, VPN authentication, certificates, firewall rules, IPv4 networking, DNS, network segmentation, remote access, security documentation.

## Resume Entry

**pfSense OpenVPN Remote Access Lab**
- Configured pfSense as an OpenVPN Remote Access (User Auth) gateway using WAN, UDP/IPv4, local authentication, and a dedicated VPN tunnel network.
- Created a certificate authority/server certificate hierarchy and configured VPN addressing, internal network routing, and DNS for remote clients.
- Implemented WAN and OpenVPN firewall rules to control access to the VPN service and traffic traversing the authenticated tunnel.
- Configured local VPN users and documented the security architecture, access controls, and network flow.

## Repository Structure

```text
pfSense-OpenVPN-Remote-Access-Lab/
├── README.md
├── docs/
│   ├── configuration-notes.md
│   ├── evidence-index.md
│   └── resume-entry.md
└── screenshots/
    ├── 01-server-certificate.png
    ├── 02-openvpn-server-setup.png
    ├── 03-tunnel-settings.png
    ├── 04-client-settings.png
    ├── 05-firewall-rules.png
    ├── 06-openvpn-server-final.png
    └── 07-vpn-users.png
```
