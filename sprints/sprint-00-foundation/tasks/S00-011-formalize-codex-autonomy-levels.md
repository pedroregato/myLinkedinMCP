# S00-011 — Formalize Codex Autonomy Levels

Status: DONE
Owner: Codex
Reviewer: Human Architect
Priority: Critical
Mandatory: Yes
Autonomy-Level: STANDARD

## Objective

Define explicit, task-scoped LOW, STANDARD, and ELEVATED Codex autonomy levels while preserving default-deny behavior and every Human Architect approval gate.

## Context

Governance 0.2 remediation is awaiting Human Architect approval. The Human Architect has authorized explicit Codex autonomy levels and assigned this task STANDARD autonomy. The repository is public and has a Git remote named `origin`.

## Scope

- autonomy rules in `governance/`;
- repository-level autonomy guidance in `AGENTS.md`;
- autonomy fields and guidance in `sprints/task-template.md`;
- Sprint 00 board, backlog, execution log, and this task record;
- read-only Git and consistency inspection;
- public-repository safety checks that do not reveal sensitive values;
- a proposed commit message without creating a commit.

## Non-Goals

- product implementation changes;
- dependency installation;
- commit, push, pull-request creation/update, merge, force-push, or branch deletion;
- CI/CD changes or migrations;
- credential, secret, environment, PII, or local-configuration modification or disclosure;
- autonomous escalation, self-approval, DONE transition, governance activation, or sprint closure.

## Risks

- broad autonomy language could accidentally override task restrictions or Human Architect authority;
- overlapping authority documents could drift or conflict;
- public-repository content could expose secrets, PII, sensitive local paths, or private artifacts;
- ELEVATED could be misread as blanket or permanent authorization;
- governance 0.2 remains Proposed until Human Architect approval.

## Acceptance Criteria

- [x] LOW, STANDARD, and ELEVATED are defined with explicit permissions and restrictions.
- [x] Autonomy is granted per task, defaults to LOW when absent, and cannot be self-escalated.
- [x] Task-specific restrictions override autonomy permissions.
- [x] Escalation, downgrade, ambiguity, additional-authority requests, and execution-log recording rules are defined.
- [x] Human Architect approval gates remain intact.
- [x] Public-repository security constraints are represented.
- [x] The task template contains the required Autonomy section and operation subsections.
- [x] Board, backlog, task, and execution log are synchronized.
- [x] Cross-document consistency and public-safety checks are completed without exposing sensitive values.
- [x] A Markdown execution report and proposed commit message are recorded.
- [x] S00-011 is moved to REVIEW, not DONE.

Human Acceptance:
Approved by: Human Architect
Date: 2026-08-08
Decision: ACCEPTED

## Evidence Required

- changed-file list and rationale;
- autonomy model and S00-008/S00-009 governance compatibility review;
- consistency-check results;
- `.gitignore` inspection and scoped sensitive-content check results without secret values;
- exact Git diff/status summary and remote-name verification without remote URLs;
- tests/checks or justified `N/A`;
- remaining risks and unresolved Human Architect decisions;
- proposed commit message;
- commit, push, PR, merge, and deployment references, or justified `N/A`.

## Autonomy

Level: STANDARD

### Authorized Operations

- read and edit/create files explicitly listed in Scope;
- run local non-destructive and read-only Git commands;
- run consistency and public-repository safety checks;
- update task, board, backlog, and execution logs;
- stage scoped files if useful for inspection;
- prepare a proposed commit message.

### Operations Requiring Human Approval

- dependency changes;
- commit creation, push, PR creation/update, CI/CD changes, migrations, secrets/credentials, external side effects, merge, DONE, governance activation, and sprint closure.

### Prohibited Operations

- force-push or branch deletion;
- product implementation edits;
- secret, credential, environment-value, PII, or sensitive local-configuration exposure/modification;
- self-escalation or self-approval;
- production-destructive actions.

## Execution Log

2026-08-08 — Task created in READY with Human Architect-assigned STANDARD autonomy.

2026-08-08 — Task moved READY -> IN_PROGRESS; autonomy governance work started.

2026-08-08 — Autonomy model, governance reconciliation, public-repository safety inspection, and consistency review completed; task moved IN_PROGRESS -> REVIEW.

2026-08-08 — Human Architect reviewed and accepted S00-011.
Decision: APPROVED.
Task moved REVIEW -> DONE.
Governance autonomy model accepted.

## Execution Report

### Files Changed and Rationale

- `AGENTS.md` — added per-task autonomy, LOW fallback, no-self-escalation, public-repository safety, and canonical Git-policy references.
- `governance/README.md` — advanced the candidate governance set to 0.3, added the autonomy policy, and established one canonical Git/GitHub policy.
- `governance/CODEX_AUTONOMY_LEVEL_POLICY.md` — created the LOW/STANDARD/ELEVATED model, escalation/downgrade rules, ambiguity handling, authority-request evidence, and public-repository gate.
- `governance/AGENT_AUTHORITY_POLICY.md` — integrated autonomy with default-deny and operation-level authority without weakening Human Architect gates.
- `governance/ENGINEERING_MANIFESTO.md` — added task-scoped autonomy and no-self-escalation as a durable principle.
- `governance/SPRINT_LIFECYCLE_POLICY.md` — required autonomy/default identification at READY and execution-log evidence for autonomy changes.
- `governance/GIT_GITHUB_VERSIONING_POLICY.md` — reconciled its staged proposal with governance 0.3 and linked it to the autonomy policy.
- `governance/GIT_CHANGE_MANAGEMENT_POLICY.md` — converted the older competing policy into a non-normative compatibility pointer.
- `sprints/README.md` — added the task-level autonomy/default rule.
- `sprints/task-template.md` — added `Autonomy-Level` and the required Autonomy headings, precedence, and change-recording guidance.
- `sprints/board.md` — registered and synchronized S00-011 through READY, IN_PROGRESS, and REVIEW.
- `sprints/sprint-00-foundation/README.md` — recorded S00-011 as a narrow Human-Architect-authorized pre-activation task while the sprint remains PLANNED.
- `sprints/sprint-00-foundation/acceptance-criteria.md` — added mandatory S00-011 governance approval and activation evidence.
- `sprints/sprint-00-foundation/backlog.md` — added S00-011 with mandatory and STANDARD designations.
- `sprints/sprint-00-foundation/execution-log.md` — recorded authorization, autonomy, lifecycle, and review completion.
- `sprints/sprint-00-foundation/tasks/S00-011-formalize-codex-autonomy-levels.md` — created the task and its evidence/report.

### Autonomy Model Implemented

- `LOW` is the fallback and the normal default for governance, security, unfamiliar, high-risk, and undeclared tasks. It permits reading, analysis, read-only commands, proposals/diffs, and authorized status/log updates; broader writes, creation, staging, commits, dependencies, and external operations require Human Architect approval.
- `STANDARD` must be declared and permits scoped file work, non-destructive local commands, checks, operational record updates, safety-gated staging, and commit preparation. Commit creation requires an explicit task grant. Dependencies, push, PRs, CI/CD, migrations, secrets, external effects, merge, DONE, activation, and closure retain Human Architect gates.
- `ELEVATED` must be granted for one named task and enumerate each extra target and operation. It may cover dependencies, branch creation, branch push, PR operations, sandbox migrations, or reversible external actions. It never grants self-approval, DONE, sprint closure, merge to `main`, protected-branch force-push, credential modification without dedicated authorization, or production-destructive action without a separate gate.
- Autonomy is never permanent. Task restrictions and stricter governance always override it. Codex cannot self-escalate but may defensively downgrade. Every grant, request, downgrade, revocation, or restoration must be logged.

### Inconsistencies Found

- A pre-existing staged `GIT_GITHUB_VERSIONING_POLICY.md` declared governance set 0.2 and intended to supersede `GIT_CHANGE_MANAGEMENT_POLICY.md`, leaving two competing Git authorities. Resolved by adopting the comprehensive policy as the canonical 0.3 candidate and retaining the old path only as a compatibility pointer.
- Existing S00-008 and S00-009 task records predate the autonomy field. This is not a permission gap because LOW applies when absent; historical records were not rewritten beyond already-authorized schema reconciliation.
- The pre-existing staged Git policy contains Markdown hard-break trailing spaces. `git diff --check` reports these in staged content. They do not alter policy meaning, and the user-owned index was not silently restaged.

### Security and Public-Repository Checks

- `.gitignore` inspected before recommending a commit.
- Existing ignore coverage detected for `.env`, IDE/local metadata, and Python cache artifacts.
- Generic `*.pem`, `*.key`, `*.p12`, and `*.pfx` ignore coverage was not detected. `.gitignore` is outside S00-011's authorized edit scope, so no change was made.
- Git remote names were inspected without URLs; `origin` exists.
- All governance files and S00-011-related sprint/agent files were scanned for known token/key formats, assigned credential-like values, email/PII indicators, and sensitive local user paths.
- Suspected sensitive-content findings: none.
- No secret values, environment values, remote URLs, PII, or credentials were printed or recorded.
- No files were staged by S00-011; the pre-existing staged state was preserved.

### Consistency Review

- Board, backlog, and acceptance criteria contain matching S00-001 through S00-011 identifiers.
- Governance policy metadata now consistently identifies governance set 0.3 Proposed.
- The template contains the exact required Autonomy headings.
- LOW fallback, task precedence, no-self-escalation, public visibility, escalation, downgrade, and logging rules are represented across the canonical documents.
- S00-011 task and board status were synchronized before the final REVIEW transition.
- No merge-conflict markers were found.
- Product tests/linters/evals: `N/A — documentation-only governance task; no executable behavior changed.`
- Commit, push, PR, merge, and deployment: `N/A — not authorized.`

### Exact Git Diff Summary

At the consistency checkpoint, `git diff --stat -- AGENTS.md governance sprints` returned:

```text
governance/GIT_GITHUB_VERSIONING_POLICY.md    |   5 +-
.../S00-008-approve-development-governance.md | 159 +++++++++++++++++++++
2 files changed, 162 insertions(+), 2 deletions(-)
```

`git diff --cached --stat -- AGENTS.md governance sprints` returned:

```text
governance/GIT_GITHUB_VERSIONING_POLICY.md    | 956 +++++++++++++++++++++
.../S00-008-approve-development-governance.md |   0
2 files changed, 956 insertions(+)
```

Most authorized governance and sprint artifacts were already untracked, so standard Git diff cannot calculate a baseline-relative stat for them. Scoped status showed the Git/GitHub policy and S00-008 as `AM`, with the other relevant governance/sprint files untracked. This pre-existing repository state limits exact task-to-diff attribution until a governed baseline is established.

### Remaining Risks

- Governance 0.3 remains Proposed until the Human Architect approves it and records an effective date.
- Generic private-key/certificate ignore patterns are missing and require a separately authorized `.gitignore` change.
- GitHub branch protections, required reviews/checks, and secret scanning remain unverified.
- The mixed staged/untracked baseline prevents reliable commit attribution and should be normalized under Human Architect direction.
- Pattern-based sensitive-content scanning reduces risk but cannot prove absence of sensitive information.

### Unresolved Human Architect Decisions

- Approve, request changes to, or reject governance set 0.3; if approved, record approver and effective date.
- Decide whether to authorize a separate `.gitignore` hardening task for private-key/certificate patterns.
- Decide how to normalize the pre-existing staged and untracked Git baseline before the first governed commit.
- Confirm whether and how GitHub protections and secret scanning will be technically enabled.
- Decide whether older task records should be mechanically backfilled with explicit autonomy fields or continue to inherit LOW.

### Proposed Commit Message

```text
docs: formalize Codex autonomy levels [S00-011]
```

Commit creation remains unauthorized and was not performed.

### Final Recommendation

`READY FOR HUMAN REVIEW` — the autonomy model is internally consistent and preserves Human Architect authority. Approval and activation of governance set 0.3, Git baseline normalization, and any `.gitignore` hardening remain Human Architect decisions.

## Completion Rule

Codex may move this task from READY to IN_PROGRESS and then to REVIEW.

Only the Human Architect may accept it and move it to DONE.
