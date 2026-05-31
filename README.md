# ICS Network Traffic Analysis with Malcolm — 4SICS Geek Lounge Dataset

A self-directed learning project: deploying CISA's **Malcolm** network analysis
suite from scratch and using it to investigate three days of real ICS attack
traffic from the 4SICS "Geek Lounge" conference lab.

> ⚠️ Public training dataset (Netresec). The "attackers" were authorized
> conference participants attacking demonstration equipment — not a real incident.

## What this project covers
- Deploying Malcolm (Zeek + Suricata + Arkime + OpenSearch) on an Ubuntu VM
- Ingesting and analyzing three PCAPs (25 MB / 134 MB / 200 MB)
- Tracing a complete ICS attack across three days
- Producing an evidence-backed report with explicit confidence levels

## The three-day story
| Day | Phase | Key finding |
|-----|-------|-------------|
| 1 (151020) | Baseline | Normal operations + benign noise; no attackers |
| 2 (151021) | Reconnaissance | Web scanning + Modbus/S7comm fingerprinting; **no writes** |
| 3 (151022) | Manipulation | Modbus attack with ~10,584 acknowledged coil-writes |

## Key lesson
The unfiltered data initially suggested an attacker wrote to the Siemens PLC.
Filtering by source IP corrected this — the writes were legitimate, and the
attacker had only made failed connection attempts. **Verify source attribution
before drawing conclusions.**

## Tools & skills
`Malcolm` `Zeek` `Suricata` `Arkime` `OpenSearch` · Modbus / S7comm / DNP3 ·
passive asset identification · alert triage · network forensics

## Full report
See [`/report`](./report) for the complete writeup (setup → methodology →
all three days → findings → recommendations).

## Dataset
[4SICS Geek Lounge captures](https://www.netresec.com/?page=PCAP4SICS) — Netresec
