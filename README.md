# CCNA · Packet Tracer lab portfolio

**Marcelo da Silva Porfirio** · CCNA studies · Cisco IOS · Routing and switching

A collection of **16 Packet Tracer labs** from my CCNA studies. I use these labs to practise device configuration, understand how traffic moves through a network and troubleshoot connectivity problems.

The lab notes explain the scenarios, commands and solutions, with diagrams and screenshots where available.

## Getting started

1. Choose a lab below and read its objective and topology.
2. Download the corresponding `.pkt` file from `packet-tracer/` and open a working copy in Cisco Packet Tracer.
3. Follow the configuration or troubleshooting steps, run the checks and compare your results with the lab notes.

The collection includes **six guided practice labs** and **ten exercises from my Udemy CCNA course**, completed through **19.1 — IGP Fundamentals**.

## Guided labs with screenshot evidence

| Lab | Scenario / troubleshooting | What to inspect |
|---|---|---|
| [L01 · Ethernet LAN](labs/L01-access-port.md) | Disabled access port; save command in the wrong IOS mode | Fault scope, `no shutdown`, privileged EXEC |
| [L02 · Inter-switch uplink](labs/L02-switch-uplink.md) | Removed shared uplink | Both interface states, surviving local branch, MAC paths |
| [L03 · ARP and MAC](labs/L03-mac-arp.md) | Learning reset and relearning | PC ARP versus switch MAC table, known-unicast evidence |
| [L04 · DNS / TCP / HTTP](labs/L04-dns-http.md) | HTTP service disabled while ping still works | UDP/53, TCP SYN-ACK, application recovery |
| [L05 · Client gateway](labs/L05-client-gateway.md) | Wrong local next hop | Local versus remote tests, IP/HTTP recovery |
| [L06 · Layered troubleshooting](labs/L06-layered-troubleshooting.md) | Cable, server return gateway and client DNS | Control tests, unknown-unicast copies, separate repairs |

## Udemy course labs · completed through 19.1 IGP

The numbering follows the course sections; a section number of 19.1 does not mean nineteen separate lab files were found. **Ten course `.pkt` files** were located through this boundary.

| Course lab | Subject | Completion / evidence |
|---|---|---|
| [04](labs/U04-ios.md) | The IOS operating system | Learner-reported; available course project |
| [11](labs/U11-device-functions.md) | Cisco device functions | Learner-reported; available course project; topology diagram |
| [12](labs/U12-packet-life.md) | The life of a packet: DNS and ARP | Learner-reported; available course project; topology diagram |
| [13](labs/U13-troubleshooting-method.md) | Cisco troubleshooting methodology | Learner-reported; available course project; topology diagram |
| [14](labs/U14-router-switch-basics.md) | Router and switch basics, CDP, speed and duplex | Learner-reported; available course project; topology diagram |
| [15](labs/U15-device-management.md) | Device management, recovery and backups | Learner-reported; available course project; topology diagram |
| [16](labs/U16-routing-fundamentals.md) | Connected, static, summary and default routes | Learner-reported; available course project; topology diagram |
| [17](labs/U17-dynamic-routing.md) | Dynamic routing behavior and failover | Learner-reported; available course project; topology diagram |
| [18](labs/U18-connectivity-troubleshooting.md) | Connectivity troubleshooting: a missing static route | Learner-reported; available course project; topology diagram |
| [19.1](labs/U19-1-igp.md) | 19.1 IGP fundamentals: RIPv2 and EIGRP | Learner-reported; available course project; topology diagram |

Later course sections are not counted as completed. The pending guided L07 is not represented as an executed lab.

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

## References and reuse

- [Commands: purpose, mode, example and pitfall](docs/COMMANDS.md)
- [Troubleshooting method and validation checklist](docs/TROUBLESHOOTING.md)
- [Evidence scope and current status](docs/EVIDENCE_POLICY.md)
- [Asset manifest with SHA-256 fingerprints](asset-manifest.json)
- [Attribution and course-material scope](ATTRIBUTION.md)

These are isolated simulator exercises. They document study and practical troubleshooting; they do not assert employment experience or CCNA certification. No IOS binaries, full commercial course books, exam dumps or personal quiz records are included.
