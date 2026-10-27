# Source verification

## Repository-name correction (2026-10-27)

The repository was first published as `kimus/picarch-conventions`, a typo for `piarch`. On the owner's instruction the GitHub repository, this checkout directory, the git remote, piarch's guided-init default, the conventions cache path, and consuming project configurations now use `piarch-conventions`. Records written before the correction keep the original spelling as the audit trail of what existed at the time; they are not rewritten.

Verified after the rename: `gh repo view kimus/piarch-conventions` reports PUBLIC at https://github.com/kimus/piarch-conventions, the previous name still redirects until a repository with that name is created, and `git fetch origin` succeeds against the new remote URL. License selection and independent review remain Pending.

## Runtime-resolution correction

The owner clarified that init must not copy prompts. Base prompts are now read directly, with optional user-created project overrides and built-in fallback for missing base files. The initial-copy behavior below is historical, not the current policy.

Refine action defaults are explicit requests offered only by user choice, not always-on role context. The controller supplies resolved base rules and effective role instructions to agents, records paths/hashes, and keeps conversation startup idle until the user sends or confirms an action. The source remains independent of controller permissions and approval enforcement.

## Initial publication checks

The owner requested a separate `kimus/picarch-conventions` repository (the name was later corrected to `piarch-conventions`; see above) and explicitly chose public visibility. This authorizes the initial public source push, not a release tag, adoption by every consuming project, independent review, or implementation acceptance.

Prepared from the owner's existing conventions and piarch prompt definitions. The previous authoritative shared source remains unchanged. The mandatory rules retain separate authorization, review, evidence, security, and operational obligations. The lifecycle is adapted to piarch's independent project-local records without introducing an external workflow runtime dependency.

Executed checks before the initial source push:

- All 14 role/action prompt files match piarch's embedded fallback copies.
- No symlinks occur in the prepared public tree.
- No absolute home-directory paths or credential-shaped values were found by the targeted prepared-tree scan. This is not a comprehensive secret-audit guarantee.
- Piarch's tests passed for local-source initialization, missing-prompt fallback, custom prompt usage/preservation, source normalization, source symlink refusal, and cache refresh/dirty-cache refusal using local Git fixtures.

The consumer integration and real GitHub-source checks are recorded separately in piarch. Independent review remains Pending. License selection remains Pending; public visibility is not an open-source license grant.
