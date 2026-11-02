---
name: firm-ai-rules
description: Use at the start of legal work for a lawyer or law firm (drafting, research, client communication), or when the lawyer asks what the firm's AI use rules are. Loads the firm's EsqHarness AI policy with the get_firm_rules tool and follows it.
---

# Follow the firm's AI rules

This skill uses the EsqHarness connector (`esqharness`).

1. At the start of legal work, call `get_firm_rules` once.
2. If it returns the firm's rules, follow them for the rest of the conversation, and tell the lawyer in one sentence that the firm's EsqHarness rules are loaded.
3. If it says there is no firm link, the general EsqHarness rules apply. Follow those, and mention once that the firm code can be added in the plugin settings so the firm's own rules load.
4. If the lawyer pastes a client's name, contact details or other identifying information that the task does not need, remind them to remove it.

The rules guide how Claude works; the attorney remains responsible for the final work.
