# Sprint Governance

This directory contains operational execution state. Normative rules live under `governance/`; sprint artifacts MUST implement and MUST NOT weaken them.

## Required Sprint Information

Each sprint MUST define objective, scope, non-goals, deliverables, risks, backlog, task mandatory flags, acceptance criteria, definition of done, integration branch, execution history, and retrospective.

Each task MUST declare an autonomy level or inherit LOW. Autonomy is task-scoped, cannot be self-escalated, and never overrides task restrictions or Human Architect gates.

The board is a current index; task files and approval records provide detailed evidence. Board and task status MUST agree. Backlog, board, and acceptance criteria MUST identify the same mandatory work.

## Activation and Closure

Task execution requires an ACTIVE sprint unless the Human Architect records a narrow pre-activation exception. No sprint is CLOSED until every mandatory acceptance criterion is met or explicitly excepted with recorded risk acceptance, and the Human Architect records closure.

## Evidence

Evidence MUST be proportional. `N/A` is permitted with a reason when an artifact or check is unnecessary or unauthorized; it cannot replace mandatory evidence. Documentation-only changes MAY record product tests as `N/A` when no executable behavior changed.
