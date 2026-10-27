# Environment and design conventions

Before approving the baseline, document the environment needed to achieve and verify it. Unknown decisions that affect behavior or feasibility are blockers. Deferrable choices can remain open with an owner and a point by which they must be resolved.

## Required project definitions

- Existing stack and architecture, or proposed choices with rationale.
- Supported runtime and tool versions, package manager, and lockfiles.
- Setup, run, build, lint, type check, and test commands where applicable.
- Local dependencies, services, fixtures, test accounts, and safe data boundaries.
- Required environment variable names and a safe way to obtain values.
- Available verification tools and checks that require human inspection.
- Agent skills: purpose, trigger, source/version, and allowed side effects.
- UI/UX constraints and the design system when a user interface is in scope.
- Security controls, sensitive data boundaries, and incident ownership in `docs/security.md`.
- Deployment targets, migration tools, backup/restore policy, and operational authorization in `docs/operations.md`.
- Release version sources, public compatibility contract, and SemVer policy.

Record actual verification of environment commands. Mark untested commands explicitly. Do not select a stack, dependency, design library, or accessibility target merely because the template contains a field.

For UI work, identify the intended users and critical journeys. Define layout and responsive behavior, components and tokens, keyboard and focus behavior, and loading, empty, success, and error states. Use approved references for visual judgment. Record the accessibility standard and scope selected by the user or applicable project requirements.

## Improve with evidence

At each checkpoint, ask whether failures came from the spec, implementation, verifier, or environment. Propose a targeted change with its reason and a way to check it. Keep project lessons local. Promote reusable lessons to the shared conventions only after review.

Do not modify global conventions, reusable skills, acceptance criteria, or tool permissions as an unannounced implementation fix. Project documentation can record observed facts; changes to the approved operating contract need review.
