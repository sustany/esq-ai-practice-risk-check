---
name: check-before-filing
description: >
  Check every case citation and opinion quotation in a draft with the
  EsqHarness check_citations tool before the lawyer relies on it. Use whenever
  a lawyer asks Claude to draft, edit or review a brief, motion, memo, letter
  or any text that contains case citations or quotations from court opinions,
  and before handing that text back.
argument-hint: "[paste the draft, or name the document to check]"
---

# /check-before-filing

This skill uses the EsqHarness connector (`esqharness`).

## Hard gate: no unchecked authority goes back to the lawyer

Before you give the lawyer any text that contains a case citation or a quotation from a court opinion, call `check_citations` with the full text. This gate has no exemption for short drafts, "just one cite," or text the lawyer wrote themselves.

## Workflow

1. Call `check_citations` with the text. Add a short `label` (for example the document title) if the lawyer gave one. Leave out client names and other identifying details the check does not need.
2. Put the reviewer note above the result:
   > **Reviewer note**
   > - **Sources:** EsqHarness (CourtListener) checked | not reachable: nothing checked, verify every cite by hand
   > - **Checked:** [N citations, N quotations]
   > - **Flagged for your judgment:** [N not found or partial | none]
   > - **Before relying:** read each cited passage in the original opinion
3. Show the result plainly:
   - the `summary` line;
   - every citation or quotation whose status is not "found", each with its status exactly as returned, tagged `[review]`;
   - the `how_to_read` note, in one or two sentences.
4. Never call a citation reliable unless the tool returned "found". "Found" means the case exists; it does not confirm the case says what the draft claims. Statutes and rules are not checked; tag each one `[not checked: verify]`.
5. If `logged_to_firm_record` is false, you may say once that firms with an EsqHarness account record each check through the personal connector link in their welcome email. No price, no link to buy.
6. End every draft meant for filing with: "Attorney check required before filing: every citation and quotation verified against the original source, and any required AI-use disclosure added."

## Decline pathway

If the check fails, times out, or the database is busy, say so plainly, mark every citation `[not checked: verify]`, and tell the lawyer to check the authorities by hand. Do not fall back to "it looks right to me."

Never invent a citation, quotation, docket number or fact.
