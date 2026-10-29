# Letter of Credit Trade Document Checking Agent

## Purpose

Provide a controlled workflow for reviewing scanned documents presented under a documentary credit (LC), comparing them with the operative LC and its amendments, and preparing an evidence-backed list of potential discrepancies for an authorized trade operations reviewer.

The agent assists document examination. It does not make the bank's final compliance, honour, refusal, sanctions, or payment decision. A qualified reviewer remains accountable for disposition and any notice to the presenter or applicant.

## Scope and operating assumptions

- The workflow is for documentary credit document checking. It does not replace the bank's KYC, sanctions, fraud, credit, AML, or payment controls; those are separate controls and queues.
- Apply the rules and interpretation standards adopted by the bank for the transaction (for example, the applicable LC terms and the incorporated ICC rules, such as UCP 600 and, where applicable, ISBP). Record the rule set and version used. Do not infer that a rule applies when the credit does not incorporate it.
- Use the latest operative LC text together with amendments in their effective sequence. Preserve the original LC and every amendment.
- Check documents on their face and within the applicable examination standard. Do not claim to verify facts outside the presented documents or to authenticate a document solely from OCR.
- This workflow is an operational design. Bank policy, jurisdictional requirements, product rules, and legal/compliance review must govern production use.

## End-to-end workflow

### 1. Secure intake and case registration

1. Receive scanned presentation documents and any electronic originals through an approved channel.
2. Create a case ID and record receipt date/time, channel, presenting party, LC reference, file names, page counts, and operator/system identity.
3. Store the source files as read-only originals; calculate integrity hashes and retain them under the bank's retention and access policies.
4. Link the presentation to the correct LC, operative amendments, and any prior presentation or correspondence. If the LC reference is missing or ambiguous, route to an operator before examination.
5. Apply access controls and data-handling rules. Do not send customer documents to unapproved services.

**Output:** registered case with immutable source documents and transaction linkage.

### 2. Scan quality and page preparation

1. Check each file for completeness, readability, orientation, cropping, blank pages, duplicate pages, colour/contrast issues, and page sequence.
2. Detect likely multi-page documents and page boundaries, but retain the original page numbering and file/page coordinates.
3. Flag illegible, cut-off, overwritten, obscured, or missing content. Request a better image or manual transcription where required; never silently fill gaps.
4. Apply image enhancement only to a working copy. Keep the original available for reviewer comparison.

**Gate:** if a material field or clause cannot be read reliably, mark it “unreadable/needs review” and do not issue a definitive pass/fail conclusion for that check.

### 3. Document classification and inventory

1. Classify each item (for example: commercial invoice, transport document, packing list, certificate of origin, insurance document, inspection/weight/quality certificate, draft, or other).
2. Identify issuer, document date, number, original/copy status where visible, page range, and apparent relationship to the presentation.
3. Compare the inventory with documents required by the LC.
4. Flag missing, extra, duplicated, misclassified, or unrequested documents for review. An extra document is not automatically a discrepancy; apply the governing rules and LC terms.

**Output:** presentation document inventory, with classification confidence and page-level source references.

### 4. OCR and evidence-preserving extraction

1. Run OCR on each page and preserve the page image, OCR text, bounding boxes or coordinates, engine/version, and extraction time.
2. Extract candidate values only for fields relevant to the LC and document checks: names, addresses, amounts, currency, dates, goods description, quantities, ports/places, shipment and delivery terms, document numbers, signatures/stamps where detectable, and required statements.
3. Attach every extracted value to its source file, page, and location. Store the verbatim text alongside any normalized value.
4. Record field-level confidence. Low-confidence, conflicting, or handwritten values must be routed for human transcription/confirmation.
5. Do not treat OCR recognition of a signature, stamp, security feature, or seal as proof of authenticity.

**Output:** structured extraction with traceable evidence and uncertainty markers.

### 5. Establish the operative LC requirements

1. Extract the LC requirements and identify relevant clauses: required documents, number/original requirements, presentation period, expiry/place, latest shipment date, shipment/transshipment terms, ports, Incoterms or other delivery terms, amount/tolerance, currency, goods description, partial shipment, insurance, and any special conditions.
2. Read the full LC and amendment text, including continuation pages and referenced conditions. Mark clauses that are ambiguous, conflicting, unreadable, or dependent on external interpretation.
3. Build an amendment timeline. For each amendment, record date, acceptance/status if available, affected clause, and resulting operative text. Do not apply an amendment whose acceptance or applicability is unknown; route it for confirmation.
4. Create a clause-to-check matrix so every required document and material requirement has a planned check.
5. Where clause meaning is unclear or contradictory, do not invent an interpretation. Escalate to an authorized LC/trade specialist.

**Output:** versioned operative-requirements record with links to LC/amendment source pages.

### 6. Normalize data without losing the source

1. Normalize dates, currencies, units, country/place names, and party names into comparison fields while retaining the original wording.
2. Preserve distinctions that may be legally or operationally meaningful; do not use fuzzy matching as a substitute for reviewing material identity differences.
3. Mark inferred values separately from values explicitly stated in a source.
4. Keep each normalized value linked to the supporting document evidence and any transformation applied.

### 7. Run document-level and cross-document checks

For each document, compare its face and contents against the operative LC requirements and applicable bank rules. Then perform cross-document consistency checks, including as relevant:

- Applicant, beneficiary, consignee, notify party, and other party names/roles.
- LC, invoice, transport, insurance, and certificate references.
- Invoice amount, LC amount and tolerance, currency, totals, and arithmetic.
- Goods description, quantity, package count, marks, and weights.
- Shipment dates, presentation timing, expiry, and latest shipment date.
- Ports/places of receipt, loading, discharge, delivery, and routing.
- Required transport document data, shipment/on-board details, original/copy count, and signatures/capacity where visible.
- Insurance amount, currency, risks, date, and coverage where required.
- Required certificates, statements, endorsements, and document-specific conditions.
- Conflicts between documents and missing information needed to assess a requirement.

Every check must produce one of: **matches**, **potential discrepancy**, **cannot determine**, **not applicable**, or **requires specialist interpretation**. “Cannot determine” is not a pass.

### 8. Generate an evidence-backed discrepancy register

For every potential discrepancy, record:

- Unique discrepancy ID and category.
- The exact LC/amendment clause and source page.
- The exact presented-document wording and source file/page/location.
- A concise explanation of the difference or missing requirement.
- Why the check was triggered and the applicable rule/policy reference, if known.
- OCR confidence and any image-quality limitation.
- Severity/urgency according to bank policy (not an automated legal conclusion).
- Whether the issue is confirmed, unresolved, or requires specialist interpretation.
- Suggested reviewer action or question; do not automatically draft or send a refusal notice.

Avoid vague findings such as “documents inconsistent.” State the two compared values and where each appears. Distinguish a confirmed textual mismatch from a possible issue caused by poor image quality or uncertain OCR.

### 9. Human review and adjudication

1. Present the reviewer with the source image and extracted evidence side by side, the operative LC clause, check result, and discrepancy rationale.
2. Require the reviewer to confirm, dismiss, amend, or escalate each potential discrepancy, with a reason and user identity.
3. Require a second-level or specialist review for material ambiguity, low-confidence evidence, conflicting clauses, high-risk exceptions, or policy-defined cases.
4. Let only authorized staff determine document compliance, waiver/escalation route, customer communication, and payment/refusal disposition.
5. If a discrepancy is dismissed, retain the rationale and evidence. If confirmed, ensure the final list is consistent, complete, and reviewed under the bank's applicable notice and timing procedures.

**Gate:** no agent-only approval, refusal, waiver, payment, or external communication.

### 10. Finalize, communicate, and retain

1. Produce a reviewer-approved examination report containing case details, document inventory, checks performed, confirmed discrepancies, unresolved items, rule-set version, and reviewer approvals.
2. Have an authorized operator handle any notice or communication using approved bank templates and applicable deadlines. The agent must not send it autonomously.
3. Record the final disposition, timestamps, reviewer identities, overrides, escalations, and any resubmission or subsequent presentation.
4. Retain source images, OCR output, operative LC/amendments, check results, reviewer actions, and final report under the bank's retention schedule.
5. Make the complete case reproducible: a reviewer or auditor should be able to trace each finding back to the exact page and clause.

## Exception handling

| Condition | Required handling |
|---|---|
| Missing, unreadable, cropped, or low-quality page | Stop affected checks; request a clearer copy or manual review; preserve the limitation. |
| Low-confidence or conflicting OCR | Show the source image; require human confirmation before using the value. |
| LC or amendment linkage uncertain | Hold the case and route for transaction identification. |
| Amendment acceptance/applicability uncertain | Do not silently apply it; route for confirmation. |
| Clause ambiguous or inconsistent | Escalate to an authorized trade specialist; record the interpretation. |
| Document type uncertain or document outside configured scope | Route for manual classification and review. |
| Possible sanctions, fraud, forgery, or suspicious activity indicator | Refer to the separate authorized control process; do not resolve through document-checking logic. |
| Rule engine unavailable or version mismatch | Fail safely to manual review; record the issue and rule-set version. |

## Audit and control requirements

- Maintain an immutable event log for intake, processing, model/rule versions, extracted fields, check results, reviewer actions, overrides, and final disposition.
- Version OCR, extraction models, validation rules, and policy/rule configurations. Record which versions were used for every case.
- Provide role-based access, encryption, retention/deletion controls, and monitoring consistent with bank policy.
- Test the workflow against representative document types, handwriting, languages, poor scans, edge cases, and known discrepancy examples before production; track false positives and false negatives.
- Require controlled change management and periodic quality review. A model or rule update must not silently alter prior case results.

## Suggested discrepancy report format

| ID | Document / page | LC clause / page | Presented evidence | Requirement | Finding | Confidence / limitation | Reviewer decision |
|---|---|---|---|---|---|---|---|

## Problem statement

Letter of Credit document checking is a manual, time-consuming process. Staff must examine scanned documents, interpret the operative LC and amendments, compare multiple document types, and identify discrepancies under applicable rules. Poor scan quality, inconsistent layouts, and complex clauses can increase processing time and the chance of missed or incorrectly raised issues.

A controlled OCR- and rules-assisted workflow can extract and normalize relevant information, compare it with LC requirements, and present potential discrepancies with exact source evidence. Human reviewers retain responsibility for interpretation and final disposition. This can reduce repetitive effort, improve traceability, and support consistent review while preserving operational, compliance, and audit controls.
