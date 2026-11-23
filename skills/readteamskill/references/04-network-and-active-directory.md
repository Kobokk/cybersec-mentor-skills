# Module 04: Internal Network Pivoting & Active Directory

## Core Objective

Navigate segmented internal networks after compromising an initial host, map Active Directory (AD) trust and permission paths, and move laterally toward high-value targets.

## Part A: Pivoting & Tunneling

1. **Identify Dual-Homed Hosts:** Check routing tables (`ip route` / `route print`) and ARP caches (`arp -a`) to spot internal subnets unreachable from the attacker machine.
2. **Select Tunneling Strategy:**
   - **Local Port Forwarding (`ssh -L`):** Forward a single specific internal port (e.g., internal RDP `3389` or web `8080`) to the attacker machine.
   - **Dynamic SOCKS Proxy (`ssh -D` or Chisel/Ligolo):** Route multiple tools (`proxychains`) through the compromised pivot host to scan and interact with an entire internal subnet.

## Part B: Active Directory Attack Methodology

1. **Domain Enumeration (Situational Awareness):**
   - Identify Domain Controllers, domain functional level, password policies (lockout threshold before spraying!), users, groups, SPNs, and GPOs.
2. **Credential & Kerberos Attacks:**
   - **AS-REP Roasting:** Target accounts with Kerberos pre-authentication disabled to capture crackable TGT hashes offline.
   - **Kerberoasting:** Request TGS tickets for service accounts with Service Principal Names (SPNs) and crack them offline.
   - **Password Spraying:** Test a single common password across many valid usernames while strictly respecting the domain lockout policy.
3. **Lateral Movement & ACL Abuse:**
   - **Pass-the-Hash (PtH) / Pass-the-Ticket (PtT):** Reuse NTLM hashes or Kerberos tickets over SMB, WinRM, or WMI without needing plaintext passwords.
   - **Relay & Poisoning:** Exploit LLMNR/NBT-NS or unsigned SMB traffic in lab segments to relay authentication.
   - **ACL / ACE Misconfigurations:** Trace indirect control paths (`GenericAll`, `WriteDacl`, `ForceChangePassword`) using graph-based analysis (BloodHound concepts).

## Anti-Spoiler Guiding Prompts

- **Tier 1:** "Before trying any password spray in AD, which domain policy number must you check first so you don't lock out every account in the lab?"
- **Tier 2:** "Your compromised host has two network interfaces (`192.168.56.x` and `10.10.20.x`). How can you route traffic from your attacker VM through this host?"
- **Tier 3:** Walk through the exact tunnel setup or Kerberos request command and explain the protocol handshake.

