# Evidence Index

Each screenshot below was retained because it directly supports the OpenVPN lab documentation. Filenames are numbered in the order they are used in the configuration walkthrough.

| # | Screenshot | Configuration area | Evidence |
|---|---|---|---|
| 01 | [01-server-certificate.png](../screenshots/01-server-certificate.png) | Certificate | Shows the `CorpNet` server certificate identity and certificate configuration fields. |
| 02 | [02-openvpn-server-setup.png](../screenshots/02-openvpn-server-setup.png) | OpenVPN server | Shows Remote Access (User Auth), Local Database authentication, WAN, UDP/IPv4, port 1194, and `CorpNet-VPN`. |
| 03 | [03-tunnel-settings.png](../screenshots/03-tunnel-settings.png) | Tunnel/network | Shows the VPN tunnel network, internal network, routing behavior, and client-communication settings. |
| 04 | [04-client-dns-settings.png](../screenshots/04-client-dns-settings.png) | Client settings | Shows client address/topology settings and DNS server `198.28.56.1`. |
| 05 | [05-firewall-rules.png](../screenshots/05-firewall-rules.png) | Firewall | Shows the OpenVPN setup workflow with the required WAN and OpenVPN firewall rules selected. |
| 06 | [06-openvpn-server-final.png](../screenshots/06-openvpn-server-final.png) | Final server configuration | Shows the saved OpenVPN server configuration after setup. |
| 07 | [07-vpn-users.png](../screenshots/07-vpn-users.png) | Authentication | Shows the local pfSense accounts used for VPN authentication. Passwords are not exposed. |

## Evidence Notes

- The documented concurrent-connection setting is **4**. The retained tunnel screenshot does not show the final value, so it is not treated as evidence for that specific setting.
- The original collection included unrelated iPad/IPsec screenshots. They were excluded because they document a different VPN technology.
- One TestOut overview screenshot displayed scenario credentials. It was excluded from the public repository to avoid exposing credentials.
- The screenshots document configuration state but do not independently prove successful end-to-end VPN client connectivity.
