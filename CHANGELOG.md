# Changelog

## 0.5.0 (draft - pending owner review and authorization; `VERSION` not yet bumped)

Agent-oriented specification rules: make the always-supplied rule set small, keep history out of specifications, and put a size ceiling on prose.

- Layout: `global/` is renamed `system/` (the controller already reads both and reported the legacy name). The conditional operational rules move to the controller's existing topic contract: `rules/backup/`, `rules/deployment/`, `rules/migration/`, `rules/release/`. A topic is supplied only when its name appears in the initiative's recorded `## Stack` or `## Compatibility` sections; governance and environment now instruct the agent to stop and ask for a topic that applies but was not supplied, so conditional never means unguarded. No controller change required.
- `system/writing.md` gains three rules: (1) a specification sentence is normative or a one-line evidence pointer - review verdicts, acceptance dates, retrospective notes, transitional implementation state, and mechanism detail belong to the record store, cited by id; (2) provenance tags (`[USER <date>]`, `[APPROVED <id>]`, `[OBSERVED <ref>]`, `[ASSUMPTION]`, `[UNKNOWN]`) replace prose that argues for a claim's origin; (3) size budgets (root spec ~800 words, requirement at most two sentences, delta = change + one-line rationale + decision reference, over-budget is re-cut before review).
- Governance and review rules adopt the tags: the claim classification list in `review-and-verification.md` points at the tag table instead of restating it; findings are recorded as belonging in the review record, never inline in the reviewed artifact; budget overflow is an Advisory finding to re-cut, not a blocking finding. Lifecycle states the same boundary once: a specification says what is true now; how it came to be true is history in the records.
- Proposals are tiered: `draft-proposal` keeps Why, Goals, Scope / Non-goals, Capabilities, Stack, Compatibility, Verification Strategy, and Open Questions required; Use Cases, Technical Approach, and Security / Failure Modes apply only when they carry content and are replaced by a one-line omission reason otherwise. Verified-nothing-exposed and open-question declarations stay one line. `refine-proposal` may re-cut a growing proposal instead of defending it, and now retains Capabilities in its section list.
- Gate definitions clarified on the owner's direction (2026-10-28): G1 is the specification gate (a proposal is the spec's draft form, reviewed the same way); the idea is defined as the plain, non-technical description of what is to be created; a delta carries no gate of its own - approving a delta is approving the specification state it produces, and an applied delta remains only as provenance. No G3 gate was introduced; acceptance stays a distinct human act in prose.
- A gate now passes only on an honest `- none` in `## Open Questions`: open questions are welcome while drafting, but each must become a recorded decision or be withdrawn before review-readiness or approval. Lifecycle, governance, environment, and the three gate review prompts carry the rule; the reviewer treats any listed question as blocking.
- Vocabulary residue from 0.4.0 fixed in agent-consumed text: `plan-tasks` no longer says "increment's checklist", governance and the deployment/release rules use deliverable/change wording, and each moved operational file opens with its conditional-topic header.

## 0.4.0

- A deliverable is one usable change to exactly one capability, created from the specification its delta produced. Its contract carries the acceptance criteria; its tasks are a plan and are never approved content, so re-cutting work cannot re-stale its own approval (D-27 in the consuming project).
- G2 is the deliverable gate. `prompts/actions/review-increment.md` is replaced by `review-deliverable.md`: a project dispatching the old name must rename it, and the controller fails closed on the missing required prompt rather than sending an agent out with less instruction.
- A capability is sliced into deliverables; an initiative does not have increments. `plan-default` names the capability and forbids a deliverable that spans two; `plan-delta` drafts a capability delta and states the specification revision it applies to.
- `## Capabilities` is a required proposal section: the branches a proposal creates or grows, with what each makes usable. Proposals open with an H1 title, because listings show the title rather than the path.
- New action `summarize-intent`: while a node has a specification, its idea is derived from it. `refine-idea` says so, so an agent no longer maintains two documents that can disagree.
- Requirements belong in a capability delta and acceptance criteria in a deliverable contract; the proposal review stops demanding either.

## 0.3.0

- Ideas and proposals carry a required `## Open Questions` section as their declared completeness state: one bullet per genuine question, or exactly `- none`. An absent or empty section is not completeness; the consuming controller refuses an idea revision that does not declare its state.
- Idea review now treats an absent or empty `## Open Questions` section as a blocking finding and judges whether `- none` is honest.

## 0.2.0

- Governance: one toolchain per project, no fetched code executed as a command, no copied shared instructions, and ranked ask points where a rule requires a question.
- Lifecycle and review: the written verification record may be waived by the owner for a phase; the checks and honest reporting of what was not tested may not.
- Migrations: scoped to state that exists outside the working copy and is not fully controlled. Compatibility work is asked about per change, before implementation, and never assumed in either direction.
- Ideas: a constraint the motive requires, or that follows from an already-fixed stack, is legitimate when written as a constraint rather than a chosen tool.
- Proposals: `## Stack` and `## Compatibility` are required sections.
- Removed editor workspace state from version control; it churned the source fingerprint.

## 0.1.0

- Read base prompts directly; project files are optional overrides, not copies created by init.
- Separate default refinement requests from neutral author-role context. Opening a conversation does not request a revision.
- Document resolved rules/prompts, source/hash provenance, and explicit startup choice.
