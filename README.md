# PFSENSE Project

[![pfSense](https://img.shields.io/badge/pfSense-Firewall-blue)](https://www.pfsense.org/)
[![Status](https://img.shields.io/badge/Status-Learning-green)]()
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)]()

A hands-on project showcasing **pfSense firewall** installation, configuration, and security features.
Covers LAN/DMZ setup, NAT, VPN, IDS, and proxy filtering.

---

## Network Topology

```sh
                   ┌───────────────┐
                   │     WAN       │
                   │   Internet    │
                   └───────┬───────┘
                           │
                    ┌──────▼──────┐
                    │   pfSense   │
                    │ Firewall/   │
                    │ VPN / IDS   │
                    └──────┬──────┘
             ┌─────────────┼─────────────┐
             │             │             │
      ┌──────▼──────┐┌─────▼──────┐┌────▼─────┐
      │    LAN      ││    DMZ      ││ OpenVPN  │
      │ Internal PC ││ Web Server  ││ Remote   │
      └─────────────┘└─────────────┘└─────────┘
```

---

## Tasks

- `Task01-Installation` -> pfSense installation & basic setup
- `Task02-LAN-&-DMZ` -> LAN/DMZ configuration
- `Task03-SNAT-&-DNAT` -> Source & Destination NAT
- `Task04-OPENVPN` -> OpenVPN server setup
- `Task05-RADIUS-OPENVPN` -> RADIUS authentication for OpenVPN
- `Task06-SURICATA-IDS` -> Suricata intrusion detection
- `Task07-Squid-Transparent-Proxy` -> Squid proxy configuration
- `Task08-SQUID-GUARD-BLACKLIST` -> Web filtering with SquidGuard

---

## Quick Start

1. Download [pfSense ISO](https://www.pfsense.org/download/).
2. Create a VM (VirtualBox / VMware / Proxmox).
3. Install pfSense.

---

## References

- [pfSense Docs](https://docs.netgate.com/pfsense/en/latest/)
- [Suricata IDS](https://suricata.io/)
- [Squid Proxy](http://www.squid-cache.org/)

---

## Author

**thierno953** – System & Network Administration | Cybersecurity Enthusiast
