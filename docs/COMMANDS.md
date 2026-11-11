# Command reference

These examples explain commands used in the documented labs. They are not captured device output. Replace interface names, prefixes and next hops with values from the selected lab. Some commands/options vary by simulated IOS model.

## IOS navigation and persistence

| Command | Mode / purpose | Pitfall |
|---|---|---|
| `enable` | User EXEC `>` → privileged EXEC `#` | A privileged command can fail at `>` |
| `configure terminal` | Privileged EXEC → global configuration | Inspect the resulting prompt |
| `interface fastEthernet 0/2` | Global → selected interface | A correct command on the wrong port changes the wrong link |
| `exit` | Leave one submode | Does not always return directly to EXEC |
| `end` | Return from configuration to privileged EXEC | Run the subsequent `show`/save in its proper context |
| `do show ip route` | Inspect routes from a supported configuration context | Simulator support can vary |
| `copy running-config startup-config` | Save IOS active settings | Accept destination; verify success; `.pkt` saving is separate |
| `show running-config` / `show startup-config` | Inspect active / boot-time settings | Neither proves that every network test passed |

## Ethernet and IPv4

| Command / example | What it shows or changes | What it does not prove |
|---|---|---|
| `show ip interface brief` | IPv4 and interface/line-protocol summary | End-to-end application health |
| `show interfaces status` | Switch port, VLAN, state, speed, duplex | A complete routed path |
| `show interfaces fastEthernet 0/24` | Detailed state and counters | The remote application's service state |
| `show mac address-table dynamic` | Learned MAC → port associations by VLAN | A PC's IPv4 ARP mapping |
| `clear mac address-table dynamic` | Reset dynamic switch learning | Does not clear the PC ARP cache; entries may relearn quickly |
| `shutdown` / `no shutdown` | Administratively disable / enable selected interface | `no shutdown` cannot reconnect a missing cable |
| `ip address 192.0.2.1 255.255.255.0` | Address the selected routed interface | Operational link state or missing remote routes |
| `show arp` | IOS on-link IPv4/MAC mapping | The remote endpoint's MAC across a router |
| `show ip route` | Selected route table | Successful forward and return delivery by itself |
| `show ip route 10.1.2.10` | Lookup matching destination where supported | Reachability of every advertised next hop |
| `ip route 10.1.2.0 255.255.255.0 10.1.1.1` | Static route used in U18 on R3 | No automatic reverse route is created |
| `ip route 0.0.0.0 0.0.0.0 203.0.113.2` | Reference upstream default on U19.1 R4 | No real Internet access is established in the simulator |

## Client and application checks

| Tool / setting | Purpose | Interpretation |
|---|---|---|
| PC `ipconfig` / `ipconfig /all` | Inspect address, mask and supported parameters | Use IP Configuration GUI when an option is unavailable |
| PC `arp -a` | Inspect local IPv4-to-MAC cache | A remote server normally uses the local gateway MAC |
| `ping <IP>` | ICMP request/reply control | Passing ping does not guarantee HTTP or DNS |
| PC `tracert <IP>` / IOS `traceroute <IP>` | Inspect responding path hops | A missing hop response is not automatic proof of a broken forward path |
| `ip name-server 10.10.10.10` | Set an IOS resolver in global configuration | Must be reachable and serve the intended records |
| `ip domain-lookup` | Enable IOS DNS lookup | Does not turn a router into the exercise's DNS server |
| Browser `http://<server-IP>/helloworld.html` | Fresh application test without a hostname lookup | Compare with a fresh name-based request |
| Server Services → HTTP / DNS | Toggle the intended simulator service | Change only one setting per diagnostic experiment |

## Dynamic routing and management

| Command | Purpose / pitfall |
|---|---|
| `show ip protocols` | Verify active process settings, selected networks and passive interfaces |
| `show ip rip database` | Inspect RIP's database separately from installed routes |
| `show ip ospf database` | Inspect OSPF link-state information |
| `show ip eigrp neighbors` | Verify intended EIGRP adjacencies |
| `debug ip rip` → `undebug all` | Observe routing updates in the isolated lab, then stop debugging |
| `router rip` + `version 2` | Configure the exercise's RIPv2 process |
| `router eigrp 100` | Classic EIGRP AS context; align intended peers |
| `router ospf 1` | Local OSPF process context; process ID is not the EIGRP AS |
| `passive-interface <port>` | Protocol-specific behavior: RIP suppresses outgoing updates; EIGRP suppresses hellos/adjacency |
| `show cdp neighbors detail` | Check direct Cisco neighbors; CDP is not an application reachability test |
| `show version`, `show flash` | Inspect actual software/platform and stored files |
| `copy startup-config tftp:` | Export a configuration backup to the lab's TFTP server |

## DHCP and first-hop redundancy

| Command / mode | Purpose | Pitfall |
|---|---|---|
| `ip address dhcp` · interface configuration | Request an address for the router interface | Does not create a client allocation pool |
| `ip dhcp excluded-address <first> <last>` · global configuration | Reserve static infrastructure addresses | Exclusions must match the intended subnet |
| `ip dhcp pool <name>` · global configuration | Enter a DHCP pool | Pool name is a local label |
| `network`, `default-router`, `dns-server` · DHCP pool | Define the client subnet and options | Gateway and DNS are different roles |
| `show ip dhcp pool`, `show ip dhcp binding` · privileged EXEC | Inspect local IOS allocation state | External-server leases are not owned by the relay |
| `ip helper-address <server-IP>` · client-facing interface configuration | Relay DHCP requests to another subnet | Configuring it only on the server-facing interface misses client broadcasts |
| PC `ipconfig /release`, `ipconfig /renew` | Release and request a client lease | Use an isolated working copy for deliberate lease-loss tests |
| `show standby brief`, `show standby` · privileged EXEC | Inspect HSRP roles, group and virtual identity | Configuration intent does not establish the active role |
| `standby <group> ip <virtual-IP>` · interface configuration | Define the shared gateway | Physical router addresses remain distinct |
| `standby <group> priority <value>` · interface configuration | Set election preference | Higher priority alone does not displace a healthy active router |
| `standby <group> preempt` · interface configuration | Allow a higher-priority router to reclaim active | Check delays and forwarding readiness |

See [U23 DHCP](../labs/U23-dhcp.md) and [U24 HSRP](../labs/U24-hsrp.md) for context and evidence limits.

## Three distinctions to remember

1. Route lookup chooses the most specific matching prefix first. AD compares eligible sources for the same prefix; each protocol uses its own metric.
2. The destination IP identifies the remote endpoint; the outgoing Ethernet destination identifies the next hop on that link.
3. DNS resolves names to addresses. ARP resolves on-link IPv4/next-hop MAC mappings. NAT translates network addresses. They are different functions.

See [official references](../ATTRIBUTION.md#technical-references) and the individual case studies for actual evidence and limits.

