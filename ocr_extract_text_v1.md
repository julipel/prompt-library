# ExtractText (Document OCR)

Version: v1.0  
Owner: AI / Prompt Engineering Team  
Tags: OCR, documents, scan, text-extraction

---

## Goal

Reliable extraction of text from scanned documents or images without hallucinations, preserving structure and explicitly marking uncertainties.

---

## Behavior Rules

- Do not invent, interpret, or correct content
- Preserve original structure when possible
- Unreadable fragments → [?]
- Missing fragments → [ ... ]

---

## Input Variables

DOC_IMAGE — document image / scan / PDF page  
LANG — ru / en / auto  
FORMAT — plain / markdown  
STRUCTURE_LEVEL — lines / paragraphs / layout  
UNCERTAINTY_TAG — default `[?]`

---

## Prompt Template v1.0

Extract text from {DOC_IMAGE}.

Rules:  
Do not add or modify information.  
Preserve structure: {STRUCTURE_LEVEL}.  
Unreadable parts → {UNCERTAINTY_TAG}  
Missing fragments → [ ... ]

Return strictly:

META  
- language:  
- notes:  

TEXT  

ISSUES  

---

## Example Input

DOC_IMAGE = scan_contract_page1.jpg  
LANG = ru  
FORMAT = plain  
STRUCTURE_LEVEL = paragraphs

---

## Example Output

META  
- language: ru  
- notes: compression artifacts

TEXT  
ДОГОВОР ПОСТАВКИ № 14/02  
...

ISSUES  
- [p1] location: "...", issue: unreadable

---

## Test Cases

### Test Case 1 — Clean Scan

Scenario: High-quality scan, printed text.

Expected Result:
- Full text extracted
- No hallucinated content
- Structure preserved

---

### Test Case 2 — Blurred Fragment

Scenario: Partial blur or artifacts.

Expected Result:
- Unreadable parts marked with `[?]`
- No guessed replacements
- ISSUE entry present

---

### Test Case 3 — Table / Layout

Scenario: Document with table, STRUCTURE_LEVEL=layout, FORMAT=markdown.

Expected Result:
- Table preserved in Markdown
- No linearized text dump
- Issues documented if distortions exist
