# PiArch conventions

Reusable project conventions and editable agent role/action prompts for Piccolo Architect (`piarch`). This is an independent repository, not a folder or submodule inside piarch.

Status: initial draft. Publication does not establish independent review or approval of any consuming project's baseline.

## Use from piarch

During guided `piarch init`, select this GitHub repository or a local checkout. Scripted setup can pass `--conventions github/kimus/piarch-conventions` or `--conventions /path/to/piarch-conventions`.

Selecting a GitHub source during init explicitly fetches it into piarch's conventions cache. Local paths do not require Git. Review selected sources before trusting them. Conventions contain instructions, not permission to bypass controller controls.

Piarch reads prompts directly from the selected base source; init does not copy them. A user-created `.piarch/prompts/roles/<role>.md` or `.piarch/prompts/actions/<action>.md` overrides only that file. Missing files fall back to the base source, then to built-in defaults if the base lacks that prompt. An explicitly configured but unavailable base is an error, not a reason to ignore its rules. Existing local files are never removed or overwritten; earlier generated copies therefore continue to act as overrides until the owner chooses to remove them.

The controller assembles selected `global/*.md`, the managed project's own instructions (not parent projects), and effective role/action prompts into model context. It records resolved source paths and hashes, and `piarch conventions check` is the session gate: it reports the fingerprint, the assessed value, and any layout the controller cannot honor, including a missing prompt or a nested rule directory, which the loader does not walk. Do not resolve this source with a separate script or execute code fetched from it. Optional defaults are not sent until selected. Prompt symlinks are not required or created. Context is resolved for an operation/session; edits take effect in a fresh session. An updated base fingerprint must be reviewed and recorded with `piarch assess-conventions` before another agent operation. Review proposed shared changes separately from local overrides.

Role prompts describe the agent's responsibilities. Action prompts describe a requested operation. Loading context is not a request to revise an artifact. An opened conversation must wait for a user instruction or an explicit choice to send a default action.

## Contents

- `global/`: governance, lifecycle, technical writing, security, review/verification, and relevant operational rules. A rule that applies only in some situations says so and names the situation; compatibility and migration rules apply only where state exists outside the working copy that the project does not control.
- `prompts/roles/`: author and reviewer defaults.
- `prompts/actions/`: refinement, proposal drafting, planning, gate-specific reviews, review output, and reconciliation. Proposal drafting and refinement require `## Stack` and `## Compatibility` sections, so a project records what it builds on and what a change may break.
- `project-template/`: minimal project-local adoption instructions.
- `templates/`: human-readable review and operational records.

Only idea review (G0) is nontechnical. Proposal (G1) and increment (G2) reviews are fully technical. Reviewer verdicts, agent output, and files named approval are never human authorization. Actual tool restrictions, artifact validation, and approval gates remain controller responsibilities; editable Markdown is not a sandbox.

## Maintain

Keep project-specific exceptions local. Change reusable rules through a reviewed, user-authorized change. Consuming projects reassess changed source fingerprints; fetching new conventions must not silently replace their customized prompts or approve new work.

The conventions do not depend on an OpenSpec runtime, CLI, generated skill, or schema. Delta terminology is inspired by OpenSpec; piarch owns its lifecycle independently.

## Provenance and licensing

Adapted at the owner's direction from the owner's existing Agent Conventions starter and piarch prompt definitions. The security, writing, review, and operational rules retain that starter's obligations; lifecycle references are adapted to project-local change records. The previous source is not modified by this repository.

No software license has been selected yet. Public visibility alone does not grant an open-source license. No release tag or package is published by the initial repository push.
