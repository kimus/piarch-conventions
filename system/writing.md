# Technical writing

Use ASD-STE100-inspired English for specifications, procedures, rules, and review reports. This policy borrows clarity principles; it does not assert conformity with the complete standard or its dictionary. Strict ASD-STE100 compliance requires a separate review against the complete standard and approved vocabulary, and a sentence-length check alone cannot establish it.

## Language

- Use short sentences and active voice.
- Use one instruction per procedural sentence.
- Put prerequisite conditions before the action that depends on them.
- Use the same term for the same concept. Define project terms in the glossary.
- Identify the actor, action, object, and relevant condition in requirements.
- Give requirements and acceptance criteria stable IDs.
- Avoid subjective terms such as fast, intuitive, robust, and user-friendly unless an approved criterion defines them.
- Preserve uncertainty. Do not turn may into will without evidence.
- Mark missing values as Unknown or To decide. Ask before using invented values.
- Separate required behavior from examples and non-binding suggestions.
- Use tables when they make criteria, evidence, and decisions easier to compare.
- Use Markdown for document structure. Leave code syntax, identifiers, and quoted source text intact.

## A document states what is true now

Every sentence in a specification, proposal, or contract is either normative or a one-line pointer to where its evidence lives. This belongs in the record store — change records, ledger, review records, decision register — never inline in a specification body:

- Review findings, verdicts, reviewer identities, and run identifiers: cite them by id where the record lives.
- Acceptance dates, decision histories, and retrospective notes ("recorded backwards", "written after the references that use it"): keep them in the decision register or change record.
- Transitional implementation state, superseded wording, and mechanism detail (code paths, queries, internal names): these belong in the change record or the code.
- A deferred question carries one line, an owner, and a decision reference. Its resolution narrative is recorded once, where the decision lives, and cited by id.

Correct a normative sentence by editing it; append-only rules protect history, not prose. Where a rule must survive a correction, the rule is reworded and a change record carries why.

## Provenance tags

Classify a claim with one tag, not a paragraph about how it came to be believed:

| Tag | Meaning |
| --- | --- |
| `[USER <date>]` | stated by the user |
| `[APPROVED <id>]` | accepted through a named decision or gate |
| `[OBSERVED <ref>]` | checked in a run, test, or record named by ref |
| `[ASSUMPTION]` | believed, not confirmed |
| `[UNKNOWN]` | open; name the owner and the resolving point |

A tag is the whole classification. Do not restate it in prose beside the claim, and do not hedge a tagged claim with narrative about what does or does not protect it. Facts carried by the ledger or a content fingerprint need no tag. Agreement between models is never evidence; cite the source instead.

## Size budgets

Budgets are drafting constraints. A document over budget is re-cut before review; exceeding one requires a normative reason, not a defensive one.

- Root specification: intent register, capability list, design principles — about 800 words. Branch specifications state requirements, not narrative.
- One requirement: at most two sentences. One scenario per behavior a check can fail.
- A delta: the change against the base text, one line of rationale, a decision reference.
- Open questions: one line each, with owner and resolving point. The discussion that answered or deferred it stays in its record.
- Three consecutive prose paragraphs in a specification signal the content belongs in a design document or a change record.
