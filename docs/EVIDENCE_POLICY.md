# Evidence scope

Repository assembled on 5 November 2026 from the current local lab material and Marcelo's explicit report of course completion through 19.1 IGP.

| Collection | What is established | Limits |
|---|---|---|
| L01 / L02 | Reviewed learner baseline, fault and recovery captures | Some individual source/status lines cropped; case pages identify limits |
| L03 | ARP mappings, peer connectivity, known-unicast and relearning | Initial flooding not shown in L03; equivalent later observation is in L06 |
| L04 | DNS UDP query, server SYN-ACK, HTTP-only failure and recovery | Not all handshake headers or a TCP RST header were inspected |
| L05 | Wrong client gateway isolation and restoration | Some sources attributed from the capture sequence; no .254 ARP packet capture |
| L06 | Baseline, unknown-unicast egress copies, three faults and operational recovery | No detailed DNS-header/cache audit; concepts completed with guided review |
| L10 | Baseline, one-setting IPv6 gateway fault, return-path explanation and eight successful recovery checks reviewed on 15 November 2026; three selected screenshots and three completion-review project snapshots | Guided completion; project internals not independently inspected or rerun; selected captures illustrate part of the reviewed test set |
| Udemy 04, 11–18 and 19.1 | Completion stated by Marcelo; ten local course projects and nine topology diagrams found | No separate learner screenshots or independently verified final configurations in this course folder |
| Udemy 22 | Completion reported by Marcelo on 10 November 2026; supplied exercise reference reviewed | Documentation only in this addition; no learner `.pkt`, device outputs or execution captures supplied |
| Udemy 23 / 24 | Completion confirmed by Marcelo on 11 November 2026; two saved `.pkt` files identified by him as his completed versions; original study summaries and file fingerprints added | No independent full rerun, new lease/role transcripts or measured failover timing; checks describe expected verification |
| Udemy 20 / 25.1 / 25.2 | Completion reported by Marcelo on 13 November 2026; three supplied saved `.pkt` projects, selected course diagrams, original study notes and fingerprints | No independent simulator rerun, device-state transcripts, measured convergence or new fault/recovery captures; paths and checks are labeled reference/expected behavior |
| Udemy 26.1 | Publication requested on 16 November 2026; supplied EtherChannel exercise/reference answers inspected; one project and two reference diagrams preserved | Configuration and diagnosis examples are reference procedures; no fresh rerun, measured bandwidth/failover or learner CLI captures accompany this addition |

Lab 20 (OSPF) was left out pending a repeat on 10 November 2026. Marcelo's 13 November request identifies it and labs 25.1/25.2 as completed for publication, superseding that pending status. Only listed sections are included; gaps in course numbering do not imply completion.

## Interpretation rules

- A saved project proves a file exists. Its filename or timestamp alone does not prove a particular configuration, a clean final result or the original sequence of actions.
- The guided narratives combine reviewed observations with explanatory reproduction commands. They do not claim a fresh rerun of the guided labs during repository preparation.
- Udemy solutions are original explanatory summaries of inspected course exercises and reference answers. They are labeled as procedures/reference diagnoses, not verbatim learner transcripts.
- Byte-identical course topology diagrams are stored once and shared between the relevant pages. They illustrate intended layouts. They are not before/after execution screenshots.
- Earlier empty submission templates and older partial reviews were superseded by later observations where available. They were not copied as current completion statements.
- Selected original asset bytes are preserved and fingerprinted in [asset-manifest.json](../asset-manifest.json). Renamed Udemy files retain their original source names in that manifest.
- Written quizzes, answer keys, grades, personal schedules, local account paths and unrelated documents are outside this repository's purpose.

The lab pages explain practical evidence, rather than certifying independent unseen mastery or completion of the full CCNA syllabus. Future labs should be added with the same distinction between reported completion, observed execution and expected behavior.
