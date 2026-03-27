# ⬡ Agency Skills Registry

> The universal registry for AI skills, agent personas, MCP servers & workflows — across every LLM platform.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Skills](https://img.shields.io/badge/Skills-25+-blue)](./skills)
[![Agents](https://img.shields.io/badge/Agents-10+-purple)](./agents)
[![Arabic](https://img.shields.io/badge/Arabic-Native%20Support-green)](./skills/arabic)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](./CONTRIBUTING.md)

---

## What Is This?

**Agency Skills Registry** is the single source of truth for AI agent skills, personas, MCP servers, and workflows — across Claude, GPT-4, Gemini, Qwen, Cursor, Codex CLI, JAIS, Falcon, and ALLaM.

Think of it as **npm for AI skills** — a curated, verified, security-scored collection that any LLM agent can reference, install, and compose.

This registry powers [SkillForge](https://github.com/salmandev/skillforge) — the web platform that makes every skill here searchable, filterable, and installable.

---

## Why This Exists

Every developer building AI agents today faces the same problem:

- Skills are scattered across dozens of GitHub repos with no standard format
- There is no cross-platform compatibility information
- No security scanning for prompt injection or data exfiltration
- Arabic and MENA skills are essentially nonexistent
- Prompt keywords — the phrases that *trigger* a skill — are never documented

This registry fixes all of that.

---

## Registry Structure

```
agency-skills-registry/
├── skills/
│   ├── devops/
│   ├── edtech/
│   ├── security/
│   ├── productivity/
│   ├── iam/
│   ├── data/
│   ├── ai-ml/
│   └── arabic/                        # MENA-native skills
├── agents/                            # Agent persona templates (SOUL.md)
├── workflows/                         # Composed multi-skill chains
├── mcp-servers/                       # MCP server registry entries
├── keywords/
│   └── index.json                     # Trigger keyword → skill mapping
├── tools/
│   ├── validate-skill.js              # Validate SKILL.md format
│   └── submit-to-skillforge.js        # Push to SkillForge API
├── CONTRIBUTING.md
├── SKILL_TEMPLATE.md
└── AGENT_TEMPLATE.md
```

---

## Skill Format

Every skill follows the standard `SKILL.md` format with registry extensions:

```markdown
---
name: skill-slug
description: One sentence description
category: devops | edtech | security | productivity | iam | data | ai-ml | other
tags: [tag1, tag2]
trigger_keywords:
  - "phrase that activates this skill"
  - "another trigger phrase"
platform_claude: true
platform_gpt: true
platform_gemini: false
platform_qwen: true
platform_cursor: true
platform_codex: true
platform_jais: false
platform_falcon: false
platform_allam: false
language: en                           # en | ar | bilingual
security_score: 95                     # 0-100, auto-scanned
verified: false
version: 1.0.0
author: github-username
install_cmd: npx agency-agents-cli install skill-slug
---

## Purpose
...

## When to Use
...

## Instructions
...

## Trigger Keywords
...

## Example
...
```

---

## Current Registry

### Skills (25)

| Skill | Category | Platforms | Security | Lang |
|-------|----------|-----------|----------|------|
| [docx](./skills/productivity/docx/) | Productivity | Claude, Cursor | 97 | EN |
| [pdf](./skills/productivity/pdf/) | Productivity | All | 95 | EN |
| [pptx](./skills/productivity/pptx/) | Productivity | Claude, Cursor | 96 | EN |
| [xlsx](./skills/productivity/xlsx/) | Productivity | All | 95 | EN |
| [github-actions](./skills/devops/github-actions/) | DevOps | Claude, GPT, Gemini | 92 | EN |
| [docker-compose](./skills/devops/docker-compose/) | DevOps | All | 90 | EN |
| [terraform-plan](./skills/devops/terraform-plan/) | DevOps | All | 91 | EN |
| [supabase-rls](./skills/devops/supabase-rls/) | DevOps | Claude, Cursor | 94 | EN |
| [api-design](./skills/devops/api-design/) | DevOps | All | 93 | EN |
| [code-review](./skills/devops/code-review/) | DevOps | All | 96 | EN |
| [test-generation](./skills/devops/test-generation/) | DevOps | All | 94 | EN |
| [security-audit](./skills/security/security-audit/) | Security | All | 98 | EN |
| [nca-ecc-compliance](./skills/security/nca-ecc-compliance/) | Security | Claude, GPT | 97 | EN/AR |
| [iam-policy](./skills/security/iam-policy/) | Security | Claude, GPT | 95 | EN |
| [sql-query](./skills/data/sql-query/) | Data | All | 93 | EN |
| [data-cleaning](./skills/data/data-cleaning/) | Data | All | 92 | EN |
| [react-component](./skills/ai-ml/react-component/) | AI/ML | All | 94 | EN |
| [prompt-optimizer](./skills/ai-ml/prompt-optimizer/) | AI/ML | All | 96 | EN |
| [resume-builder](./skills/productivity/resume-builder/) | Productivity | All | 95 | EN |
| [email-drafter](./skills/productivity/email-drafter/) | Productivity | All | 96 | EN |
| [log-analyzer](./skills/devops/log-analyzer/) | DevOps | All | 91 | EN |
| [arabic-email-drafter](./skills/arabic/arabic-email-drafter/) | Productivity | Claude, GPT, JAIS | 97 | AR |
| [arabic-content](./skills/arabic/arabic-content/) | Productivity | Claude, GPT | 95 | AR |
| [mdcat-quiz](./skills/edtech/mdcat-quiz/) | EdTech | Claude, GPT | 94 | EN |
| [physics-simulator](./skills/edtech/physics-simulator/) | EdTech | Claude, GPT | 93 | EN |

### Agents (coming in v0.2)
### Workflows (coming in v0.2)
### MCP Servers (coming in v0.2)

---

## Install Any Skill

Via [agency-agents-cli](https://www.npmjs.com/package/agency-agents-cli):

```bash
# Install a single skill
npx agency-agents-cli install docx

# Install all Arabic skills
npx agency-agents-cli install --lang ar

# Install all security skills
npx agency-agents-cli install --category security

# Search skills by keyword
npx agency-agents-cli search "create pdf"
```

Or reference directly in your agent system prompt:
```
Use the skill at: https://raw.githubusercontent.com/salmandev/agency-skills-registry/main/skills/productivity/docx/SKILL.md
```

---

## Keyword Index

The `keywords/index.json` file maps natural language phrases to skills — the first trigger keyword taxonomy for AI agent skills.

```json
{
  "create word document": ["docx"],
  "write pdf report": ["pdf"],
  "deploy with docker": ["docker-compose"],
  "saudi compliance": ["nca-ecc-compliance"],
  "اكتب بريد إلكتروني": ["arabic-email-drafter"],
  "مراجعة الأمن السيبراني": ["nca-ecc-compliance", "security-audit"]
}
```

This powers the semantic search in [SkillForge](https://github.com/salmandev/skillforge).

---

## Arabic & MENA Skills

This registry includes a dedicated Arabic skills collection — the first of its kind.

Arabic skills live in `skills/arabic/` and are also maintained in the companion repository:
**[arabic-skills-library](https://github.com/salmandev/arabic-skills-library)**

Current Arabic coverage:
- ✅ Business communication (MSA formal style)
- ✅ NCA ECC compliance (Saudi cybersecurity framework)
- 🔄 SAMA CSF (in progress)
- 🔄 Arabic medical documentation (in progress)
- 🔄 Saudi/Egyptian curriculum skills (in progress)
- 🔄 Gulf dialect variants (in progress)

---

## Security

Every skill in this registry is scanned for:

- **Prompt injection** — `ignore previous instructions`, `new persona`, etc.
- **Data exfiltration** — unauthorized external POST/upload calls
- **Privilege escalation** — destructive system commands
- **Credential exposure** — hardcoded keys or tokens
- **Obfuscation** — base64-embedded instructions, unicode direction overrides

Security scores are displayed on [SkillForge](https://github.com/salmandev/skillforge). Skills scoring below 70 are quarantined pending review. Skills scoring below 50 are rejected.

---

## Platform Compatibility

| Platform | Skills Supported | Notes |
|----------|-----------------|-------|
| Claude (Anthropic) | 25/25 | Full native support |
| GPT-4 (OpenAI) | 22/25 | 3 Claude-specific skills excluded |
| Gemini (Google) | 18/25 | Limited tool-use skills |
| Qwen (Alibaba) | 20/25 | Strong code skill support |
| Cursor | 15/25 | IDE-native skills prioritized |
| Codex CLI | 14/25 | Terminal-focused skills |
| JAIS (G42) | 5/25 | Arabic skills only currently |
| Falcon (TII) | 4/25 | Arabic skills only currently |
| ALLaM (SDAIA) | 4/25 | Arabic skills only currently |

---

## Contributing

We welcome contributions — especially:

- 🔴 Arabic/MENA skills (biggest gap in the ecosystem)
- 🔴 JAIS / Falcon / ALLaM compatibility testing
- 🟡 New skill categories (legal, finance, HR)
- 🟡 Workflow compositions (multi-skill chains)
- 🟢 Agent persona templates
- 🟢 MCP server registry entries

See [CONTRIBUTING.md](./CONTRIBUTING.md) for the full guide.

### Quick Contribution Steps
```bash
# 1. Fork and clone
git clone https://github.com/your-username/agency-skills-registry

# 2. Copy the template
cp SKILL_TEMPLATE.md skills/<category>/<your-skill-slug>/SKILL.md

# 3. Fill in your skill
# 4. Validate
node tools/validate-skill.js skills/<category>/<your-skill-slug>/SKILL.md

# 5. Submit a PR
```

---

## Roadmap

### v0.1 (Current)
- [x] 25 foundation skills
- [x] Standard SKILL.md format with registry extensions
- [x] Keyword index (seed)
- [x] Arabic skills collection started

### v0.2
- [ ] Agent persona templates (SOUL.md format)
- [ ] Workflow compositions
- [ ] MCP server registry
- [ ] GitHub Actions auto-submit to SkillForge

### v0.3
- [ ] 50 Arabic skills (full v1.0 of arabic-skills-library)
- [ ] JAIS / Falcon / ALLaM compatibility scores
- [ ] CLI: `npx agency-agents-cli install --lang ar`
- [ ] Automated security scanning on PRs

### v1.0
- [ ] 200+ skills across all categories
- [ ] Full Arabic skills library integrated
- [ ] Community governance model
- [ ] SkillForge as hosted platform

---

## Related Projects

| Project | Description |
|---------|-------------|
| [skillforge](https://github.com/salmandev/skillforge) | Web UI — search, browse, and install skills |
| [skillforge-api](https://github.com/salmandev/skillforge-api) | Backend API powering SkillForge |
| [arabic-skills-library](https://github.com/salmandev/arabic-skills-library) | Dedicated Arabic/MENA skills collection |
| [agency-agents-cli](https://www.npmjs.com/package/agency-agents-cli) | CLI to install skills from this registry |

---

## License

MIT © [salmandev](https://github.com/salmandev)

---

<p align="center">
  Built for every LLM. Open to every contributor. Native to Arabic.
  <br/><br/>
  <a href="https://github.com/salmandev/skillforge">SkillForge Platform</a> ·
  <a href="https://github.com/salmandev/arabic-skills-library">Arabic Skills</a> ·
  <a href="https://www.npmjs.com/package/agency-agents-cli">CLI on npm</a>
</p>