---
name: ai-use-policy-draft
description: >
  Draft a firm-specific generative AI use policy for a U.S. law firm, built
  from the firm's AI Practice Risk Check answers and the duties summarized in
  ABA Formal Opinion 512, for attorney review. Use after the risk check, or
  when a lawyer asks for an AI use policy, an AI policy template, or written
  rules for how lawyers and staff may use AI.
argument-hint: "[optional: firm name and states, e.g. 'Smith Law, CA and NV']"
---

# /ai-use-policy-draft

Uses `explain_ai_ethics_duties` from the ESQ Risk Check connector (`esq-risk-check`). If the tool is not available, say so in one sentence and do not draft the duty summaries from memory.

## Inputs

1. The 12 risk check answers from this conversation, if the check was run. If not, offer to run the `ai-practice-risk-check` skill first, or draft a general version with every firm-specific choice left as a bracketed placeholder.
2. Ask in one message, all optional: firm name, states where the firm's lawyers are licensed, firm size, and which AI tools the firm uses or allows. Read them from `~/.claude/plugins/config/esq-copilot/esq-ai-practice-risk-check/CLAUDE.md` if it exists, and let the user confirm. Never ask for client names or matter details.
3. Call `explain_ai_ethics_duties` with `all`.

## Draft

Start with `[AI-ASSISTED DRAFT: requires attorney review before use]` and the reviewer note from the plugin's CLAUDE.md. Then write the policy with these sections, short and in plain English:

1. **Purpose and scope**: who it covers (lawyers, staff, contractors) and that the responsible attorney remains responsible for all work.
2. **Approved tools**: list the tools the user named, or `[list approved tools]`. Only business accounts the firm controls; no personal or free consumer accounts for client work.
3. **Confidential information**: check vendor retention and training terms before client information goes in; informed client consent before entering client information into a tool that can disclose it, and boilerplate consent in an engagement letter is not enough (from the tool's confidentiality summary).
4. **Verification**: every AI-assisted citation and quotation checked against the original source before filing or sending, with the check recorded; follow each court's AI disclosure or certification rules.
5. **Client communication and fees**: when AI use is disclosed to clients; hourly billing only for time actually spent; no billing for learning a general AI tool; AI costs as expenses only with a proper basis and disclosure (from the tool's fees and communication summaries).
6. **Supervision and training**: who approves tools, training on Opinion 512 and state guidance, written acknowledgment by every lawyer and staff member, and supervision of outside vendors.
7. **Security and incidents**: multi-factor sign-in on email and every AI tool; a one-page plan for client data exposed through an AI tool (who is told first, how to stop the tool, how to record what was exposed, who reviews notice duties).
8. **Review**: review date `[date]` and policy owner `[name]`.

Tailor the detail to the answers: where an answer was c (no), write the rule in full and mark the line `[review: new practice for the firm]`; where it was a, keep the rule short. Name each duty's source as the tool returns it (ABA Formal Opinion 512, July 29, 2024, and the Model Rule numbers).

End with: "ABA opinions are not binding. Check your state's rules and ethics guidance, which control, and adapt this draft before adoption."

## Rules

- Draft only. Do not say the policy makes the firm compliant.
- Do not invent state rules, court rules, opinion numbers or dates. If the user wants state-specific rules, say they must be added from the state's own sources and mark `[add state guidance]`.
- No product names, prices or links in the draft.
