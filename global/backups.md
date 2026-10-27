# Backup and restore rules

Projects with persistent data must define recovery needs in `docs/operations.md`. A stateless project can mark data backup requirements Not applicable with a reason; identify any configuration or external state that still needs recovery.

## Required policy

- Identify the data and configuration to protect, exclusions, owners, storage locations, and recovery dependencies.
- Obtain an approved recovery point objective (RPO: acceptable data loss in time) and recovery time objective (RTO: acceptable recovery duration). Use these to choose schedule, retention, and restore-test frequency. Do not invent business tolerances.
- Encrypt sensitive backups and restrict access. Keep required recovery keys accessible through an approved mechanism that does not depend solely on the failed system.
- Keep at least one protected recovery copy outside the live application's write and deletion authority. Select an offline, immutable, or separately isolated mechanism appropriate to the project, and document residual risks.
- Monitor failed, missing, or stale backups. A scheduled job does not prove a usable backup exists.
- Define retention and deletion rules, including handling of sensitive data. Do not delete recovery points early or change retention without authorization.

## Required recovery evidence

Test restoration into an isolated environment before relying on a new backup mechanism and at the approved recurring interval. Restore the required components and verify application behavior and important data invariants. Record the backup identifier, data timestamp, integrity checks, measured recovery time, and limitations.

Before a risky mutation, confirm the selected recovery point exists, satisfies the approved RPO, and has applicable restore-test evidence. Resolve gaps or obtain an explicit documented exception before proceeding. Do not restore over live data as a backup test.

Before a real restore, identify the target, selected recovery point, expected data loss, dependent systems, and treatment of newer writes. Prevent concurrent writes where the recovery procedure requires it. Record actual authorization and validate the recovered state before reopening normal access.

Repository history, replication, and file synchronization alone do not establish a recoverable backup. Treat a successful backup command and a successful restore test as different evidence.

Reference: [CISA StopRansomware Guide](https://www.cisa.gov/stopransomware/ransomware-guide). This project policy adapts recovery practices to the actual environment; it does not claim certification.
