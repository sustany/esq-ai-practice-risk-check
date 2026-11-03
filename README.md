# EsqHarness for Claude

AI safeguards for U.S. lawyers, inside Claude. From ESQ CoPilot.

EsqHarness checks the parts of AI-assisted legal work that get lawyers sanctioned: case citations that do not exist, quotations a court never wrote, and court rules on AI use that a filing ignores. It also loads the firm's own AI rules and runs a short AI Practice Risk Check. These tools check and remind; the attorney remains responsible for the final work. This is not legal advice.

## What it does
- **Citation and quotation check** (`check_citations`): every case citation in a draft is looked up in the CourtListener case-law database; quotations from opinions are searched in the opinion text. Anything not found is flagged for a check by hand. "Found" means the case exists, not that it says what the draft claims. Statutes and rules are not checked.
- **Court AI rules** (`get_court_ai_rules`): court rules, ethics guidance and judges' standing orders on AI for a U.S. court, each with its source and a label saying whether a person checked it against the source. Coverage is listed in every answer; a court with nothing on file says so.
- **AI-use disclosure** (`draft_ai_disclosure`): a draft declaration based on the court's rules, for the attorney to review and adapt.
- **Firm AI rules** (`get_firm_rules`): the firm's EsqHarness AI policy, loaded at the start of legal work.
- **AI Practice Risk Check** (`get_risk_check_questions`, `score_ai_practice_risk`, `explain_ai_ethics_duties`): 12 questions, a score out of 100 in seven areas, and one next step for each weak area.

Four short skills tell Claude when to use each tool: `check-before-filing`, `court-ai-rules`, `firm-ai-rules` and `ai-practice-risk-check`.

## Install
Claude Code (version 2.1.275 or later):

```
/plugin install esqharness --marketplace sustany/esq-ai-practice-risk-check
```

Older versions:

```
/plugin marketplace add sustany/esq-ai-practice-risk-check
/plugin install esqharness@esqharness
```

**Firm code (optional):** firms with an EsqHarness account can enter the 36-character code from the end of their EsqHarness connector link (after `t=`) when the plugin asks. Claude stores it as a protected setting. With it, the firm's own AI rules load and every citation check is added to the firm's monthly record. Without it, the checks work and nothing is recorded. EsqHarness accounts: https://esqcopilot.com/esqharness.html

## Examples
- "Check the citations and quotations in this brief before I file it." (paste the draft)
- "What are the AI rules for a filing in the Central District of California before Judge Wright?"
- "Draft the AI-use declaration for my opposition in Orange County Superior Court."
- "Run the AI practice risk check for my firm."
- "What does ABA Formal Opinion 512 say about confidentiality?"

## What this plugin sends and runs
Nothing runs on your computer. The plugin connects Claude to two remote servers operated by Decentralized Publishing LLC:
- `https://mcp.esqcopilot.com/harness` (EsqHarness). It receives the draft text you ask it to check, or the court and judge name. It sends the citations and short quotation phrases to CourtListener (https://www.courtlistener.com) to look them up. With a firm code, the check result (citations, statuses, quotations) is saved to that firm's record; without one, nothing is saved.
- `https://mcp.esqcopilot.com/mcp` (Risk Check). It receives only the 12 letter answers or the ethics topic, and stores nothing.

Claude never sends your chat history, files or memory. Remove client names and other identifying details the task does not need before asking for a check.

## Privacy and terms
Plugin privacy notice: [PRIVACY.md](PRIVACY.md). Privacy policy: https://esqcopilot.com/privacy.html. Terms: https://esqcopilot.com/terms.html.

## Support
https://esqcopilot.com/contact.html, notices@esqcopilot.com. Operated by Decentralized Publishing LLC, 92 Corporate Park, Ste C #1083, Irvine, CA 92606.
