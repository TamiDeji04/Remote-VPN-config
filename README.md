# pfSense OpenVPN Remote Access Lab

A documented pfSense OpenVPN remote-access lab focused on authenticated VPN access, network segmentation, DNS delivery, firewall controls, and configuration evidence.

## Lab Objectives

- Configure a certificate authority and OpenVPN server certificate.
- Configure pfSense for OpenVPN Remote Access with local user authentication.
- Define a dedicated VPN tunnel network and internal network.
- Provide DNS settings to VPN clients.
- Apply firewall controls for VPN service access and tunneled traffic.
- Organize configuration screenshots as portfolio evidence.

## Network Overview

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
Internal Network: 198.28.56.18
```

## Configuration Summary

| Area | Configuration |
|---|---|
| VPN mode | Remote Access (User Auth) |
| Authentication | Local Database |
| Interface | WAN |
| Protocol | UDP, IPv4 only |
| Port | 1194 |
| Device mode | TUN / Layer 3 |
| VPN description | CorpNet-VPN |
| Tunnel network | `198.28.20.0/24` |
| Internal network | `198.28.56.18` |
| DNS server | `198.28.56.1` |
| Concurrent connections | 4 |
| Redirect Gateway | Disabled |
| Inter-client communication | Disabled |

The documented concurrent-connection setting is **4**. The available tunnel screenshot was captured before the final value was visible, so that screenshot is retained as historical configuration evidence rather than used to establish the final connection limit.

## Certificate Configuration

- Certificate Authority: `CorpNet-CA`
- Server certificate: `CorpNet`
- Country: `GB`
- State/Province: `Cambridgeshire`
- Locality: `Woodwalton`
- Organization: `CorpNet`

Evidence: [01-server-certificate.png](screenshots/01-server-certificate.png)

## Firewall Controls

The lab configured two firewall controls through the OpenVPN setup workflow:

1. A rule permitting clients to connect to the OpenVPN server.
2. An OpenVPN rule permitting authenticated clients to pass traffic through the VPN tunnel.

Evidence: [05-firewall-rules.png](screenshots/05-firewall-rules.png)

## User Authentication

The pfSense User Manager screenshot shows two local VPN accounts:

- `blindley`
- `jphillips`

Passwords are intentionally excluded.

Evidence: [07-vpn-users.png](screenshots/07-vpn-users.png)

## Security Concepts Demonstrated

- Certificate-based server identity
- Local VPN authentication
- Network segmentation
- Layer 3 VPN tunneling
- Firewall access control
- DNS configuration for remote clients
- Separation of VPN service access from tunneled traffic

## Verification Scope

The repository documents the server-side configuration and captured lab evidence. It does **not** claim successful end-to-end OpenVPN client connectivity because a dedicated client-connectivity validation was not captured.

## Documentation

- [Evidence Index](docs/evidence-index.md) — maps each retained screenshot to the configuration it demonstrates.
- [Configuration Notes](docs/configuration-notes.md) — provides the technical walkthrough and network flow.
- [Resume Entry](docs/resume-entry.md) — concise resume-ready project bullets.

## Repository Structure

```text
Remote-VPN-config/
├── README.md
├── .gitignore
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
