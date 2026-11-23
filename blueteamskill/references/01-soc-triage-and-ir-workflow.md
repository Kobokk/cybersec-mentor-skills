# Module 01: SOC Triage & Incident Response Workflow

## Core Objective

Validate alerts accurately using multi-source evidence before triggering disruptive containment, following the standard Incident Response lifecycle (`Preparation -> Identification -> Containment -> Eradication -> Recovery -> Lessons Learned`).

## Structured Triage Methodology

1. **Baseline & Context Validation:**
   - Verify timezone and clock synchronization across log sources before building a timeline.
   - Identify source and destination asset roles (internal scanner, admin workstation, public-facing server, or unknown host).
2. **Outcome Ratio Analysis:**
   - Separate noisy failed attempts (HTTP `403`/`404`, failed logins) from pivot events where an action succeeded (`200 OK` on restricted paths, successful authentication after brute-force bursts).
3. **Evidence Preservation Before Containment:**
   - Capture volatile state (active connections, running processes, memory/PCAP snapshots) before rebooting or wiping a compromised lab VM.

## Anti-Spoiler Guiding Prompts

- **Tier 1 (Observation):** "Look at the timestamps and source IP first—does this activity belong to a scheduled admin task, or is it unexpected?"
- **Tier 2 (Direction):** "You see hundreds of failed requests, but check the end of that sequence—did any single request succeed or trigger a new outbound connection?"
- **Tier 3 (Execution Pattern):** Provide targeted filtering commands (`grep`, `awk`, `jq`, or journalctl queries) and explain each filter condition.

## Common Pitfalls to Correct

- **Escalating from a single log line:** Treating isolated port scans or automated internet noise as a full system breach without checking post-access execution.
- **Destroying volatile evidence:** Restarting services immediately during containment, erasing active process and network socket clues.
