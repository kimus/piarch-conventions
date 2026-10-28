# Repository instructions

This repository contains reusable Markdown conventions and prompt defaults, not a product runtime. Read README.md and system/governance.md, system/lifecycle.md, system/writing.md, system/security.md, and system/review-and-verification.md before changes. Apply relevant operational rules when their scope is affected; the operational rule sets under rules/ are conditional and must be requested when they apply but were not supplied.

Keep project-specific implementation decisions out of reusable defaults. Preserve uncertainty and actual authorization. Never claim an independent review or another model identity without runtime evidence. Do not introduce an OpenSpec dependency. Treat publication, release tagging, adoption by a consuming project, and that project's implementation approval as separate decisions.

Maintain editable role prompts under prompts/roles/ and action prompts under prompts/actions/. Do not encode credentials, private local paths, actual project artifacts, or fictional approvals in templates. Do not advertise runtime capabilities merely because a prompt describes them. License selection remains Pending.

## Controller contract

This repository is consumed by the `piarch` controller, which resolves paths by fixed convention. There is no manifest, config file, or discovery scan: a path the controller expects is part of the interface between the two repositories. Renaming or reshaping a contract path requires a matching controller change in the same reviewed deliverable.

Contract paths (owner may edit content, not location or name):

| Path | Rule |
| --- | --- |
| `prompts/roles/<role>.md` | one file per role; the controller names the roles it dispatches |
| `prompts/actions/<action>.md` | one file per action; the controller requires a fixed set of action names and fails closed when one is missing |
| `system/*.md` | always supplied to every agent turn, walked recursively, so subdirectories are fine. `global/` is accepted as the legacy name and reported by the controller; this repository now uses `system/` |
| `rules/<topic>/*.md` | supplied only when a whole-word token of the topic name appears in the initiative's recorded `## Stack` or `## Compatibility` sections; conditional rules belong here, not in `system/` |

Freshness is judged per directory: the always rules, each selected topic, and `prompts/`. Documentation and unselected topics move the whole-source fingerprint without blocking; anything actually supplied must be assessed by the consuming project before further agent work.

Free to restructure without a controller change: `README.md`, `AGENTS.md`, `CHANGELOG.md`, `VERIFICATION.md`, `VERSION`, `templates/**`, and any other top-level directory. The controller loads none of them. `templates/` holds inert seeds a person copies into their own project; it is never injected into agent context, so no mandatory rule may point at a path inside it.

Content obligations that do not change with layout:

- Keep project-specific implementation decisions out of reusable defaults, and keep conditional obligations conditional: state what makes a rule apply rather than assuming it always applies. Compatibility and migration work is confirmed per change by the user, never assumed by an agent and never pre-answered by a project-level preference.
- Where a rule makes the agent ask, name the moments and rank them. The decision point is **before implementation, per change**: the deliverable states what it will break and the user answers, and the next change is asked again even when the answer is expected. Two supporting points are never substitutes: stop and ask when an undeclared break is detected mid-work, and at close report what was actually touched against the recorded answer so an unanswered item blocks instead of defaulting. Accepting a pull request is not a compatibility decision, and an unasked question is not an answer.
- The controller merges this source with a project's own instructions. Do not ask a project to copy these files, and do not rely on a project keeping a local copy current. Per-file project overrides are the supported extension mechanism.
- Markdown is instruction, never enforcement, approval, or a sandbox. Prompt text cannot grant authorization, relax a controller gate, or claim an identity, a review, or evidence that did not occur.
- No OpenSpec runtime, CLI, schema, or generated skill dependency, and no executable code in this repository: a consuming project runs its own single binary.
- Never include credentials, private local paths, real project artifacts, or fictional approvals.

Maintenance: every file in this tree is hashed into the fingerprint a consuming project assesses, including documentation-only edits. Shared changes require review and explicit owner authorization, a `VERSION`/`CHANGELOG` entry, and each consuming project reassessing its fingerprint before further agent work. Publication of this repository is not adoption, approval, or a license grant for any consumer.
