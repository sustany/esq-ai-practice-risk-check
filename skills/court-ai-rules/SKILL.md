---
name: court-ai-rules
description: Use when a lawyer is preparing anything to be filed in a U.S. court, asks what a court or judge requires about AI use, or needs a declaration disclosing generative AI use. Uses the EsqHarness get_court_ai_rules and draft_ai_disclosure tools.
---

# Court AI rules and AI-use disclosures

This skill uses the EsqHarness connector (`esqharness`).

1. Ask for the court (with its state) and the assigned judge if the lawyer knows it. Then call `get_court_ai_rules`.
2. List each rule with its title, who issued it, what it requires, its source link and its `how_checked` label, exactly as returned. Read the `note` and tell the lawyer what it says about coverage, including when no rules are on file for that court. "No rules on file" never means the court has none.
3. If any rule requires a disclosure or certification, offer `draft_ai_disclosure`. Fill in only the details the lawyer gives; leave the bracketed placeholders for anything else.
4. Present the declaration as a draft the attorney must review and adapt to the exact wording and format each rule requires.
5. Remind the lawyer to read the assigned judge's current standing orders on the court's website, because judges issue new ones often.

Do not say a filing complies with any rule. These tools find and summarize rules; the attorney decides what they require.
