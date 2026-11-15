---
name: ai-practice-risk-check
description: >
  Run my AI risk check: the free ESQ CoPilot AI Practice Risk Check for a U.S.
  lawyer or law firm. Twelve quick multiple-choice questions (about 2
  minutes), then a score out of 100 in seven areas and the top 3 gaps, each
  with a next step. Use when a lawyer says "run my AI risk check", asks how
  safely their firm uses generative AI, wants an AI risk score or
  self-assessment, asks whether their AI use meets their ethics duties, or
  asks what ABA Formal Opinion 512 requires.
argument-hint: "[optional: an ethics topic such as 'confidentiality', or leave blank to run the check]"
---

# /ai-practice-risk-check

This skill uses the ESQ Risk Check connector (`esq-risk-check`) and its three tools:
`get_risk_check_questions`, `score_ai_practice_risk` and `explain_ai_ethics_duties`.
The `check_citations` tool mentioned below comes from the EsqHarness connector (`esqharness`) in the same plugin.

## Load context

Optional: `~/.claude/plugins/config/esq-copilot/esq-ai-practice-risk-check/CLAUDE.md` for the practice setting. The check runs the same way without it.

## If the tools are missing

Tell the user in one sentence to turn on the connector: click **+** in the message box, then **Connectors**, switch on **esq-risk-check**, and send any message. Do not score the check from memory and do not search for other connectors.

## Run the check

1. Call `get_risk_check_questions`. Say in one line: "12 quick questions, about 2 minutes. Answers are scored on the spot and not stored."
2. Show all 12 questions in one message, numbered, each with its a, b and c options exactly as the tool gives them, in a compact list. Tell the user they can reply in one line, for example `1a 2c 3b ...`, or in their own words. Map each answer to a, b or c. If some answers are missing or unclear, ask only for those, once. If the user is still unsure, use c.
3. When you have all 12 answers, call `score_ai_practice_risk` with the answers in order.
4. Show the result exactly as the tool returns it:
   - the score out of 100 and the one-line summary,
   - a short table of the seven areas and their percentages,
   - **Your top 3 gaps**: the three weakest areas, each with its next step,
   - the disclaimer, word for word.
   Do not add your own analysis, ranking or advice, and do not say how much any change will raise the score. Keep the result free of products and prices.
5. Then add one short section headed **Free next steps in this chat**, with these three offers, one line each:
   - "**Draft your firm's AI use policy**, built from your answers, for attorney review." (runs `/esq-ai-practice-risk-check:ai-use-policy-draft`)
   - "**ABA Formal Opinion 512 checklist**, marked with what your answers show is done and still open." (runs `/esq-ai-practice-risk-check:aba-512-checklist`)
   - "**Check a draft's citations**: paste a brief, motion or memo and every case citation and quotation is looked up in the CourtListener case-law database. No account needed, nothing saved." If Verification is one of the top 3 gaps, put this offer first.
6. End the reply with exactly one link, on its own line, and nothing after it:

   `**Save your report:** https://esqcopilot.com/save-report.html?a=ANSWERS&utm_source=claude&utm_medium=plugin&utm_campaign=risk-check`

   Replace `ANSWERS` with the 12 answer letters in question order, lower case, with no spaces or separators (for example `bcabcbacbbca`). The page rebuilds the same score from those letters. This link takes the place of the tool's `full_report` link; do not show both. Do not add any other link, product name, price or sales wording to the reply.
7. If the user picks an offer, run that skill. If the user pastes a draft, follow `/esq-ai-practice-risk-check:check-before-filing`.

## Explain the ethics duties

When the user asks what ethics duties apply to using AI, call `explain_ai_ethics_duties` with the topic (competence, confidentiality, communication, candor, supervision or fees), or `all`. Give the summary, name the source, and say that the user's own jurisdiction's rules and guidance control. Offer to run the check afterward.

## Rules (hard gates)

- Use only the questions, scores and wording the tools return. Do not change the scoring or add questions.
- Do not give legal advice or say whether the user complies with any rule. The check is general education about practice management.
- Do not ask for client names, matter details or other confidential information. The check does not need them.
- The answer letters in the Save your report link are the only data in it. Never put a name, email, firm, bar number or any other personal detail in the link.
- Do not sell, quote prices, link to a checkout page, promise outcomes, or say an offer is limited or ending. The one Save your report link is the only link to esqcopilot.com in the reply.
- Show the Free next steps section and the Save your report link once per completed check. If the user declines, do not repeat them.

## What this skill does not do

- Store answers. The server scores them and keeps nothing. The answers reach esqcopilot.com only if the user opens the Save your report link, and are kept only if the user saves the report there.
- Certify compliance or replace the firm's own review of its AI policy.
