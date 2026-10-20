---
name: skills-create-modify
description: Create and modify LLM skills globally with documentation, configuration, and dependencies.
---

## Overview
Agent skills are stored in `~/.agents/skills`. Each skill follows `{skill name}/SKILL.md` structure. Files contain clear steps for agents to perform tasks related to the skill.

## Creating a New Skill

### 1. Check Existing Skills
Search existing skills to see if requested functionality can extend or integrate into an existing one. This prevents duplication and improves token efficiency.

### 2. Determine Skill Name
Choose unique, descriptive name that matches directory structure (e.g., `my-skill`).

### 3. Create Directory
```bash
mkdir ~/.agents/skills/{skill-name}
```

### 4. Create SKILL.md File with These Sections
Write the main content file at `~/.agents/skills/{skill-name}/SKILL.md`:

- **Usage Instructions** (required): How to use the skill, concrete examples, common workflows, and prerequisites for using this skill
- **Documentation** (recommended): Purpose explanation, context about capabilities, use-case examples
- **Configuration & Preferences** (optional): Default parameter values, references to environment variables or config sources (non-sensitive only)
- **Dependencies** (optional): Tools or complementary skills required for this skill to work

### 5. Security Best Practices
- Never store sensitive information (API keys, passwords, secrets) directly in SKILL.md
- Use environment variables, config files, or other secure methods for sensitive data
- Document where to find configuration, but do not include actual credentials

## Modifying an Existing Skill

1. **Locate**: `~/.agents/skills/{skill-name}`
2. **Read**: Open and understand current functionality, documentation, and configuration
3. **Plan Changes**: Identify what needs to be added, changed, or removed while maintaining clarity and token efficiency
4. **Edit**: Use `edit_file` or `write_file` - preserve original structure and format
5. **Test**: Verify skill works as expected

## Validation Checklist
- Directory and file structure correct
- Skill name matches directory name exactly
- Instructions clear, comprehensive, yet concise
- No sensitive information stored directly in the skill file
