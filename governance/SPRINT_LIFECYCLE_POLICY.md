# Sprint Lifecycle Policy

> Document version: 0.2  
> Governance set: 0.3 Proposed  
> Authority: Human Architect  
> Effective date: Pending approval

## Sprint States

Normal flow: `PLANNED -> ACTIVE -> REVIEW -> CLOSED`

Exceptional states: `ON_HOLD`, `CANCELLED`

| Transition | Authority | Preconditions and evidence |
|---|---|---|
| Create -> PLANNED | Human Architect | Objective, owner, and initial record exist |
| PLANNED -> ACTIVE | Human Architect | Objective, scope, non-goals, deliverables, risks, backlog, mandatory flags, acceptance criteria, and definition of done are defined |
| ACTIVE -> REVIEW | Human Architect | Every mandatory task is DONE or has an explicitly accepted exception; acceptance evidence is assembled |
| REVIEW -> ACTIVE | Human Architect | Changes required are recorded |
| REVIEW -> CLOSED | Human Architect only | Acceptance criteria verified; closure decision and references recorded |
| PLANNED/ACTIVE/REVIEW -> ON_HOLD | Human Architect | Reason, impact, and resume condition recorded |
| ON_HOLD -> prior state | Human Architect | Resume decision and changed assumptions recorded |
| Any non-CLOSED state -> CANCELLED | Human Architect | Reason and disposition of work recorded |
| CLOSED/CANCELLED -> any state | Prohibited by default | New explicit Human Architect exception and audit record required |

An AI agent MUST NOT activate, close, cancel, hold, resume, or reopen a sprint.

## Sprint Activation Rule

Work on sprint tasks MUST NOT begin until the sprint is ACTIVE. A Human Architect MAY authorize a narrowly scoped pre-activation task needed to make activation possible. The exception MUST be recorded in the task and sprint execution log and does not activate the sprint or authorize other tasks.

## Mandatory and Optional Tasks

Every sprint task MUST declare `Mandatory: Yes` or `Mandatory: No`.

- A mandatory task is required for sprint acceptance unless the Human Architect records a specific exception and risk acceptance.
- An optional task may be deferred or cancelled without blocking sprint REVIEW, but its disposition MUST be recorded.
- The backlog, board, and acceptance criteria MUST identify the same mandatory work. Any mismatch blocks sprint transition until reconciled.

## Task States

Normal flow: `BACKLOG -> READY -> IN_PROGRESS -> REVIEW -> DONE`

Exceptional states: `BLOCKED`, `CHANGES_REQUESTED`, `CANCELLED`

| Transition | Authority | Preconditions and evidence |
|---|---|---|
| Create -> BACKLOG | Human Architect or authorized planner | Objective and owner/status fields recorded |
| BACKLOG -> READY | Human Architect | Scope, acceptance criteria, autonomy level (or LOW default), authority, dependencies, and reviewer defined; sprint ACTIVE or pre-activation exception recorded |
| READY -> IN_PROGRESS | Assigned Codex or Human Architect | Task explicitly authorized; execution start logged |
| IN_PROGRESS -> REVIEW | Assigned Codex or Human Architect | Scoped work complete; evidence and known risks recorded |
| REVIEW -> DONE | Human Architect only | Acceptance decision, approver, date, and evidence recorded |
| REVIEW -> CHANGES_REQUESTED | Human Architect | Requested changes recorded |
| CHANGES_REQUESTED -> IN_PROGRESS | Assigned Codex or Human Architect | Rework explicitly authorized and started |
| READY/IN_PROGRESS/CHANGES_REQUESTED -> BLOCKED | Assigned Codex or Human Architect | Blocker, impact, and needed decision recorded |
| BLOCKED -> prior executable state | Human Architect, or Codex when the recorded objective condition is demonstrably cleared | Resolution evidence recorded |
| Any non-DONE state -> CANCELLED | Human Architect | Reason and work disposition recorded |
| DONE/CANCELLED -> any state | Human Architect only | Reopening reason and audit record required |

Codex MUST NOT move a task to DONE or approve its own evidence. Board and task-file status MUST be updated together; disagreement is a blocking inconsistency.

Any autonomy assignment, escalation, one-time grant, downgrade, revocation, or restoration MUST be recorded in the task Execution Log. Autonomy changes do not themselves change task or sprint state.

## Proportional Evidence

Evidence MUST match risk and change type. Documentation-only tasks do not require product tests when no executable behavior changed; the test field MAY be `N/A` with a reason. A field such as commit, PR, deployment, or external effect MAY be `N/A` only when it was unnecessary or unauthorized, with a concise justification. `N/A` MUST NOT be used to bypass a required control. Higher-risk, security-sensitive, destructive, or externally visible changes require stronger verification and explicit approval.
