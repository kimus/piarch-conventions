# Migration rules

*Conditional rule set (topic: migration). Supplied when the initiative's recorded Stack or Compatibility section names it; when it applies and was not supplied, stop and ask.*

Apply these rules only when the state a change touches exists outside that working copy in a form the project does not fully control: a published release, another user, a deployed database, shared configuration, or data another system reads. Record project-specific tooling and procedures in `docs/operations.md`.

Where no such state exists, change the format directly. Do not add migration files, compatibility readers, expand-and-contract staging, or rollback rehearsal for state that exists only to be replaced. Ask the user before writing any of it, once per change, before implementation. Do not assume compatibility is wanted, and do not assume it is unwanted.

When the state above does exist, the rules below apply in full and the same question is asked before implementation rather than answered by assumption.

## Required planning

- Describe the current state, target state, affected data, expected volume, and application compatibility during rollout.
- Use versioned migration files with stable identifiers. Do not alter or delete migrations already applied to a shared or production environment. Add a corrective migration instead.
- Separate migration preparation from execution. Implementation approval authorizes execution only if its scope explicitly includes the target environment and migration identifiers.
- Define ordering, deployment dependencies, estimated operational impact, lock behavior, time limits, and validation queries. Validate assumptions on representative data.
- Identify destructive or irreversible steps explicitly. Explain data loss and the recovery procedure before approval.
- Before a production or destructive shared-data mutation, identify a usable recovery point and the restore evidence required by `backups.md`. An untested backup file is not proof of recoverability.

## Required implementation and rehearsal

- Prefer compatible expand, migrate, and contract stages when old and new application versions can overlap. Do not remove an old field or behavior before dependent consumers have moved.
- Test against a representative starting version and sanitized or synthetic data. Test the supported upgrade paths, important invariants, and the resulting application behavior.
- Determine transaction and rollback behavior from the actual engine. Do not assume every schema operation is transactional or safely reversible.
- Make large backfills resumable and observable. Define batch limits, progress tracking, retry behavior, and duplicate handling where needed.
- Prevent concurrent migration execution and record which migrations completed. Use the framework's migration history rather than a claim of idempotency alone.
- Test a rollback when it is supported. When it is unsafe or impossible, document and rehearse a forward fix or restore path instead. Do not invent a down migration merely to complete a template.

## Required execution evidence

Record the target, migration identifiers and checksums, preflight checks, backup/recovery reference, authorization, execution results, and post-migration validation. Monitor the relevant error, latency, lock, and data-integrity signals.

If a migration fails, establish what committed before retrying. Do not blindly rerun a partially applied migration or automatically apply a destructive reverse operation. Stay within the approved recovery scope.
