# Configuration Notes

## 1. Certificate hierarchy

```
CorpNet-CA
    |
    +---- CorpNet (OpenVPN server certificate)
```

The certificate evidence is captured in [01-server-certificate.png](../screenshots/01-server-certificate.png). The screenshot shows the CorpNet server certificate being created with the lab's certificate identity fields.

## 2. OpenVPN server

[02-openvpn-server-setup.png](../screenshots/02-openvpn-server-setup.png) documents:

- Interface: WAN
- Protocol: UDP on IPv4 only
- Port: 1194
- Description: CorpNet-VPN
- TLS authentication enabled
- TLS key generation enabled

The resulting saved server configuration is shown in [06-openvpn-server-final.png](../screenshots/06-openvpn-server-final.png).
## 3. Tunnel and internal network

[03-tunnel-settings.png](../screenshots/03-tunnel-settings.png) documents:

- Tunnel network: 198.28.20.0/24
- Local network: 198.28.56.18
- Redirect Gateway: disabled
- Inter-client communication: disabled
- Duplicate connections: disabled

- Concurrent connections: 4

The captured tunnel screenshot does not show the final configured concurrent-connection value. The documented value of 4 is retained as the lab configuration rather than being inferred from that screenshot.

## 4. Client configuration

[04-client-dns-settings.png](../screenshots/04-client-dns-settings.png) shows:

- Dynamic IP enabled
- Subnet topology
- DNS Server 1: 198.28.56.1

## 5. Firewall controls

[05-firewall-rules.png](../screenshots/05-firewall-rules.png) shows both firewall controls selected in the OpenVPN setup wizard:

1. A rule permitting clients to connect to the OpenVPN server.
2. An OpenVPN rule permitting connected clients to pass traffic through the VPN tunnel.
## 6. User authentication

[07-vpn-users.png](../screenshots/07-vpn-users.png) shows the local pfSense accounts used for VPN authentication:

- blindley
- jphillips

Passwords are not included in the repository.

## 7. VPN flow

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

## Evidence limitations

The screenshots document the server-side configuration and user setup. They do not, by themselves, establish successful end-to-end OpenVPN client connectivity.

The iPad/IPsec screenshots from the original session are excluded because they demonstrate a different VPN technology.
