# CCNA · Packet Tracer lab portfolio

## Guided labs with screenshot evidence

| Lab | Scenario / troubleshooting | What to inspect |
|---|---|---|
| [L01 · Ethernet LAN](labs/L01-access-port.md) | Disabled access port; save command in the wrong IOS mode | Fault scope, `no shutdown`, privileged EXEC |
| [L02 · Inter-switch uplink](labs/L02-switch-uplink.md) | Removed shared uplink | Both interface states, surviving local branch, MAC paths |
| [L03 · ARP and MAC](labs/L03-mac-arp.md) | Learning reset and relearning | PC ARP versus switch MAC table, known-unicast evidence |
| [L04 · DNS / TCP / HTTP](labs/L04-dns-http.md) | HTTP service disabled while ping still works | UDP/53, TCP SYN-ACK, application recovery |
| [L05 · Client gateway](labs/L05-client-gateway.md) | Wrong local next hop | Local versus remote tests, IP/HTTP recovery |
| [L06 · Layered troubleshooting](labs/L06-layered-troubleshooting.md) | Cable, server return gateway and client DNS | Control tests, unknown-unicast copies, separate repairs |

## Udemy course labs

Course exercises with configuration walkthroughs and troubleshooting notes. Open a lab for its topology, key commands and verification steps.

| Course lab | Subject | Practical focus |
|---|---|---|
| [04](labs/U04-ios.md) | The IOS operating system | Navigate CLI modes, inspect settings and save configuration |
| [11](labs/U11-device-functions.md) | Cisco device functions | Compare interface state, MAC learning and routing tables |
| [12](labs/U12-packet-life.md) | The life of a packet | Follow DNS resolution, ARP and next-hop forwarding |
| [13](labs/U13-troubleshooting-method.md) | Troubleshooting methodology | Isolate interface, resolver and DNS-service faults |
| [14](labs/U14-router-switch-basics.md) | Router and switch basics | Configure management access; inspect CDP, speed and duplex |
| [15](labs/U15-device-management.md) | Device management and recovery | Back up configurations and practise device recovery |
| [16](labs/U16-routing-fundamentals.md) | Routing fundamentals | Choose next hops with connected, static, summary and default routes |
| [17](labs/U17-dynamic-routing.md) | Dynamic routing | Compare route selection and alternate paths after a failure |
| [18](labs/U18-connectivity-troubleshooting.md) | Connectivity troubleshooting | Use reachability tests and route tables to find a missing static route |
| [19.1](labs/U19-1-igp.md) | IGP fundamentals: RIPv2 and EIGRP | Compare learned routes, metrics and administrative distance |
| [20](labs/U20-ospf.md) | OSPF | Understand adjacencies, path costs, summaries and DR/BDR roles |
| [22](labs/U22-vlan-inter-vlan-routing.md) | VLANs and inter-VLAN routing | Connect VLANs through trunks and compare gateway designs |
| [23](labs/U23-dhcp.md) | DHCP | Allocate client addresses and relay requests across subnets |
| [24](labs/U24-hsrp.md) | HSRP gateway redundancy | Set gateway preference and check failover and preemption |
| [25.1](labs/U25-1-stp-troubleshooting.md) | STP troubleshooting | Trace the Layer 2 path and explain its relationship to HSRP |
| [25.2](labs/U25-2-stp-configuration.md) | STP configuration | Place the root bridge and apply Rapid PVST+, PortFast and guards |

## Troubleshooting quick index

| Symptom | Case |
|---|---|
| One client fails; local router still answers | [L01 access port](labs/L01-access-port.md#case-1--one-pc-becomes-unreachable) |
| Configuration save rejected at `>` | [L01 command mode](labs/L01-access-port.md#case-2--configuration-save-rejected) |
| Cross-switch traffic fails; local branch works | [L02 uplink](labs/L02-switch-uplink.md) |
| MAC entries disappear and return | [L03 learning state](labs/L03-mac-arp.md) |
| Ping works; HTTP fails | [L04 service fault](labs/L04-dns-http.md) |
| Local IP works; remote IP fails | [L05 client gateway](labs/L05-client-gateway.md) |
| Server local ping works; remote replies fail | [L06 return gateway](labs/L06-layered-troubleshooting.md#fault-2--wrong-server-return-gateway) |
| IP HTTP works; hostname unresolved | [L06 DNS](labs/L06-layered-troubleshooting.md#fault-3--wrong-client-dns-server) |
| DNS complaint has several underlying causes | [U13 methodology](labs/U13-troubleshooting-method.md) |
| Trace reaches R3; PC3 subnet route missing | [U18 static-route case](labs/U18-connectivity-troubleshooting.md) |
| RIP route changes after EIGRP is introduced | [U19.1 route selection](labs/U19-1-igp.md) |
| Same-VLAN works; cross-VLAN fails | [U22 VLAN and gateway checks](labs/U22-vlan-inter-vlan-routing.md#troubleshooting-map) |
| Clients cannot lease from a server on another subnet | [U23 DHCP relay](labs/U23-dhcp.md#3-move-allocation-to-the-server-subnet) |
| Higher-priority router remains standby | [U24 priority and preemption](labs/U24-hsrp.md#3-make-r1-preferred) |
| Missing OSPF neighbor, default or equal-cost path | [U20 OSPF diagnosis](labs/U20-ospf.md#verification-and-troubleshooting-map) |
| Trace looks correct but the switch path detours | [U25.1 STP path investigation](labs/U25-1-stp-troubleshooting.md) |
| Unexpected root, error-disabled or root-inconsistent port | [U25.2 STP protections](labs/U25-2-stp-configuration.md#verification-and-troubleshooting-map) |

## References and reuse

- [Commands: purpose, mode, example and pitfall](docs/COMMANDS.md)
- [Troubleshooting method and validation checklist](docs/TROUBLESHOOTING.md)
- [Evidence scope and current status](docs/EVIDENCE_POLICY.md)
- [Asset manifest with SHA-256 fingerprints](asset-manifest.json)
- [Attribution and course-material scope](ATTRIBUTION.md)

These are isolated simulator exercises. They document study and practical troubleshooting; they do not assert employment experience or CCNA certification. No IOS binaries, full commercial course books, exam dumps or personal quiz records are included.

