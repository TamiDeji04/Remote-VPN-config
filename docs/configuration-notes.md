# Configuration Notes

## Certificate hierarchy

```text
CorpNet-CA
    |
    +---- CorpNet (OpenVPN server certificate)
```

The CA represents the internal trust authority. The server certificate identifies the OpenVPN server.

## VPN flow

```text
Remote user
    |
    | Username/password
    v
OpenVPN on pfSense WAN
    |
    | Authenticated tunnel
    v
198.28.20.0/24
    |
    | Firewall-controlled traffic
    v
198.28.56.18/24
```

## Security controls

1. Server-side certificate infrastructure
2. Local user authentication
3. Dedicated VPN address space
4. WAN firewall rule
5. OpenVPN interface rule
6. Restricted inter-client communication
7. No full-tunnel redirect gateway configured

## Evidence notes

The screenshots in this repository are configuration evidence from the TestOut pfSense lab. Credentials are intentionally omitted from the public documentation.

The unrelated iPad/IPsec screenshots from the session are not included because they demonstrate a different VPN technology and would incorrectly imply that they validate the OpenVPN configuration.
