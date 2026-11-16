# Attribution and references

## Portfolio material

The seven guided case studies document Marcelo da Silva Porfirio's Packet Tracer learning work and original device screenshots from October–November 2026. The repository prose organizes those observations and explains the commands. The source study workspace remains separate; no study-progress state was reset or changed.

## Udemy / Flackbox course material

The sixteen course-associated `.pkt` projects and selected topology images were supplied in Marcelo's local `CCNA_Udemy` course folder. Titles and instructional content identify Flackbox course material. Their original authorship and any applicable course terms remain with their respective creators; no repository-wide open-source licence is applied to third-party assets.

The lab pages are original summaries and explanations. Full course PDFs, answer keys and IOS binaries are not included. Course completion through lab 19.1 was reported by Marcelo on 5 November 2026. Source filenames are recorded in the asset manifest so the course material is not presented as independently designed portfolio topology art.

On 10 November 2026, lab 22 was added as an original study summary based on the supplied Flackbox VLAN/inter-VLAN routing exercise reference and Marcelo's completion statement. Its answer-key PDF and reference screenshots are not redistributed. No learner project or execution screenshots were supplied for this addition. At that date, lab 20 (OSPF) was left out pending a repeat; its subsequent inclusion is recorded below.

On 11 November 2026, labs 23 (DHCP) and 24 (HSRP) were added with original study explanations and the two course-folder `.pkt` files Marcelo identified as his completed versions. Their course-derived topology remains attributed to Flackbox; learner completion is reported rather than independently retested. No course PDFs, answer keys or reference configuration bundles were added. File fingerprints preserve the exact supplied bytes.

On 13 November 2026, labs 20 (OSPF), 25.1 (STP Troubleshooting) and 25.2 (STP Configuration v1.1) were added following Marcelo's completion/publication request. The three supplied projects are preserved byte-for-byte, with original study explanations and selected course topology images. Identical diagrams are shared rather than duplicated. No fresh execution transcripts, independently verified final configurations, course PDFs, answer keys or reference configuration bundles accompany these additions.

On 16 November 2026, U26.1 (EtherChannel) was added from the supplied Flackbox course exercise, together with one `.pkt` and two distinct reference topology images. The walkthrough covers LACP, PAgP, static bundles and routed port channels with OSPF. It does not claim a fresh simulator run or captured learner CLI output. Full course PDFs, answer keys and configuration bundles remain excluded.

The same update added guided case L10, completed on 15 November 2026 after reviewed dual-stack baseline, IPv6-gateway fault and recovery evidence. Three learner screenshots and three project snapshots associated with the final review are included. Original private assessments, answers and schedules remain outside the public repository.

Cisco, CCNA, IOS and Packet Tracer are trademarks of their respective owners. This is a personal study archive and is not an official Cisco course or endorsement.

## Technical references

Official documentation checked while assembling the explanations on 5 November 2026:

- [Cisco: Unicast Flooding in Switched Campus Networks](https://www.cisco.com/c/en/us/support/docs/switches/catalyst-6000-series-switches/23563-143.html) — unknown-destination forwarding within a VLAN.
- [Cisco: Catalyst 2960 administration and address tables](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst2960/software/release/15-2_1_e/configuration/guide/2960_scg/swadmin.html) — dynamic table inspection and clearing.
- [Cisco: Catalyst 2960 interface and show commands](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst2960/software/release/15-2_3_e/command/reference/cr_2960/cli2.html) — interface state and MAC table commands; actual simulator support varies.
- [Cisco: Troubleshooting TCP/IP](https://www.cisco.com/en/US/docs/internetworking/troubleshooting/guide/tr1907.html) — local/remote reachability, configuration and DNS checks. This is a legacy reference, used for stable diagnostic principles rather than current product/version guidance.

Reference explanations are paraphrased. Actual simulated results are attributed to the individual screenshot evidence or clearly labeled learner reports.


Additional primary references checked for the 13 November 2026 additions are linked in [U20](labs/U20-ospf.md), [U25.1](labs/U25-1-stp-troubleshooting.md) and [U25.2](labs/U25-2-stp-configuration.md). These cover OSPF election/neighbor behavior and Cisco spanning-tree configuration and protections.
