# TASK-ID — Task Title

Status: BACKLOG
Owner: Unassigned
Reviewer: Human Architect
Priority: Medium
Mandatory: Yes / No
Autonomy-Level: LOW | STANDARD | ELEVATED

## Objective

Describe the intended outcome.

## Context

Describe why this task exists and reference its requirement or sprint acceptance criterion.

## Inputs

- `AGENTS.md`
- relevant specifications;
- relevant governance policies.

## Scope

Define authorized files and operations.

## Non-Goals

Define prohibited and excluded work.

## Acceptance Criteria

- [ ] Criterion 1
- [ ] Criterion 2
- [ ] Criterion 3

## Risks and Dependencies

Describe risks, dependencies, external effects, and any required Human Architect decisions.

## Authority and Exceptions

Record any operation-specific authorization or pre-activation exception. If none: `N/A — no exceptional authority granted.`

## Autonomy

Level: LOW | STANDARD | ELEVATED

### Authorized Operations

List operations authorized by task scope and the assigned autonomy level.

### Operations Requiring Human Approval

List operations that require an additional Human Architect grant before execution.

### Prohibited Operations

List operations forbidden for this task even if a broader autonomy level would otherwise permit them.

If the level is omitted or ambiguous, LOW applies. Task restrictions override level permissions. Codex MUST NOT self-escalate. Record every escalation request, grant, one-time authority, downgrade, revocation, or restoration in the Execution Log with actor, date, scope, constraints, and expiry or resume condition.

## Traceability and Evidence

- Requirement/acceptance criterion:
- Authorized scope:
- Branch:
- Files changed:
- Diff summary:
- Checks executed and results:
- Commit hash(es):
- Pull request and reviewed head:
- Human acceptance decision/date:
- Merge reference:
- Sprint closure reference:

Use `N/A — <reason>` only when the evidence item is unnecessary or unauthorized.

## Execution Log

Not started.

## Completion Rule

Codex may move an authorized task from READY to IN_PROGRESS and then to REVIEW.

Only the Human Architect may accept it and move it to DONE.
