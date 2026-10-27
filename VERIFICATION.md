# Initial-source verification

The owner requested a separate `kimus/picarch-conventions` repository and explicitly chose public visibility. This authorizes the initial public source push, not a release tag, adoption by every consuming project, independent review, or implementation acceptance.

Prepared from the owner's existing conventions and piarch prompt definitions. The previous authoritative shared source remains unchanged. The mandatory rules retain separate authorization, review, evidence, security, and operational obligations. The lifecycle is adapted to piarch's independent project-local records without introducing an external workflow runtime dependency.

Executed checks before the initial source push:

- All 14 role/action prompt files match piarch's embedded fallback copies.
- No symlinks occur in the prepared public tree.
- No absolute home-directory paths or credential-shaped values were found by the targeted prepared-tree scan. This is not a comprehensive secret-audit guarantee.
- Piarch's tests passed for local-source initialization, missing-prompt fallback, custom prompt usage/preservation, source normalization, source symlink refusal, and cache refresh/dirty-cache refusal using local Git fixtures.

The consumer integration and real GitHub-source checks are recorded separately in piarch. Independent review remains Pending. License selection remains Pending; public visibility is not an open-source license grant.
