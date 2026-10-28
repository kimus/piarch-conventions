# Specification and delivery lifecycle

## Establish intent and environment

The idea is the plain, non-technical description of what is intended to be created. It carries no requirements, acceptance criteria, or technical content; those belong to the specification.

Capture the original request. Read existing evidence and selected conventions. Record goals, users, scope/non-goals, constraints, assumptions, and decisions. Define the environment, security boundaries, relevant operations, and UI design where applicable. Do not turn agreement with a direction into approval of draft details.

## Gates

A gate passes only when the artifact's `## Open Questions` section declares exactly `- none` and independent review has no unresolved blocking finding. Questions are welcome while drafting and stay explicit; to pass its gate, each one is resolved into a recorded decision or withdrawn. An open question is blocking by definition, and softening its wording is dishonesty, not progress. A reviewer READY verdict never grants approval; only the human authorization bound to the exact artifact set does.

- G0 idea: review the idea as a plain non-technical description of what is to be created - clarity, simplicity, and consistency only. Do not demand technical design here. A ready result permits proposal drafting where the project's controller supports automatic promotion; it does not authorize implementation.
- G1 spec: full technical review of the node's specification - design, feasibility, dependencies/environment, data/control flow, security, failure/recovery, and verification. Resolve implementation-critical unknowns; a proposal is the specification's draft form and shares this gate. Human baseline approval remains separate from reviewer readiness.
- A delta is a change to a specification. It carries no gate of its own: reviewing and approving a delta is reviewing and approving the specification state it produces. Once approved it is merged into the specification, and the merged delta remains only as the provenance record.
- G2 deliverable: one usable change to one capability, created from the specification its delta produced. The contract states what becomes usable and the acceptance criteria; that is the approved content. Tasks are the plan for reaching them and are never approved content, so re-cutting work cannot re-stale its own approval. Review technically and obtain explicit human authorization for that exact deliverable before implementation.

## Deliver and verify

Use project-local change records for scope, review, actual authorization, verification evidence, and user decisions. No particular external workflow runtime is required. Only the controller's supported behavior may be claimed as enforced. An instruction or a named file is not proof of a transition. A specification states what is true now; how it came to be true - reviews, acceptance dates, superseded wording, retrospective notes - is history, and history lives in these records, the ledger, or the decision register, cited by id when a specification needs it.

Implement only authorized scope. Run the checks the contract names and report each criterion as PASS, FAIL, or NOT CHECKED with exact commands, fixtures, results, and tested revisions. For UI changes, retain terminal/screen evidence. A project may waive the written record with its owner's authorization, never the checks: report the same facts in the conversation and reconcile documents when the work is approved. Waiving the record never softens a statement about what was not tested. Passing checks do not prove criteria that were not tested. Preserve interrupted or unknown outcomes; do not infer success or retry uncertain mutations blindly.

Obtain independent outcome review and actual user acceptance. Keep implementation approval, acceptance, publication, deployment, migration, and restore authorization distinct. Reconcile accepted specifications and retain provenance/history. Delivered changes and applied deltas must not be silently rewritten. Record lessons and propose reusable convention improvements separately, grouped into one reviewed source release rather than one release per lesson.

## Conversations and prompts

Role instructions and supplied context do not constitute a request to revise a document. Do not start a model call just because a conversation opened unless the user explicitly selected an initial action. Discuss questions without replacing artifacts. Requested revisions belong to completed qualifying turns, not to exit. Ending a session must not ask a model to invent a final revision.
