# Specification and delivery lifecycle

## Establish intent and environment

Capture the original request. Read existing evidence and selected conventions. Record goals, users, scope/non-goals, constraints, assumptions, decisions, and open questions. Define the environment, security boundaries, relevant operations, and UI design where applicable. Do not turn agreement with a direction into approval of draft details.

## Gates

- G0 idea: review nontechnical clarity, simplicity, and consistency. Do not demand technical design here. A ready result permits proposal drafting where the project's controller supports automatic promotion; it does not authorize implementation.
- G1 proposal: conduct full technical review of design, feasibility, dependencies/environment, data/control flow, security, failure/recovery, and verification. Resolve implementation-critical unknowns. Human baseline approval remains separate from reviewer readiness.
- G2 deliverable: one usable change to one capability, created from the specification its delta produced. The contract states what becomes usable and the acceptance criteria; that is the approved content. Tasks are the plan for reaching them and are never approved content, so re-cutting work cannot re-stale its own approval. Review technically and obtain explicit human authorization for that exact deliverable before implementation.

## Deliver and verify

Use project-local change records for scope, review, actual authorization, verification evidence, and user decisions. No particular external workflow runtime is required. Only the controller's supported behavior may be claimed as enforced. An instruction or a named file is not proof of a transition.

Implement only authorized scope. Run the checks the contract names and report each criterion as PASS, FAIL, or NOT CHECKED with exact commands, fixtures, results, and tested revisions. For UI changes, retain terminal/screen evidence. A project may waive the written record with its owner's authorization, never the checks: report the same facts in the conversation and reconcile documents when the work is approved. Waiving the record never softens a statement about what was not tested. Passing checks do not prove criteria that were not tested. Preserve interrupted or unknown outcomes; do not infer success or retry uncertain mutations blindly.

Obtain independent outcome review and actual user acceptance. Keep implementation approval, acceptance, publication, deployment, migration, and restore authorization distinct. Reconcile accepted specifications and retain provenance/history. Delivered changes and applied deltas must not be silently rewritten. Record lessons and propose reusable convention improvements separately, grouped into one reviewed source release rather than one release per lesson.

## Conversations and prompts

Role instructions and supplied context do not constitute a request to revise a document. Do not start a model call just because a conversation opened unless the user explicitly selected an initial action. Discuss questions without replacing artifacts. Requested revisions belong to completed qualifying turns, not to exit. Ending a session must not ask a model to invent a final revision.
