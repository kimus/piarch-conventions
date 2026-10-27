# Repository instructions

This repository contains reusable Markdown conventions and prompt defaults, not a product runtime. Read README.md and global/governance.md, global/lifecycle.md, global/writing.md, global/security.md, and global/review-and-verification.md before changes. Apply relevant operational rules when their scope is affected.

Keep project-specific implementation decisions out of reusable defaults. Preserve uncertainty and actual authorization. Never claim an independent review or another model identity without runtime evidence. Do not introduce an OpenSpec dependency. Treat publication, release tagging, adoption by a consuming project, and that project's implementation approval as separate decisions.

Maintain editable role prompts under prompts/roles/ and action prompts under prompts/actions/. Do not encode credentials, private local paths, actual project artifacts, or fictional approvals in templates. Do not advertise runtime capabilities merely because a prompt describes them. License selection remains Pending.

## Controller contract

This repository is consumed by the `piarch` controller, which resolves paths by fixed convention. There is no manifest, config file, or discovery scan: a path the controller expects is part of the interface between the two repositories. Renaming or reshaping a contract path requires a matching controller change in the same reviewed increment.

Contract paths (owner may edit content, not location or name):

| Path | Rule |
| --- | --- |
| `prompts/roles/<role>.md` | one file per role; the controller names the roles it dispatches |
| `prompts/actions/<action>.md` | one file per action; the controller requires a fixed set of action names and fails closed when one is missing |
| `system/*.md` (currently `global/*.md`) | always supplied to every agent turn; flat `.md` files, not nested subdirectories |
| `rules/<topic>/*.md` | supplied only when the topic is selected by the consuming project's recorded state; conditional rules belong here, not in `system/` |

Free to restructure without a controller change: `README.md`, `AGENTS.md`, `CHANGELOG.md`, `VERIFICATION.md`, `VERSION`, `templates/**`, and any other top-level directory. The controller loads none of them. `templates/` holds inert seeds a person copies into their own project; it is never injected into agent context, so no mandatory rule may point at a path inside it.

Content obligations that do not change with layout:

- Keep project-specific implementation decisions out of reusable defaults, and keep conditional obligations conditional: state what makes a rule apply rather than assuming it always applies. Compatibility and migration work is requested by a project, never assumed by an agent, until that project has published state outside its own working copy.
- The controller merges this source with a project's own instructions. Do not ask a project to copy these files, and do not rely on a project keeping a local copy current. Per-file project overrides are the supported extension mechanism.
- Markdown is instruction, never enforcement, approval, or a sandbox. Prompt text cannot grant authorization, relax a controller gate, or claim an identity, a review, or evidence that did not occur.
- No OpenSpec runtime, CLI, schema, or generated skill dependency, and no executable code in this repository: a consuming project runs its own single binary.
- Never include credentials, private local paths, real project artifacts, or fictional approvals.

Maintenance: every file in this tree is hashed into the fingerprint a consuming project assesses, including documentation-only edits. Shared changes require review and explicit owner authorization, a `VERSION`/`CHANGELOG` entry, and each consuming project reassessing its fingerprint before further agent work. Publication of this repository is not adoption, approval, or a license grant for any consumer.
