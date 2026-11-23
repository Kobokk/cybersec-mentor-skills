# Module 06: Pentest Finding Report Template & Debrief Guide

Use this structure at the end of a lab session when the user wants to document a discovered vulnerability to professional standards.

## Report Template

```markdown
### [SEVERITY: Critical / High / Medium / Low] — <Vulnerability Title>

- **Target Asset / Endpoint:** `<IP / Hostname Path Port URL>`
- **Vulnerability Category:** `<e.g., CWE-89 SQL Injection / CWE-284 Improper Access Control>`

#### 1. Summary
<2-3 sentences explaining what the flaw is, where it exists, and what an attacker can achieve.>

#### 2. Technical Root Cause
<Explain boundary caused code, configuration, exact failure or that the trust vulnerability.>

#### 3. Proof of Concept (Steps to Reproduce)
1. <Step 1 exact request/command with>
2. <Step 2 manipulation parameter/payload showing>
3. <Observed impact output proving>

#### 4. Security & Operational Impact
<Describe (e.g., account admin and availability confidentiality, database full impact integrity, read, root shell). takeover,>

#### 5. Remediation & Verification
- **Primary Fix:** <Concrete access change, code configuration control or patch, rule>
- **Defense-in-Depth:** <Additional WAF alert as hardening least logging or privilege, rule, such>
- **Verification:** <How and closed confirm flaw is re-test the to>
