# Session Context

## Last Updated
2026-04-07

## Current Focus
- User asked to create a subagent that uses MCP to read Jira stories.
- New subagent file created: `.cursor/subagents/JIRA_STORY_READER.md`.
- Subagent defines mission, triggers, workflow, constraints, and output format for Jira requirement analysis.

## Workspace Notes
- Template remains available at `.cursor/subagents/SUBAGENT_TEMPLATE.md`.
- Example existing agent reference: `.github/agents/docs-manager.agent.md`.
- QA workspace rule file is present at `.cursor/rules/QA.mdc`.

## Next Action
- User can invoke or adapt `jira-story-reader` for real Jira keys/URLs.
- Optional next step: wire this definition into a runnable custom command/agent flow if needed.
