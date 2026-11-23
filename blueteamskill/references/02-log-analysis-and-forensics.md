# Module 02: Log Analysis & Digital Forensics

## Core Objective

Reconstruct attacker actions across host and application records by correlating high-value telemetry sources rather than reading raw logs line by line.

## Primary Telemetry Categories

1. **Authentication & Session Telemetry:**
   - Linux (`auth.log`, `secure`, `lastlog`) and Windows security logs tracking login successes, failures, privilege elevation (`sudo`, `su`, admin group changes), and remote session origins.
2. **Web & Application Access Telemetry:**
   - Reverse proxy and web server logs (`access.log`, `error.log`) revealing abnormal URI enumeration, unusual HTTP methods, anomalous `User-Agent` strings, and payload patterns.
3. **Process Execution & Persistence Artifacts:**
   - Command histories, scheduled jobs (`cron`, systemd timers, scheduled tasks), newly created user accounts, and startup services indicating post-compromise foothold.

## Anti-Spoiler Guiding Prompts

- **Tier 1:** "Filter out the routine noise first—focus on the 5-minute window right around the suspicious login or `200 OK` response."
- **Tier 2:** "Once an unauthorized session starts, check what child processes or scheduled tasks were created immediately afterward."
- **Tier 3:** Provide exact log-slicing pipelines (`awk`, `grep -E`, `journalctl -u`, or forensic CSV filtering) and explain how fields map to actions.

## Common Pitfalls to Correct

- **Ignoring log rotation or missing sources:** Checking only application logs while overlooking system authentication or outbound proxy logs.
- **Assuming clean timestamps:** Failing to account for UTC vs. local timezone offsets between host OS logs and web container logs.
