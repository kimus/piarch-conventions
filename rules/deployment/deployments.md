# Deployment rules

*Conditional rule set (topic: deployment). Supplied when the initiative's recorded Stack or Compatibility section names it; when it applies and was not supplied, stop and ask.*

Define environments and exact commands in `docs/operations.md`. Use `<shared>/templates/release-record.md` for each deployment or release operation. Apply only the sections relevant to that operation.

## Required before execution

- Identify the environment, account or tenant, region, services, current revision, and intended target revision. Confirm the actual command targets that environment.
- Record the immutable artifact identifier, source revision, configuration revision, and required secrets by name. Do not put secret values in the plan.
- Define prerequisites, execution order, health checks, observation period, failure thresholds, and recovery actions before deployment. Obtain agreement on consequential thresholds instead of inventing them.
- State whether the operation changes data, schemas, infrastructure, permissions, external integrations, or user-visible behavior. Review applicable security, migration, and backup rules.
- Define the operator, required access, approval scope, and any allowed automated recovery. Passing tests or acceptance of a deliverable does not itself authorize a production deployment.
- Use authorization already provided for the exact operation, artifact, environment, and recovery scope. Request a decision only when that scope is absent, changed, expired, or unclear.

## Required execution and evidence

- Use the reviewed, repeatable deployment path. Avoid unrecorded manual changes to live hosts or services.
- Promote the tested immutable artifact where possible. If the platform builds per environment, document that behavior and verify the resulting artifact.
- Rehearse changes with material operational risk in a representative non-production environment. Record any difference that limits the rehearsal's evidence.
- Prevent concurrent operations that can conflict. Verify that CI or the platform supplies the necessary lock or coordination.
- Check application behavior, health signals, relevant security controls, and integration state after deployment. A successful command exit is insufficient.
- Stop further rollout when agreed checks fail. Execute only authorized recovery. Preserve evidence and report the observed state if recovery is not authorized or feasible.
- Record operator, time, target, artifact, configuration, checks, outcome, and any deviations. Report degraded or partially deployed state explicitly.

## Recovery

State whether recovery uses an application rollback, configuration rollback, forward fix, data restore, or a combination. Verify application compatibility with the resulting schema. A previous application version is not a safe rollback if the database has become incompatible.

A restore can overwrite newer writes. Do not treat it as a routine application rollback. Record the recovery point, expected data loss, reconciliation approach, and authorization before restoring persistent data.
