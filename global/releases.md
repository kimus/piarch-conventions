# Release and versioning rules

## Required Semantic Versioning policy

Use Semantic Versioning 2.0.0: `MAJOR.MINOR.PATCH`. Define the public compatibility contract in `conventions/project.md`. It can include APIs, CLI behavior, configuration, persisted formats, and other supported interfaces. An internal sprint number or change-record name is not a release version.

For stable versions at or above `1.0.0`:

- Increment MAJOR for an incompatible change to the public contract. Reset MINOR and PATCH to zero.
- Increment MINOR for backward-compatible functionality or public deprecation. Reset PATCH to zero.
- Increment PATCH for backward-compatible bug fixes.
- Use the highest required bump when a release contains several changes. A security fix can still require a major bump if it breaks compatibility.

Use prerelease identifiers such as `1.2.0-rc.1` for candidate releases. Build metadata such as `+build.42` identifies a build but does not change version precedence. Do not replace a published release's contents; issue a new version.

Before `1.0.0`, the public API is unstable under SemVer. This conventions repository adopts an additional explicit policy: incompatible changes and new capabilities advance `0.MINOR.0`; compatible corrections advance `0.MINOR.PATCH`. Each project must document its own pre-1.0 policy and readiness criteria for `1.0.0`.

Reference: [Semantic Versioning 2.0.0](https://semver.org/spec/v2.0.0.html). The pre-1.0 bump policy above is a project convention, not an extra SemVer requirement.

## Required release preparation

- Identify the included accepted changes and their verification evidence. A sprint can produce no release or several releases.
- Record the current version, proposed version, compatibility assessment, and reason for the bump.
- Use the project's declared version files as the source of truth. Keep package metadata, lockfiles where applicable, release notes, and artifact version labels consistent. Do not introduce a VERSION file when the project already has a suitable version source unless that change is approved.
- Record user-visible changes, fixes, breaking changes, security notes, required migrations, and upgrade steps. Do not expose secrets or unnecessary exploit details in public notes.
- Build from a known source revision using the recorded toolchain and lockfiles. Record artifact digests and the required CI evidence. Identify environment-dependent build behavior.
- Confirm applicable security findings are resolved or have approved, scoped exceptions. Review deployment, migration, and recovery readiness.
- Prepare the release locally before requesting any missing publication decision. Preserve existing authorization when it covers the concrete version, target, and scope.

## Publication and deployment

Use immutable release identifiers and the project's documented tag convention; default to Git tags such as `v1.2.0`. Publish tags or packages only within authorized scope. Do not force-move published release tags or silently replace artifacts.

Record publication separately from deployment. Identify each environment's deployed artifact; a published release is not proof that production runs it. Run the post-deployment checks required by `deployments.md`.

If a release is defective, use the approved rollback, forward fix, or package withdrawal procedure. Keep history traceable. Do not reuse the version number. A hotfix follows the same applicable security, verification, and recovery rules; any expedited exception must be explicit.

## This conventions repository

`VERSION` is the version source. `CHANGELOG.md` records changes. Updating local files prepares a candidate; it does not create a published release or Git tag. Projects reference the current shared source and reassess global changes at lifecycle checkpoints. Record the last assessed commit and content fingerprint; do not copy or pin global rules in each project.
