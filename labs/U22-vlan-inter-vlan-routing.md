# U22 · VLANs and inter-VLAN routing

**Completion:** reported by Marcelo on 10 November 2026. **Basis:** the supplied Flackbox exercise reference and his completion statement. No learner `.pkt` project or execution captures were supplied for this addition; the checks below describe what to verify, not newly observed results.

## Objective

Separate Engineering and Sales into VLANs, carry both VLANs between switches, and compare three ways of providing their IPv4 gateways. This connects Layer 2 segmentation to Layer 3 forwarding: a trunk extends a VLAN, while a router or multilayer switch provides a path between different subnets.

## Scenario and addressing

| VLAN | Name / use | IPv4 subnet | Client gateway |
|---|---|---|---|
| 10 | Eng | 10.10.10.0/24 | 10.10.10.1 |
| 20 | Sales | 10.10.20.0/24 | 10.10.20.1 |
| 199 | Native on the inter-switch trunks | No routed subnet specified | Not a client gateway |

Three switches form the switching path: SW1 connects to SW2, which connects to SW3. R1 is used for the external-router alternatives; SW2 provides the gateways for the multilayer-switch alternative.

| Link / ports | Intended function |
|---|---|
| SW1 Gi0/1 ↔ SW2 Gi0/1 | Inter-switch trunk |
| SW2 Gi0/2 ↔ SW3 Gi0/2 | Inter-switch trunk |
| SW1 Fa0/1–2 | Engineering access ports, VLAN 10 |
| SW1 Fa0/3 | Sales access port, VLAN 20 |
| SW3 Fa0/1–2 | Sales access ports, VLAN 20 |
| SW3 Fa0/3 | Engineering access port, VLAN 10 |

These are reference port assignments. Check the actual device model and cabling before applying a command.

## 1. Build and inspect the Layer 2 path

Configure the inter-switch links as explicit trunks and assign each PC port to its intended access VLAN. Use VLAN 199 as the native VLAN on both ends of each inter-switch trunk. This separates the exercise's native VLAN from the user VLANs; it does not by itself enforce access control between routed subnets.

The exercise also compares VTP roles in the domain `Flackbox`:

| Switch | Role | What that means for this exercise |
|---|---|---|
| SW1 | Server | Create the VLAN definitions here for distribution |
| SW2 | Transparent | Maintain its own VLAN database; create the required VLANs locally |
| SW3 | Client | Learn VLAN definitions from the server rather than editing them locally |

VTP does not assign PC ports to VLANs. Those access-port settings still belong on each switch. Transparent mode also does not mean that all received VTP messages are blocked: forwarding depends on VTP version, with received advertisements forwarded over trunks in version 2. Inspect `show vtp status` rather than assuming the simulator's active version.

Before adding routing, test Engineering-to-Engineering and Sales-to-Sales across the switches. A same-VLAN test should use the switching path without a routed gateway.

## 2. Compare the gateway designs

Run these as successive alternatives in a working copy. Reusing a gateway address on multiple active devices would create a conflict.

| Method | Gateway location | SW2 connection | Why compare it? |
|---|---|---|---|
| Separate router interfaces | R1 Fa0/0 for VLAN 10 and Fa0/1 for VLAN 20 | One access link per VLAN | Makes the physical interface cost of each VLAN visible |
| Router-on-a-stick | R1 Fa0/0.10 and Fa0/0.20 | One 802.1Q trunk to R1 Fa0/0 | Uses VLAN tags to share one physical router link |
| Layer 3 switch | SW2 SVI VLAN 10 and SVI VLAN 20 | Gateway resides on SW2 | Moves the routing function onto a routing-capable switch |

### Separate physical interfaces

Each R1 interface has an address in one client subnet. Its SW2 port must be an access port in that same VLAN. Clients use the corresponding .1 address as their default gateway. This design needs two router links for the two user VLANs.

### Router-on-a-stick

Remove the old IP address from the parent Fa0/0 interface before placing the gateway addresses on subinterfaces. Keep the parent interface enabled, match each subinterface's 802.1Q VLAN ID to the intended VLAN, and convert SW2's router-facing port to a trunk.

Representative interface context for VLAN 10:

```text
interface FastEthernet0/0.10
 encapsulation dot1Q 10
 ip address 10.10.10.1 255.255.255.0
```

VLAN 20 needs its own tagged subinterface and gateway address. This excerpt is not a complete device configuration. VLANs 10 and 20 are tagged on this router link; the VLAN 199 native setting above concerns the inter-switch links. If changing a router link's native VLAN, configure its treatment consistently at both ends.

Some switch models require `switchport trunk encapsulation dot1q` before selecting trunk mode; fixed-802.1Q models may not offer that command.

### Multilayer-switch routing

Disable the previous router gateway path before moving the same .1 addresses onto SW2. A routing-capable SW2 needs `ip routing` and an addressed SVI for each user VLAN. For example:

```text
ip routing
interface Vlan10
 ip address 10.10.10.1 255.255.255.0
 no shutdown
```

Repeat the SVI pattern for VLAN 20 using its own subnet. An SVI also needs its VLAN to exist and an active Layer 2 member path for normal operational state. Inspect both interface and line-protocol status. A Layer 2 switch management gateway setting is not a substitute for `ip routing`.

## Verification checklist

The table records expected checks for a repeatable review. It does not assert that output was captured during this repository update.

| Check | Command / test | What to establish |
|---|---|---|
| VLAN membership | `show vlan brief` | VLANs exist and PC access ports are assigned correctly |
| Trunk operation | `show interfaces trunk` | Intended trunks operate; native VLANs agree; user VLANs are carried and forwarding |
| Port mode | `show interfaces <port> switchport` | Administrative and operational mode match the chosen design |
| VTP role | `show vtp status` | Intended domain, mode and version; compare client and server VLAN databases |
| Gateway state | `show ip interface brief` | Required physical interfaces, subinterfaces or SVIs are operational |
| Route availability | `show ip route` | Both client subnets are present on the active routing device |
| Switching baseline | Eng1 → Eng3; Sales1 → Sales3 | Same-VLAN communication across the switching path |
| Inter-VLAN path | Eng1 → Sales1, then reverse | Forward and return communication through the selected gateways |

VTP distributes VLAN definitions, not IP routes. Both client subnets are directly connected to the selected gateway device in this exercise, so an OSPF process is not needed for routing between them.

## Troubleshooting map

| Symptom | Inspect first | Correction when confirmed |
|---|---|---|
| A same-VLAN PC on the other switch is unreachable | Access membership, trunk state, VLAN presence and forwarding | Fix the incorrect port or missing Layer 2 VLAN path |
| SW3 does not learn VLANs | VTP domain/version/mode and intervening trunk path | Align the intended VTP settings; do not assume transparent means off |
| Local VLAN works but the other VLAN fails | Client gateway/mask and the selected routing method | Repair the relevant gateway, tag or routing configuration |
| One router subinterface fails | VLAN ID, parent interface state and SW2 trunk | Match the subinterface tag and carry that VLAN on the trunk |
| An SVI is down | VLAN database, shutdown state and active VLAN members | Restore the intended VLAN/interface and its active Layer 2 path |
| Reachability changes after switching methods | Old router interfaces/subinterfaces and duplicate .1 addresses | Leave only the selected gateway design active |

## Learning focus

The useful distinction is between creating a VLAN, transporting it and routing out of it. Checking those functions separately makes a failed cross-VLAN ping easier to isolate. Routing permits inter-VLAN communication here; restrictive policy would require a separate configuration such as an ACL.

## Sources and evidence

Original study summary based on the Flackbox *22-1 VLAN and Inter-VLAN Routing Configuration* exercise reference supplied on 10 November 2026. The course answer-key PDF is not redistributed, and its screenshots are not presented as learner evidence.

- [Cisco: Understand VLAN Trunk Protocol](https://www.cisco.com/c/en/us/support/docs/lan-switching/vtp/10558-21.html)
- [Cisco: Inter-VLAN routing with an external router](https://www.cisco.com/c/en/us/support/docs/lan-switching/inter-vlan-routing/14976-50.html)

- [Cisco: Inter-VLAN routing with Catalyst switches](https://www.cisco.com/c/en/us/support/docs/lan-switching/inter-vlan-routing/41260-189.html)

[Course attribution](../ATTRIBUTION.md) · [Evidence scope](../docs/EVIDENCE_POLICY.md) · [Command reference](../docs/COMMANDS.md) · [Index](../README.md)
