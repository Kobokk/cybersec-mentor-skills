# Installation & Setup Guide

## 1. Clone the Repository

```bash
git clone [https://github.com/Kobokk/cybersec-mentor-skills.git](https://github.com/Kobokk/cybersec-mentor-skills.git)
cd cybersec-mentor-skills
```

## 2. Using with Agent Skill Frameworks

Copy either or both skill directories (`readteamskill/` and `blueteamskill/`) into your AI agent's skills folder so the agent can discover `SKILL.md` and load `references/` on demand:

```bash
cp -r readteamskill blueteamskill /path/to/your/agent/skills/
```

## 3. Using with System Prompts or Local LLMs

If your AI interface does not support modular skill folders natively:
1. Paste the contents of `readteamskill/SKILL.md` or `blueteamskill/SKILL.md` into your custom instructions or system prompt.
2. Attach or paste the specific file from `references/` matching the topic you are currently practicing.
