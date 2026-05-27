# QA HRcloud Codex Instructions

This repository contains QA knowledge, agent profiles, and skills migrated from Cursor into Codex-native locations.

## Always-On Rules

- Prefer the smallest relevant specialist context instead of loading every agent or skill.
- When the user provides a Jira or Atlassian link, use the configured Atlassian MCP first to fetch the story, comments, parent/linked issues, and related context before analysis.
- For requirement review, use `.codex/agents/requirement-analysis.agent.md` and `.codex/skills/requirement_analyze/SKILL.md`.
- For loophole/gap analysis, use `.codex/agents/story-loophole-finder.agent.md` and requirement analysis context.
- For test case writing, use `.codex/skills/testcasewriting/SKILL.md`; present draft suites for approval before finalizing when requested by the QA rules.
- For browser execution or bug verification, first read `.codex/system/Guidance.md`, then the relevant setup/navigation/module/role/testing files listed there.
- For bug reports, use `.codex/skills/bugreport/SKILL.md`; do not create or submit Jira bugs without explicit user approval.
- For automation code, follow Selenium/C# POM rules in `.codex/skills/automationtest/SKILL.md` or Playwright rules in `.codex/skills/auto_playwright/SKILL.md`, depending on the request.

## Migrated Assets

- Rules: `.codex/rules/QA.md`
- Agents: `.codex/agents/`
- Skills: `.codex/skills/`
- HRcloud knowledge base: `.codex/system/`
- QA instructions mirror: `.codex/instructions/QA.instructions.md`

Read `.codex/rules/QA.md` for the full Cursor rule migration when a task is QA-heavy, mode-specific, or ambiguous.
