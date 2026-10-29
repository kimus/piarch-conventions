# Progress reporting

When executing multi-step work - task sequences, refactors, gate loops, test campaigns - the agent MUST emit a fixed-column execution tree at each state transition, so the owner can read the whole plan's health in one glance. The tree is agent output, not bound content: it is never written into a specification.

## 1. Column alignment

Every primary task row places its trailing tag at a fixed column, so tags align vertically:

1. **Prefix block (exactly 12 characters)**: `<branch> <glyph> <task_id>  ` - branch connector, one space, state glyph, one space, task id, two spaces. Example: `├── ✔ G0.1  `.
2. **Description block (exactly 44 characters)**: truncate longer descriptions to 43 characters plus `…`; pad shorter ones with trailing spaces.
3. **Trailing tag (exactly 17 characters)**: after the description plus two separating spaces, the tag `[<7-char scope-or-time> | <5-char tokens>]` opens on **column 59** of every primary line.

## 2. State glyphs and tags

- **Queued (`·`) and active (`↻`)** tasks show a complexity scope and an empty token dash: `[  small |     -]`, `[ medium |     -]`, `[   high |     -]`.
- **Completed (`✔`)** tasks replace the scope with zero-padded elapsed time `[MMm SSs]` and the dash with the measured cost (`  450`, ` 1.2k`, `45.2k`). Never mark a task `✔` until its changes are written and verified by a syntax or test check. Where a cost genuinely cannot be measured, print `-`; an invented number is a false record.
- **Unresolved errors and blockers** render as a sub-line indented five spaces after the branch line: `│     ✖: <description>`, in soft red for the whole sub-line.
- **Resolved errors** keep their sub-line - the history is not deleted - and flip the prefix to `│     ✔: <resolution>` in muted green.

## 3. State persistence

When execution spans multiple turns, environment reloads, or carries failure history, the agent persists the tree state in a local `tasks.jsonl` (one line per state transition: Queued → Active → Complete, plus issue-open and issue-resolved events, with cumulative time and token totals) and re-reads it at the start of each turn, so the tree's ids, wording, and error history do not drift between reports. The file is working data: disposable, unbound, never an agreement.

## 4. Scope rubric (for pre-completion tags)

- `[  small]` - single-file edits under 15 lines, typos, config tweaks, lint runs, simple checks.
- `[ medium]` - localized bug fixes across one to three files, unit-test updates, bounded refactors, author refine loops.
- `[   high]` - architectural changes, full test suites, multi-file re-cuts, external model review calls.

## 5. Colors (ANSI)

| Element | Escape | Style |
| :--- | :--- | :--- |
| Phase header | `\033[38;5;75m` | soft cyan |
| Tree connectors (`├──`, `└──`, `│`) | `\033[90m` | dim gray |
| Completed glyph `✔` | `\033[38;5;71m` | muted sage |
| Active glyph `↻` | `\033[33m` | warm amber |
| Queued glyph `·` | `\033[90m` | dim gray |
| Completed tag | `\033[90m` | dim gray |
| Active scope | `\033[33m` | warm amber |
| Queued scope | `\033[38;5;208m` | muted orange |
| Resolved sub-line `✔:` | `\033[38;5;71m` | muted sage, whole line |
| Unresolved sub-line `✖:` | `\033[38;5;203m` | soft red, whole line |

## 6. Output template

```text
\033[38;5;75mPhase <ID>: <Phase Name>\033[0m \033[90m(<k>/<total> complete)\033[0m
\033[90m├──\033[0m \033[38;5;71m✔\033[0m \033[1m<ID>.1\033[0m  <44-char description>  \033[90m[00m 04s |  1.2k]\033[0m
\033[90m├──\033[0m \033[33m↻\033[0m \033[1m<ID>.2\033[0m  <44-char description>  \033[33m[ medium\033[90m |     -\033[33m]\033[0m
\033[90m│     \033[38;5;71m✔: <resolved description>\033[0m
\033[90m│     \033[38;5;203m✖: <active error description>\033[0m
\033[90m└──\033[0m \033[90m· <ID>.3  <44-char description>  \033[38;5;208m[   high\033[90m |     -\033[38;5;208m]\033[0m

\033[90m--------------------------------------------------------------------------------\033[0m
\033[1mTasks:\033[0m \033[38;5;71m<p> passed\033[0m | \033[33m<a> active\033[0m | \033[90m<q> queued\033[0m | \033[90mElapsed: <total> | Total Tk: <total>\033[0m
```
