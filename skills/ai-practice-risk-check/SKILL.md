---
name: ai-practice-risk-check
description: Run the ESQ AI Practice Risk Check for a U.S. lawyer or law firm. Use when a lawyer asks how safely their firm uses generative AI, wants an AI risk score or self-assessment, asks whether their AI use meets their ethics duties, or asks what ABA Formal Opinion 512 requires.
---

# ESQ AI Practice Risk Check

This skill uses the ESQ Risk Check connector (`esq-risk-check`), part of the EsqHarness plugin. It has three tools:
`get_risk_check_questions`, `score_ai_practice_risk` and `explain_ai_ethics_duties`.

## Run the check

If the three tools are not available in this conversation, tell the user in one sentence to turn on the connector: click **+** in the message box, then **Connectors**, switch on **esq-risk-check**, and send any message. Do not search for other connectors.

1. Call `get_risk_check_questions`. Tell the user it takes about 4 minutes and that answers are scored on the spot and not stored.
2. Ask the 12 questions in order, three or four at a time, with the a, b and c options exactly as the tool gives them. Let the user answer with a letter or in their own words, and map each answer to a, b or c. If an answer is unclear, ask once. If the user is still unsure, use c.
3. When you have all 12 answers, call `score_ai_practice_risk` with the answers in order.
4. Reply with:
   - the score out of 100 and the one-line summary,
   - a short table of the seven areas and their percentages,
   - the three weakest areas, each with its next step,
   - the `full_report` link, introduced as the full report on esqcopilot.com,
   - the disclaimer, word for word.
5. Stop there. Do not add your own analysis, commentary, ranking or advice after the result, and do not say how much any change will raise the score or close a gap. You may offer, in one sentence, to explain the ethics duties behind any area.

## Explain the ethics duties

When the user asks what ethics duties apply to using AI, call `explain_ai_ethics_duties` with the topic they ask about (competence, confidentiality, communication, candor, supervision or fees), or `all`. Give the summary, name the source, and tell the user that their own jurisdiction's rules and guidance control. Offer to run the risk check afterward.

## Rules

- Use only the questions, scores and wording the tools return. Do not change the scoring or add questions.
- Do not give legal advice or say whether the user complies with any rule. The check is general education about practice management.
- Do not ask for client names, matter details or other confidential information. The check does not need them.
- Do not promise outcomes, savings or returns.
