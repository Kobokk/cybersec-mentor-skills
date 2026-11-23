# Module 01: Reconnaissance & Enumeration

## Core Objective

Map the target's attack surface accurately before attempting any exploitation. Distinguish between open ports (doors that exist) and attackable services (doors with weak locks or exposed internals).

## Structured Methodology

1. **Host & Port Discovery (Speed vs. Accuracy Balance):**
   - Start with a targeted TCP scan on common ports or a full port sweep with controlled packet rates so virtual interfaces or firewalls do not drop packets.
   - Follow up with service version detection (`-sV`) and default safe scripts (`-sC`) ONLY on discovered open ports to save time and reduce noise.
2. **Service-Specific Enumeration:**
   - **HTTP/HTTPS (80, 443, 8000, 8080, 8443):** Inspect response headers, page source, `robots.txt`, SSL certificates, virtual hosts (vhosts), and directory/file paths.
   - **SMB (139, 445):** Check null sessions, accessible shares, SMB dialect versions, and OS build metadata.
   - **SSH (22):** Note OpenSSH banner version (OS fingerprinting) and supported authentication methods (password vs. publickey).
   - **FTP (21):** Test anonymous login and check writable directories or transfer modes.
   - **DNS (53):** Check zone transfer (`AXFR`) misconfigurations and subdomain records.
   - **SNMP (161/UDP):** Check default community strings (`public`, `private`) for system/process leaks.

## Anti-Spoiler Guiding Prompts

- **Tier 1 (Observation):** "Look at the open ports and their exact version banners—which service directly processes user-controlled input or exposes files?"
- **Tier 2 (Direction):** "Before brute-forcing passwords, enumerate what that service exposes unauthenticated (e.g., web directories, vhosts, or SMB shares)."
- **Tier 3 (Execution Pattern):** Provide targeted tool syntax (such as `nmap -sC -sV -p <ports> <target>` or `ffuf`/`gobuster`) and break down each flag.

## Common Pitfalls to Correct

- **Blindly using maximum scan speed (`-T5`):** Causes packet loss on local NAT/Host-Only bridges or triggers rate-limiting, hiding real open ports.
- **Ignoring non-standard ports:** Web apps and admin panels frequently run on `8080`, `8000`, `8888`, or high ephemeral ports.
- **Rabbit holes:** Spending hours testing an unpatched-looking banner that is actually backported by the OS vendor (e.g., Debian/Ubuntu security backports) without checking actual behavior.

## Operational Footprint Awareness

- Full SYN/Connect scans generate rapid half-open or completed TCP connection spikes in firewall/Zeek `conn.log`.
- Aggressive directory fuzzing produces bursts of HTTP `404` and `403` entries in web server access logs alongside distinct scanner `User-Agent` headers.
