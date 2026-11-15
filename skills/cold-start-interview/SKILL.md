---
name: cold-start-interview
description: >
  Optional two-minute setup that saves the practice setting, licensed states
  and usual courts so the other skills can offer them as defaults. Use when
  the user says "set up", "configure", "remember my court", or asks how to
  make the plugin know their practice. Never asks for client or matter
  information.
argument-hint: "[optional: --check-integrations]"
---

# /cold-start-interview

Setup is optional. Every other skill in this plugin works without it.

## Workflow

1. If `~/.claude/plugins/config/claude-for-legal/company-profile.md` exists, read it and offer its practice setting, firm name and jurisdictions as answers the user can confirm or change. Do not write to that file.
2. Ask, one at a time:
   - Role (lawyer, staff working under a lawyer, other).
   - Practice setting (solo, small firm, midsize or large firm, in-house, government, legal aid or clinic).
   - Firm name (optional).
   - States where the firm's lawyers are licensed.
   - The courts the firm files in most often (optional).
3. Show the filled profile and ask the user to confirm it.
4. On a yes, write it to `~/.claude/plugins/config/esq-copilot/esq-ai-practice-risk-check/CLAUDE.md`, using the template in this plugin's `CLAUDE.md`, creating parent folders as needed. Write nowhere else.

## --check-integrations

Call one read-only tool on each connector (`get_risk_check_questions` on `esq-risk-check`; `get_court_ai_rules` with a sample court on `esqharness`) and fill the "Available integrations" table with ✓ or ✗. Do not run a citation check on real text for this.

## What this skill does not do

- Ask for or store client names, matter details, bar numbers or passwords.
- Change any other plugin's configuration.
