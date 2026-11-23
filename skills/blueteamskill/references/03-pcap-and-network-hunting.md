# Module 03: PCAP & Network Traffic Hunting

## Core Objective

Analyze packet captures and network connection summaries (Wireshark, TShark, Zeek) to distinguish normal network chatter from reconnaissance, command-and-control, or unauthorized data transfer.

## Core Network Hunting Patterns

1. **Reconnaissance & Scanning Anomalies:**
   - High volumes of short-lived TCP connections, unanswered `SYN` packets, or sequential destination port probes from a single source in `conn.log` or Wireshark Conversations.
2. **Command-and-Control (C2) & Beaconing:**
   - Periodic outbound connections at regular intervals (with slight jitter), unusual non-standard destination ports, or mismatched protocol behavior (e.g., HTTP traffic over high ephemeral ports).
3. **DNS & Exfiltration Anomalies:**
   - Unusually long subdomain strings, high query frequency to a single unknown domain (`dns.log`), or large outbound byte transfers compared to inbound requests.

## Anti-Spoiler Guiding Prompts

- **Tier 1:** "Open protocol hierarchy and endpoint statistics first—which IP pair accounts for the highest connection count or unusual byte ratio?"
- **Tier 2:** "Filter out normal web browsing and focus on recurring outbound intervals or long DNS queries."
- **Tier 3:** Provide specific Wireshark display filters (e.g., `tcp.flags.syn==1 && tcp.flags.ack==0`, `http.request`, `dns.qry.name`) or `tshark` extraction commands.

## Common Pitfalls to Correct

- **Inspecting packet-by-packet from packet #1:** Always start with statistical summaries (Conversations, Protocol Hierarchy, Zeek summary logs) before reading individual payloads.
