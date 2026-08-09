# Governance

This directory contains the canonical governance rules for myLinkedinMCP. It defines how humans and AI agents collaborate, how work moves through tasks and sprints, and how repository changes are controlled.

## Governance Record

- Governance set version: 0.3
- Status: Active
- Approving authority: Human Architect
- Approval record: Approved by the Human Architect on 2026-08-08 under S00-013
- Effective date: 2026-08-08
- Supersedes: Version 0.1 draft and version 0.2 proposal

Governance set 0.3 is ACTIVE by explicit Human Architect decision recorded under S00-013. Activation grants no authority beyond the task-scoped permissions defined by this governance set.

## Approval Record

- Version: 0.3
- Decision: Approved and authorized to become ACTIVE
- Human Architect: Human Architect
- Decision date: 2026-08-08
- Effective date: 2026-08-08
- Exceptions: None recorded
- Task/PR reference: S00-013; PR pending creation

## Normative Documents

- `ENGINEERING_MANIFESTO.md`
- `SPRINT_LIFECYCLE_POLICY.md`
- `AGENT_AUTHORITY_POLICY.md`
- `CODEX_AUTONOMY_LEVEL_POLICY.md`
- `GIT_GITHUB_VERSIONING_POLICY.md`

`GIT_CHANGE_MANAGEMENT_POLICY.md` is a compatibility pointer and is not a second normative Git policy.

Normative terms `MUST`, `MUST NOT`, `REQUIRED`, `SHOULD`, and `MAY` are to be interpreted as requirement, prohibition, obligation, recommendation, and permission respectively. A `MAY` never overrides an explicit restriction or required human approval.

## Precedence and Conflict Resolution

Within repository-controlled instructions, precedence is:

1. an explicit, current Human Architect instruction recorded in the repository or task;
2. approved governance policies in this directory;
3. approved product and architecture specifications;
4. the active sprint definition and acceptance criteria;
5. the authorized task file;
6. operational artifacts such as the board, backlog, templates, and execution logs.

Higher-level platform, legal, security, and system constraints always apply and cannot be overridden by repository instructions. A lower-precedence artifact MUST NOT weaken a higher-precedence control. If two instructions at the same level conflict, or an instruction is unsafe or materially ambiguous, work MUST stop at the smallest affected scope, the conflict MUST be recorded, and the Human Architect MUST resolve it. Silence does not grant authority.

## Activation, Amendment, and Supersession

- Only the Human Architect MAY approve or activate governance.
- Approval MUST record the version, approver, decision date, effective date, and any accepted exceptions.
- Governance changes MUST be performed through an authorized task with a reviewable diff and human acceptance.
- An AI agent MAY propose or implement an explicitly authorized amendment but MUST NOT approve, activate, weaken, or supersede governance.
- Each amendment MUST increment the governance-set version and affected-document versions.
- A superseding version MUST identify what it replaces. Historical approval evidence MUST remain in Git history and sprint/task records.
- Emergency exceptions MUST be explicit, time-bounded, scoped, recorded by the Human Architect, and MUST NOT silently amend the policy.

Autonomy levels are governed by `CODEX_AUTONOMY_LEVEL_POLICY.md`. Autonomy is assigned per task and never changes this precedence hierarchy or the Human Architect's final authority.

## Approval Record Template

- Version:
- Decision: Approved / Changes Requested / Rejected
- Human Architect:
- Decision date:
- Effective date:
- Exceptions:
- Task/PR reference:
