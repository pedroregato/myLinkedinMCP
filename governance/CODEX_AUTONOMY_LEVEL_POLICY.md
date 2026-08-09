# Codex Autonomy Level Policy

> Document version: 0.1  
> Governance set: 0.3  
> Authority: Human Architect  
> Effective date: 2026-08-08  
> Status: Active

## Purpose and Core Rule

Autonomy defines which operations Codex may perform without an additional approval while executing one explicitly authorized task. Autonomy is granted per task, never permanently to the agent. It does not select work, expand scope, accept risk, or replace task authorization.

If a task does not declare an autonomy level, `LOW` applies. Task-specific scope, restrictions, non-goals, and operation-level limits override every autonomy permission. A more restrictive applicable rule always controls. Silence or ambiguity grants no authority.

## Required Task Record

Every newly created task MUST contain:

```markdown
## Autonomy

Level: LOW | STANDARD | ELEVATED

### Authorized Operations

### Operations Requiring Human Approval

### Prohibited Operations
```

The selected level and any task-specific grants MUST be explicit. Listing a level alone does not authorize work outside task scope.

## LOW

LOW is the default for governance tasks, security tasks, unfamiliar or high-risk work, and any task without an explicitly declared autonomy level.

LOW permits, within an authorized task:

- repository reading and analysis;
- read-only local commands;
- proposals and diffs;
- authorized task, board, and execution-log status updates.

LOW requires Human Architect approval before:

- general file edits or file creation beyond the expressly authorized status/log updates;
- dependency changes;
- Git staging or commit creation;
- external operations or side effects.

## STANDARD

STANDARD is intended for normal implementation work after applicable governance is approved. It MUST be explicitly declared by the task; governance and security tasks remain LOW unless the Human Architect explicitly assigns another level.

STANDARD permits, within explicit task scope:

- reading files and editing or creating authorized files;
- local non-destructive commands;
- tests, linters, and evaluations;
- task, board, and execution-log updates;
- `git add` of authorized task files after required public-repository safety checks;
- preparation of a small task-scoped commit;
- creation of a small task-scoped commit only when the task explicitly grants commit creation.

STANDARD requires additional Human Architect approval for:

- new or changed dependencies;
- push or pull-request creation/update;
- CI/CD changes;
- data or schema migrations;
- credential or secret access/modification;
- external side effects;
- merge, REVIEW -> DONE, governance activation, and sprint closure.

## ELEVATED

ELEVATED MUST be explicitly granted by the Human Architect for one named task. Its task record MUST enumerate each additional authorized operation, target, environment, constraints, and expiry or completion boundary. Unlisted operations remain unauthorized.

ELEVATED may authorize, when specifically listed:

- approved dependency installation;
- branch creation;
- push of a named task or sprint branch to a named remote;
- pull-request creation or update;
- development or sandbox migrations;
- reversible external operations with defined targets and recovery controls.

ELEVATED never implies permission to:

- approve Codex's own work or evidence;
- move Codex's own task to DONE;
- close a sprint;
- merge to `main` unless a future approved governance amendment explicitly permits it;
- force-push a protected branch;
- expose or modify credentials without explicit dedicated authorization;
- perform a production-destructive action without a separate, operation-specific Human Architect gate.

## Escalation and Additional Authority

Codex MUST NOT self-escalate. To request additional authority, Codex MUST stop the affected operation and provide the Human Architect with:

- the current level and exact additional operation requested;
- target files, branch, remote, environment, or external system;
- reason and expected outcome;
- material risks and side effects;
- validation and recovery plan;
- requested duration or completion boundary.

Only the Human Architect MAY grant escalation. The grant MUST be recorded in the task's Autonomy section or Execution Log before the operation begins, including approver, date, old and new level or one-time grant, scope, constraints, and expiry. A one-operation grant does not necessarily change the task's level.

## Downgrade and Revocation

The Human Architect MAY downgrade or revoke autonomy at any time. Codex MUST also operate at a lower effective level when risk, unfamiliarity, conflicting instructions, suspected sensitive content, unsafe repository state, or failed controls make the declared level inappropriate. A self-imposed downgrade is protective and does not require approval.

Downgrades and revocations MUST be recorded with the reason, time/date, affected operations, and resume condition. Work MAY continue only within the lower effective authority. Restoration or escalation requires Human Architect approval.

## Ambiguity and Conflicts

When authority, scope, or the applicable level is missing, ambiguous, or conflicting, LOW applies to unaffected analysis and read-only work, and the affected write or external operation MUST stop. Codex MUST record the ambiguity and request Human Architect resolution. Task-specific prohibitions, governance restrictions, and platform/security controls override autonomy permissions.

## Public Repository Safety Gate

All content proposed for staging, commit, push, or PR in a public repository MUST be treated as publicly visible. Before staging or recommending a commit, Codex MUST:

1. inspect `.gitignore` and relevant ignore rules;
2. inspect the scoped change set for suspected secrets, credentials, tokens, API keys, `.env` contents, PII, sensitive local paths, and generated private artifacts;
3. avoid printing or reproducing any suspected sensitive value;
4. report only the suspected type and location;
5. stop staging and request Human Architect review if suspected sensitive content is detected.

A clean scan reduces risk but is not proof that content is safe. Staging authorization never overrides this gate.
