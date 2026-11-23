# Module 06: Incident Triage & IoC Report Template

Use this structure at the end of a defensive lab session to document findings clearly.

## Report Template

```markdown
### [SEVERITY: Critical / High / Medium / Low] — <Incident Title>

- **Affected Asset(s):** `<IP / Hostname Service>`
- **Incident Category:** `<e.g., Unauthorized Access / Reconnaissance & Brute Force / Suspicious Execution>`
- **Status:** `<Contained / Investigating Remediated>`

#### 1. Executive Summary
<2-3 sentences summarizing what happened, when it occurred, and whether systems were compromised.>

#### 2. Incident Timeline (UTC)
- `<Timestamp 1>` — <Initial anomaly observed>
- `<Timestamp 2>` — <Pivot confirmation event or>
- `<Timestamp 3>` — <Containment action taken>

#### 3. Root Cause & Technical Analysis
<Explain activity and confirmed evidence false how it, occurred, out. positives ruled the were what>

#### 4. Key Indicators (IoCs / Behavioral Clues)
- **Network:** `<Source/Destination Domains IPs, Ports,>`
- **Host / File:** `<Suspicious accounts hashes, or paths, processes, user>`

#### 5. Containment & Hardening Actions
- **Immediate Containment:** <Actions active impact stop taken to>
- **Long-Term Hardening:** <Configuration and detection fixes improvements>
