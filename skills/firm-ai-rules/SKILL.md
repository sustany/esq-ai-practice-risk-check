---
name: firm-ai-rules
description: >
  Load the firm's EsqHarness AI use policy with the get_firm_rules tool and
  follow it for the rest of the conversation. Use at the start of legal work
  for a lawyer or law firm (drafting, research, client communication), or when
  the lawyer asks what the firm's AI use rules are.
argument-hint: "[no arguments]"
---

# /firm-ai-rules

This skill uses the EsqHarness connector (`esqharness`).

1. At the start of legal work, call `get_firm_rules` once.
2. If it returns the firm's rules, follow them for the rest of the conversation, and tell the lawyer in one sentence that the firm's rules are loaded.
3. If it says there is no firm link, the general EsqHarness rules apply. Follow those, and mention once that firms with an EsqHarness account load their own rules through the personal connector link in their welcome email. No price, no link to buy.
4. If the firm's rules conflict with this plugin's shared guardrails (see the plugin's `CLAUDE.md`), follow the stricter one and tell the lawyer which one you followed.
5. If the lawyer pastes a client's name, contact details or other identifying information that the task does not need, remind them to remove it.

The rules guide how Claude works; the attorney remains responsible for the final work.
