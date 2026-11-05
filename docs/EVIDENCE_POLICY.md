# Evidence scope

Repository assembled on 5 November 2026 from the current local lab material and Marcelo's explicit report of course completion through 19.1 IGP.

| Collection | What is established | Limits |
|---|---|---|
| L01 / L02 | Reviewed learner baseline, fault and recovery captures | Some individual source/status lines cropped; case pages identify limits |
| L03 | ARP mappings, peer connectivity, known-unicast and relearning | Initial flooding not shown in L03; equivalent later observation is in L06 |
| L04 | DNS UDP query, server SYN-ACK, HTTP-only failure and recovery | Not all handshake headers or a TCP RST header were inspected |
| L05 | Wrong client gateway isolation and restoration | Some sources attributed from the capture sequence; no .254 ARP packet capture |
| L06 | Baseline, unknown-unicast egress copies, three faults and operational recovery | No detailed DNS-header/cache audit; concepts completed with guided review |
| Udemy 04, 11–18 and 19.1 | Completion stated by Marcelo; ten local course projects and nine topology diagrams found | No separate learner screenshots or independently verified final configurations in this course folder |

## Interpretation rules

- A saved project proves a file exists. Its filename or timestamp alone does not prove a particular configuration, a clean final result or the original sequence of actions.
- The guided narratives combine reviewed observations with explanatory reproduction commands. They do not claim a fresh rerun of the six labs during repository preparation.
- Udemy solutions are original explanatory summaries of inspected course exercises and reference answers. They are labeled as procedures/reference diagnoses, not verbatim learner transcripts.
- Byte-identical course topology diagrams are stored once and shared between the relevant pages. They illustrate intended layouts. They are not before/after execution screenshots.
- Earlier empty submission templates and older partial reviews were superseded by later observations where available. They were not copied as current completion statements.
- Selected original asset bytes are preserved and fingerprinted in [asset-manifest.json](../asset-manifest.json). Renamed Udemy files retain their original source names in that manifest.
- Written quizzes, answer keys, grades, personal schedules, local account paths and unrelated documents are outside this repository's purpose.

The lab pages explain practical evidence, rather than certifying independent unseen mastery or completion of the full CCNA syllabus. Future labs should be added with the same distinction between reported completion, observed execution and expected behavior.
