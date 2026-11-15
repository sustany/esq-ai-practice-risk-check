# ESQ CoPilot AI Practice Risk Check

A free AI practice risk check for U.S. lawyers and law firms, inside Claude, with citation, quotation and court-rule checks. From ESQ CoPilot. Built to the same layout and conventions as Anthropic's open-source Claude for Legal plugins (skills, a practice-profile template, shared guardrails, and a reviewer note on every legal draft).

Every output is a draft for attorney review. This is not legal advice.

## Skills

| Skill | What it does |
|---|---|
| `/esq-ai-practice-risk-check:ai-practice-risk-check` | Say "Run my AI risk check" (or `/esq-ai-practice-risk-check:run-my-ai-risk-check`). 12 quick questions (about 2 minutes), a score out of 100 in seven areas, your top 3 gaps with a next step for each, and summaries of the ethics duties in ABA Formal Opinion 512 (July 29, 2024). Answers are not stored. The result ends with one "Save your report" link to esqcopilot.com. |
| `/esq-ai-practice-risk-check:ai-use-policy-draft` | A firm-specific AI use policy draft built from the risk check answers and the Opinion 512 duty summaries, for attorney review. |
| `/esq-ai-practice-risk-check:aba-512-checklist` | An ABA Formal Opinion 512 checklist, each item marked done, partly or open from the risk check answers. |
| `/esq-ai-practice-risk-check:check-before-filing` | Looks up every case citation in a draft in the CourtListener case-law database and searches each quotation in the opinion text. "Found" means the case exists, not that it says what the draft claims. Statutes and rules are not checked. |
| `/esq-ai-practice-risk-check:court-ai-rules` | Court rules, ethics guidance and judges' standing orders on AI for a U.S. court, each with its source and a label saying how it was checked, plus a draft AI-use disclosure for the attorney to adapt. |
| `/esq-ai-practice-risk-check:firm-ai-rules` | Loads the firm's own AI use policy, for firms that connect with their personal EsqHarness link. |
| `/esq-ai-practice-risk-check:cold-start-interview` | Optional setup: practice setting, licensed states and usual courts, used only as defaults. |

## Install

```
/plugin marketplace add sustany/esq-ai-practice-risk-check
/plugin install esq-ai-practice-risk-check@esq-copilot
```

## Practice profile

Setup is optional. If you run `/esq-ai-practice-risk-check:cold-start-interview`, your answers are saved on your own computer at `~/.claude/plugins/config/esq-copilot/esq-ai-practice-risk-check/CLAUDE.md`. If you already use Anthropic's Claude for Legal plugins, the interview offers the practice setting and jurisdictions from your existing `company-profile.md` and never changes that file.

## What this plugin sends and runs

Nothing runs on your computer. The plugin connects Claude to two remote servers operated by ESQ CoPilot (Digital Crossings Inc):

- `https://mcp.esqcopilot.com/mcp` (Risk Check): receives only the 12 letter answers or the ethics topic, and stores nothing.
- `https://mcp.esqcopilot.com/harness` (EsqHarness): receives the draft text you ask it to check, or the court and judge name. It sends the citations and short quotation phrases to CourtListener (https://www.courtlistener.com) to look them up. Through this plugin nothing is saved.

Claude never sends your chat history, files or memory. Remove client names and other identifying details the task does not need before asking for a check.

## Privacy and terms

Plugin privacy notice: [PRIVACY.md](PRIVACY.md). Privacy policy: https://esqcopilot.com/privacy.html. Terms: https://esqcopilot.com/terms.html.

## Support

https://esqcopilot.com/contact.html, notices@esqcopilot.com. ESQ CoPilot is operated by Digital Crossings Inc, 92 Corporate Park, Ste C #1083, Irvine, CA 92606.
