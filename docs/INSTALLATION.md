# Installation & Setup Guide

## 1. Install as a Plugin (ChatGPT / Codex / Claude)

1. Download the repository ZIP or package the root directory so `.codex-plugin/plugin.json` and `skills/*/SKILL.md` sit at the archive root.
2. Upload the `.zip` archive in your platform's **Plugins / Skills** uploader, or add via CLI:

```bash
codex plugin marketplace add Kobokk/cybersec-mentor-skills
```

## 2. Clone for Manual Skill Setup

```bash
git clone [https://github.com/Kobokk/cybersec-mentor-skills.git](https://github.com/Kobokk/cybersec-mentor-skills.git)
cd cybersec-mentor-skills
cp -r skills/readteamskill skills/blueteamskill /path/to/your/agent/skills/
```
