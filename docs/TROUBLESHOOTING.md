# Troubleshooting workflow

## Repeatable method

1. Define the affected source, destination and application. Record what still works.
2. Capture the baseline addressing, interface state, selected route and relevant services.
3. Compare physical/link, local IP, remote IP, name resolution and application tests as needed.
4. Form a cause that explains both the failed test and the successful control.
5. Change one confirmed item. Preserve the failed state and the exact correction.
6. Repeat the original failing test and the successful controls; check both directions when relevant.
7. Save the recovered project/configuration, and state remaining evidence limits.

## Symptom-to-test map

| Symptom | First comparisons | Possible cause to confirm |
|---|---|---|
| One client missing, other branches work | Access link and port state | Disabled port or disconnected cable |
| Devices behind another switch fail | Both uplink ends and local branch | Shared uplink failure |
| Local gateway IP responds, remote IP fails | Client gateway, destination route, server return gateway | Wrong next hop or missing route |
| Numeric IP and HTTP work, name fails | Resolver setting, service/record and fresh-name request | DNS-specific problem |
| Ping works, fresh direct-IP HTTP fails | Server HTTP service and transport/application behavior | Service failure |
| `Invalid input` | IOS mode, spelling and `?` | Command entered in wrong context or unsupported syntax |

These are hypotheses, not automatic diagnoses. A cache hit, old browser page, cropped source label or route table alone can be insufficient evidence.

## Record each result

| Field | Example |
|---|---|
| Source and destination | PC-A → SRV6 198.51.100.10 |
| Test | `ping 198.51.100.10` |
| Observed result | 0/4, not an expected-output template |
| Control | Local router 4/4 |
| Changed item | SRV6 default gateway .14 → .9 |
| Recovery | Remote ping, reverse ping, direct-IP HTTP and named HTTP |
| Limitation | No packet-level capture of attempted server ARP |

## Saving and rollback

Use different baseline/fault/recovered `.pkt` filenames. IOS `copy running-config startup-config` and Packet Tracer File → Save As solve different persistence needs. Reopen the baseline or undo the one intended fault; inspect dynamic state after reopening rather than assuming it is identical.
