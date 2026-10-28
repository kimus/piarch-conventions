# Changelog

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
