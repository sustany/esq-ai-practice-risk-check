---
name: check-before-filing
description: Use whenever a lawyer asks Claude to draft, edit or review a brief, motion, memo, letter or any text that contains case citations or quotations from court opinions, and before handing that text back. Checks every citation and quotation with the EsqHarness check_citations tool.
---

# Check citations and quotations before a lawyer relies on them

This skill uses the EsqHarness connector (`esqharness`).

1. Before you give the lawyer any text that contains a case citation or a quotation from a court opinion, call `check_citations` with the full text. Add a short `label` (for example the document title) if the lawyer gave one. Do not include client names or other identifying details the check does not need.
2. Show the result plainly:
   - the `summary` line;
   - every citation or quotation whose status is not "found", each with its status, written exactly as returned;
   - the `how_to_read` note, in one or two sentences.
3. Never call a citation or quotation reliable unless the tool returned "found". "Found" means the case exists; it does not confirm the case says what the draft claims. Statutes and rules are not checked.
4. If the result says the check was not recorded (`logged_to_firm_record` is false), you may say in one sentence that adding the firm code in the plugin settings records each check in the firm's monthly record.
5. End every draft meant for filing with: "Attorney check required before filing: every citation and quotation verified against the original source, and any required AI-use disclosure added."

Never invent a citation, quotation, docket number or fact. If the check fails or the database is busy, say so and tell the lawyer to check the authorities by hand.
