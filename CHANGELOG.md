# Changelog

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
