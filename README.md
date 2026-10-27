# PicArch conventions

Reusable project conventions and editable agent role/action prompts for Piccolo Architect (`piarch`). This is an independent repository, not a folder or submodule inside piarch.

Status: initial draft. Publication does not establish independent review or approval of any consuming project's baseline.

## Use from piarch

During guided `piarch init`, select this GitHub repository or a local checkout. Scripted setup can pass `--conventions github/kimus/picarch-conventions` or `--conventions /path/to/picarch-conventions`.

Selecting a GitHub source during init explicitly fetches it into piarch's conventions cache. Local paths do not require Git. Review selected sources before trusting them. Conventions contain instructions, not permission to bypass controller controls.

Piarch seeds `.piarch/prompts/roles/` and `.piarch/prompts/actions/` from this source. Missing known prompts receive built-in defaults. Existing project-local prompt files are never overwritten. Edit those local copies for project-specific behavior; propose reusable improvements here separately.

Role prompts describe the agent's responsibilities. Action prompts describe a requested operation. Loading context is not a request to revise an artifact. An opened conversation must wait for a user instruction or an explicit choice to send a default action.

## Contents

- `global/`: governance, lifecycle, technical writing, security, review/verification, and relevant operational rules.
- `prompts/roles/`: author and reviewer defaults.
- `prompts/actions/`: refinement, proposal drafting, planning, gate-specific reviews, review output, and reconciliation.
- `project-template/`: minimal project-local adoption instructions.
- `templates/`: human-readable review and operational records.

Only idea review (G0) is nontechnical. Proposal (G1) and increment (G2) reviews are fully technical. Reviewer verdicts, agent output, and files named approval are never human authorization. Actual tool restrictions, artifact validation, and approval gates remain controller responsibilities; editable Markdown is not a sandbox.

## Maintain

Keep project-specific exceptions local. Change reusable rules through a reviewed, user-authorized change. Consuming projects reassess changed source fingerprints; fetching new conventions must not silently replace their customized prompts or approve new work.

The conventions do not depend on an OpenSpec runtime, CLI, generated skill, or schema. Delta terminology is inspired by OpenSpec; piarch owns its lifecycle independently.

## Provenance and licensing

Adapted at the owner's direction from the owner's existing Agent Conventions starter and piarch prompt definitions. The security, writing, review, and operational rules retain that starter's obligations; lifecycle references are adapted to project-local change records. The previous source is not modified by this repository.

No software license has been selected yet. Public visibility alone does not grant an open-source license. No release tag or package is published by the initial repository push.
