# roylistack

Roy's collection of reusable skills for Codex. Each skill lives in its own folder, so you can install what you need and add more over time.

## Skills

| Skill | What it does |
| --- | --- |
| [icon-picker](skills/icon-picker/SKILL.md) | Select, source, and uniformly scale consistent, accessible Untitled UI icons for websites, apps, and Figma. |

## Install a skill

Ask Codex to install the skill from its GitHub folder:

```text
Use skill-installer to install https://github.com/royli25/roylistack/tree/main/skills/icon-picker
```

Or clone the collection and copy the skill into your Codex skills directory:

```sh
git clone https://github.com/royli25/roylistack.git
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R roylistack/skills/icon-picker "${CODEX_HOME:-$HOME/.codex}/skills/"
```

The copy command is for a fresh installation. If `icon-picker` is already installed, preserve any local edits before replacing its folder. Restart Codex after installation to discover the skill, then invoke it with `$icon-picker` or describe a matching task.

## Add a skill

Create a folder under `skills/` with a lowercase, hyphenated name. Add a `SKILL.md` containing YAML frontmatter and the instructions:

```markdown
---
name: your-skill-name
description: Explain what the skill does and when to use it.
---

# Your skill name

Write the instructions Codex should follow when using this skill.
```

Keep supporting files inside that skill's folder and link to them with relative paths. Add only the resources the skill needs: `references/` for supporting guidance, `scripts/` for helpers, `assets/` for output resources, and `agents/openai.yaml` for optional Codex UI metadata. Add the skill to the table above when it is ready.

```text
roylistack/
├── README.md
└── skills/
    ├── icon-picker/
    │   ├── SKILL.md
    │   ├── agents/openai.yaml
    │   └── references/implementation.md
    └── your-skill-name/
        └── SKILL.md
```

Each folder under `skills/` is a separate installable skill. The collection itself does not need a root `SKILL.md`.
