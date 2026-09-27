# pfSense OpenVPN Remote Access Lab

## Overview

This project documents a pfSense OpenVPN Remote Access (User Auth) lab configured in a TestOut-style network environment.

The repository is organized so that each major configuration step has corresponding screenshot evidence in [screenshots/](screenshots/) and a direct explanation in [docs/evidence-index.md](docs/evidence-index.md).

## Objectives

- Configure certificate infrastructure for the VPN server.
- Configure pfSense for authenticated OpenVPN remote access.
- Define a dedicated VPN tunnel network and internal network.
- Configure DNS delivery to VPN clients.
- Apply WAN and OpenVPN firewall controls.
- Document the configuration as portfolio evidence.

## Architecture

```
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
Internal Network: 198.28.56.18
```

## Certificate Configuration

- Certificate Authority: CorpNet-CA
- Server certificate: CorpNet
- Country: GB
- State/Province: Cambridgeshire
- Locality: Woodwalton
- Organization: CorpNet

Evidence: [01-server-certificate.png](screenshots/01-server-certificate.png)
## OpenVPN Server Configuration

- Mode: Remote Access (User Auth)
- Authentication backend: Local Database
- Interface: WAN
- Protocol: UDP on IPv4 only
- Port: 1194
- Description: CorpNet-VPN
- Device mode: TUN / Layer 3

Evidence:
- [02-openvpn-server-setup.png](screenshots/02-openvpn-server-setup.png)
- [06-openvpn-server-final.png](screenshots/06-openvpn-server-final.png)

## Network and Client Configuration

- Tunnel network: 198.28.20.0/24
- Local network: 198.28.56.18
- DNS Server 1: 198.28.56.1
- Redirect Gateway: disabled
- Inter-client communication: disabled

Evidence:
- [03-tunnel-settings.png](screenshots/03-tunnel-settings.png)
- [04-client-dns-settings.png](screenshots/04-client-dns-settings.png)

The tunnel screenshot shows the concurrent-connections field as 0 at capture time, so this repository does not claim a different final value without screenshot evidence.

## User Authentication

Two local VPN users are shown in pfSense User Manager:

- blindley
- jphillips

Evidence: [07-vpn-users.png](screenshots/07-vpn-users.png)

Passwords are intentionally omitted from the repository.
## Firewall Configuration

The lab includes:

1. A firewall rule allowing clients to connect to the OpenVPN server.
2. An OpenVPN rule allowing connected clients to pass traffic through the VPN tunnel.

Evidence: [05-firewall-rules.png](screenshots/05-firewall-rules.png)

## Security Concepts Demonstrated

- Certificate-based server identity
- Local VPN user authentication
- Network segmentation
- Remote-access VPN architecture
- Firewall access control
- DNS configuration for remote clients
- Layer 3 VPN tunneling
- Separation of VPN service access from tunneled traffic

## Verification Scope

The screenshots document the server-side configuration and final settings. They do not claim end-to-end OpenVPN client connectivity because a dedicated OpenVPN client validation was not captured for this lab.

## Documentation

- [Evidence Index](docs/evidence-index.md) — screenshot-by-screenshot mapping
- [Configuration Notes](docs/configuration-notes.md) — technical explanation and network flow
- [Resume Entry](docs/resume-entry.md) — concise resume-ready project description

## Resume Entry

**pfSense OpenVPN Remote Access Lab**
- Configured pfSense as an OpenVPN Remote Access (User Auth) gateway using WAN, UDP/IPv4, local authentication, and a dedicated VPN tunnel network.
- Created a certificate authority/server certificate hierarchy and configured VPN addressing, internal network routing, and DNS for remote clients.
- Implemented WAN and OpenVPN firewall rules to control access to the VPN service and traffic traversing the authenticated tunnel.
- Configured local VPN users and documented the security architecture, access controls, and network flow.
## Repository Structure

```
Remote-VPN-config/
├── README.md
├── docs/
│   ├── configuration-notes.md
│   ├── evidence-index.md
│   └── resume-entry.md
└── screenshots/
    ├── 01-server-certificate.png
    ├── 02-openvpn-server-setup.png
    ├── 03-tunnel-settings.png
    ├── 04-client-dns-settings.png
    ├── 05-firewall-rules.png
    ├── 06-openvpn-server-final.png
    └── 07-vpn-users.png
```
