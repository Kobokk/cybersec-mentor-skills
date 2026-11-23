# Cybersec Mentor Skills (`readteamskill` & `blueteamskill`)

Modular AI mentor plugin and skills designed for hands-on cybersecurity learning in local VM labs and legal training platforms. Built with flexible anti-spoiler pedagogy, non-judgmental mistake guidance, automatic skill-level calibration, and four adaptive mentor personas.

## Repository Structure

```text
cybersec-mentor-skills/
├── .codex-plugin/
│   └── plugin.json
├── skills/
│   ├── readteamskill/
│   │   ├── SKILL.md
│   │   └── references/
│   │       ├── 01-recon-and-enumeration.md
│   │       ├── 02-web-exploitation.md
│   │       ├── 03-privilege-escalation.md
│   │       ├── 04-network-and-active-directory.md
│   │       ├── 05-ctf-reversing-and-crypto.md
│   │       └── 06-finding-report-template.md
│   └── blueteamskill/
│       ├── SKILL.md
│       └── references/
│           ├── 01-soc-triage-and-ir-workflow.md
│           ├── 02-log-analysis-and-forensics.md
│           ├── 03-pcap-and-network-hunting.md
│           ├── 04-malware-and-artifact-triage.md
│           ├── 05-detection-rules-and-hardening.md
│           └── 06-incident-report-template.md
├── docs/
│   ├── INSTALLATION.md
│   └── MENTOR-PERSONAS.md
├── LICENSE
└── README.md
```

## Core Features

- **Clean Domain Separation:** `readteamskill` handles offensive lab mentoring (`reconnaissance`, `enumeration`, `exploitation`, `privilege escalation`, `CTF`), while `blueteamskill` handles defensive mentoring (`SOC triage`, `log/PCAP analysis`, `forensics`, `hardening`).
- **Four Adaptive Mentor Personas:** Switches dynamically—or manually via slash commands—between `[PEMBIMBING]`, `[KRITIS]`, `[SOLUSI]`, and `[TEGAS]`.
- **Flexible Anti-Spoiler System:** Starts with directional prompts so you build analytical intuition, but immediately unlocks full commands and walkthroughs whenever you are stuck or request them directly.
- **Language & Level Mirroring:** Adapts automatically to your language, formality, and technical experience level.

## Ethics & Authorized Use

All workflows, simulations, and guidance in this repository are strictly intended for isolated local labs, personal Virtual Machines, or authorized training platforms.
