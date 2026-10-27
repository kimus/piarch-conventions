# Independent review and verification

## Contract review

The reviewer must be a separate agent session using a different model from the author. Record both model identifiers as reported by the runtime or user. If identity cannot be established, record Unknown and keep the independence check unresolved.

Read the original request, proposed documents, applicable conventions, and relevant sources or code. Inspect independently before relying on the author's conclusions. Do not execute mutating project scripts during contract review.

Check these questions:

- Does the specification address the user's goal?
- Could two reasonable implementations satisfy the wording but behave differently?
- Are actors, conditions, outputs, failure cases, and boundaries explicit?
- Can each acceptance criterion fail through a repeatable check?
- Are targets supported by the user, a source, or an approved decision?
- Does the approach assume unavailable tools, data, services, or capabilities?
- Do project, design, and change documents contradict each other?
- Does the increment fit one meaningful user checkpoint?
- Are UI states, accessibility, and visual references sufficient when applicable?
- Are applicable security controls and denied-access scenarios specified?
- Are deployment targets, authorization, health checks, and recovery triggers explicit?
- Are migration compatibility, partial failure, backup freshness, and restore evidence adequate?
- Does the proposed SemVer bump match the declared compatibility contract?

Classify claims as User requirement, Observed fact, Approved decision, Assumption, or Unknown. Use direct source references for factual claims. Agreement between models is not evidence that a factual claim is true.

For each finding, give an ID, location, evidence, consequence, and a correction or focused question. Mark a finding Blocking when it can change scope, correctness, acceptance, or a material decision. Mark it Advisory when it can safely wait. Do not invent findings to fill a quota.

The author can draft responses and corrections. Only an actual independent review can close the review requirement. Keep the previous findings and their resolutions traceable. Do not have the author silently rewrite the reviewer's verdict.

## Outcome verification

Use the approved contract as the reference. Verify requirements through tests, observed output, approved visual references, or a repeatable manual procedure. Check failures and boundary conditions that matter to the increment.

Record the command or procedure, input or fixture, expected result, actual result, and tested revision. For UI work, include relevant screenshots or other reviewable artifacts and the path to them. Keep credentials and personal data out of evidence.

Checked task boxes and an agent's confidence are not verification. A passed test covers only the behavior it checks. State limitations.

The outcome reviewer examines the implementation and evidence. Run non-destructive checks where appropriate. Disclose checks that cannot be repeated. The reviewer can recommend acceptance; the user makes the acceptance decision.

Load applicable security and operational rules. Do not run production deployments, migrations, restores, or publication as an implicit verification step. Review operation records and available runtime evidence. Run an operation only if existing authorization explicitly covers that target and action. Check security findings, migration results, backup/restore evidence, version consistency, and publication/deployment state where applicable.
