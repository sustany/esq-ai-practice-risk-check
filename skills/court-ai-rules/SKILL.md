---
name: court-ai-rules
description: >
  List a U.S. court's rules, ethics guidance and judges' standing orders on
  generative AI, each with its source, and draft an AI-use disclosure for
  attorney review. Use when a lawyer is preparing anything to be filed in a
  U.S. court, asks what a court or judge requires about AI use, or needs a
  declaration disclosing generative AI use.
argument-hint: "[court and state, optional judge, e.g. 'C.D. Cal., Judge Wright']"
---

# /court-ai-rules

This skill uses the EsqHarness connector (`esqharness`) and its `get_court_ai_rules` and `draft_ai_disclosure` tools.

## Load context

Optional: `~/.claude/plugins/config/esq-copilot/esq-ai-practice-risk-check/CLAUDE.md` → courts the firm files in most often. Offer that court as a default, and have the lawyer confirm it.

## Workflow

1. Ask for the court (with its state) and the assigned judge if the lawyer knows it. Then call `get_court_ai_rules`.
2. Start with `[AI-ASSISTED DRAFT: requires attorney review before use]` and a one-line reviewer note (sources checked, number of rules found).
3. List each rule with its title, who issued it, what it requires, its source link and its `how_checked` label, exactly as returned.
4. Read the `note` and tell the lawyer what it says about coverage. When no rules are on file, say: "No rules on file for this court in EsqHarness. That does not mean the court has none." Tag that line `[review]`.
5. If any rule requires a disclosure or certification, offer `draft_ai_disclosure`. Fill in only the details the lawyer gives; leave the bracketed placeholders for everything else.
6. Present the declaration as a draft the attorney must review and adapt to the exact wording and format each rule requires.
7. Remind the lawyer to read the assigned judge's current standing orders on the court's website, because judges issue new ones often.

## Hard gate

Do not say a filing complies with any rule. These tools find and summarize rules; the attorney decides what they require.
