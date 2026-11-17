---
name: aba-512-checklist
description: >
  Build an ABA Formal Opinion 512 checklist for a U.S. lawyer or law firm,
  marked done or open from the firm's AI Practice Risk Check answers. Use
  after the risk check, or when a lawyer asks for an Opinion 512 checklist,
  what Opinion 512 requires them to do, or how to check their AI use against
  their ethics duties.
argument-hint: "[optional: one duty such as 'fees', or leave blank for all six]"
---

# /aba-512-checklist

Uses `explain_ai_ethics_duties` from the ESQ Risk Check connector (`esq-risk-check`). If the tool is not available, say so in one sentence and do not write the checklist from memory.

## Workflow

1. Call `explain_ai_ethics_duties` with `all` (or the one topic the user asked for).
2. Build one table per duty, in this order: Competence (Rule 1.1), Confidentiality (Rules 1.6, 1.9(c), 1.18(b)), Communication (Rule 1.4), Candor and meritorious claims (Rules 3.1, 3.3, 8.4(c)), Supervision (Rules 5.1, 5.3), Fees (Rule 1.5). Each row is one concrete practice taken from the tool's summary for that duty, written as a yes/no item.
3. Mark each row from the risk check answers in this conversation, using only the risk check question listed for it:

   | Checklist item | Risk check question |
   |---|---|
   | Training on Opinion 512 or state AI guidance | Q1 |
   | Client disclosure of AI use and its effect on fees | Q2 |
   | Vendor retention and training terms checked before client data goes in | Q3 |
   | Only business AI accounts the firm controls | Q4 |
   | Every AI-assisted citation and quotation checked and recorded | Q5 |
   | Court AI disclosure and certification rules known and tracked | Q6 |
   | Written AI use policy acknowledged by staff | Q7 |
   | Approved-tools list | Q8 |
   | Written vendor questionnaire before adoption | Q9 |

   Answer a = **Done**, b = **Partly**, c = **Open**. Rows with no question listed = **Not covered by the check**. If the check was not run, mark every row `[ ]` and offer to run the `ai-practice-risk-check` skill.
4. Below the tables, list the Open and Partly rows in one short list, each with the next step for that area from the check result if one was returned.
5. End with: "ABA opinions are not binding. Your state's rules and guidance control." Offer the `ai-use-policy-draft` skill in one line.

## Rules

- Use only the duty summaries the tool returns. Do not add duties, rules or state requirements, and do not say the firm complies.
- Label the checklist `[AI-ASSISTED DRAFT: requires attorney review before use]`.
- No product names, prices or links.
