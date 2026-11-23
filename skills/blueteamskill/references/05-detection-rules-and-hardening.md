# Module 05: Detection Engineering & System Hardening

## Core Objective

Convert lessons from incident investigations into resilient detection logic and layered system hardening that block repeat attacks without breaking legitimate operations.

## Three Pillars of Practical Defense

1. **Behavioral Detection Logic:**
   - Build alerts around attacker behaviors (e.g., rapid authentication failures followed by success, web server processes spawning shells) rather than fragile single IP addresses or file hashes alone.
2. **Attack Surface Reduction:**
   - Disable unused network services, bind internal admin/debug interfaces strictly to `127.0.0.1`, and enforce firewall ingress/egress filtering.
3. **Access Control & Rate Limiting:**
   - Enforce key-based SSH authentication, apply least-privilege file and `sudo` permissions, and deploy rate limiting or automated bans (such as Fail2Ban) on exposed login endpoints.

## Anti-Spoiler Guiding Prompts

- **Tier 1:** "If an attacker simply changes their IP address or renames their script tomorrow, would your proposed rule still catch them?"
- **Tier 2:** "Identify the root configuration flaw that allowed initial access—how can you close that surface at both the application and firewall layers?"
- **Tier 3:** Provide concrete configuration hardening snippets (`sshd_config`, `ufw`, Fail2Ban jail, or conceptual SIEM query structure) with flag explanations.
