# Configuration Notes

## 1. Certificate Hierarchy

```text
CorpNet-CA
    |
    +---- CorpNet (OpenVPN server certificate)
```

[01-server-certificate.png](../screenshots/01-server-certificate.png) documents the server certificate identity used by the lab.

## 2. OpenVPN Server

[02-openvpn-server-setup.png](../screenshots/02-openvpn-server-setup.png) captures the main OpenVPN server configuration:

- Mode: Remote Access (User Auth)
- Authentication: Local Database
- Interface: WAN
- Protocol: UDP on IPv4 only
- Port: 1194
- Description: `CorpNet-VPN`
- Device mode: TUN / Layer 3

[06-openvpn-server-final.png](../screenshots/06-openvpn-server-final.png) shows the resulting saved server configuration.

## 3. Tunnel and Internal Network

[03-tunnel-settings.png](../screenshots/03-tunnel-settings.png) documents:

- Tunnel network: `198.28.20.0/24`
- Local network: `198.28.56.18`
- Redirect Gateway: disabled
- Inter-client communication: disabled
- Duplicate connections: disabled
- Concurrent connections: 4

The retained tunnel screenshot was captured before the final concurrent-connection value was visible. The documented value of 4 is retained as the lab configuration rather than inferred from that screenshot.

## 4. Client Configuration

[04-client-dns-settings.png](../screenshots/04-client-dns-settings.png) shows:

- Dynamic IP enabled
- Subnet topology
- DNS Server 1: `198.28.56.1`

## 5. Firewall Controls

[05-firewall-rules.png](../screenshots/05-firewall-rules.png) shows both firewall controls selected in the OpenVPN setup workflow:

1. A rule permitting clients to connect to the OpenVPN server.
2. An OpenVPN rule permitting connected clients to pass traffic through the VPN tunnel.

## 6. User Authentication

[07-vpn-users.png](../screenshots/07-vpn-users.png) shows two local pfSense accounts used for VPN authentication:

- `blindley`
- `jphillips`

Passwords are not included in the repository.

## 7. VPN Traffic Flow

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

## Evidence Limitations

The screenshots document the server-side configuration and user setup. They do not, by themselves, establish successful end-to-end OpenVPN client connectivity.

The excluded iPad/IPsec screenshots are not part of this lab's OpenVPN evidence set.
