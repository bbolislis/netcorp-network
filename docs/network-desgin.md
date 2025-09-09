# Network Design

## Goals
- Provide a clear, scalable network topology for Netcorp's two branches + hybrid cloud.
- Define IP addressing scheme (IPv4 private ranges) and VLAN segementation.
- Routing plan between the two branches + cloud environment.

---

## Topology
- Core: HQ + Branch interconnected with site-to-site VPN over the Internet.
- HQ: Router/Firewall(pfSense), Core switch, VLANs(Servers, Users, Management, DMZ).
- Branch: Router/Firewall, Access switch, VLANs(Users, Management).
- Cloud: Public cloud VPC with VPN back to HQ.
- Monitoring and Automation servers in HQ.

---

## IP Addressing Plan
| Location | VLAN | Subnet | Purpose |
|----------|------|--------|---------|
| HQ | 10 | 10.10.10.0/24 | User devices |
| HQ | 20 | 10.10.20.0/24 | Servers |
| HQ | 30 | 10.10.30.0/24 | DMZ |
| HQ | 99 | 10.10.99.0/24 | Management |
| Branch | 10 | 10.20.10.0/24 | User devices |
| Branch | 99 | 10.20.99.0/24 | Management |
| Cloud | - | 10.30.0.0/16 | VPC |

---

## Routing Plan
- Use OSPF internally between routers (HQ, Branch, Cloud gateway)
- Default route from Branch -> HQ.
- HQ advertises summary routes to cloud.