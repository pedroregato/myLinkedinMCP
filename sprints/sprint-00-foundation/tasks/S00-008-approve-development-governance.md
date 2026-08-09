# S00-008 — Approve Development Governance

Status: DONE
Owner: Codex
Reviewer: Human Architect
Priority: Critical
Mandatory: Yes

## Objective

Review and validate the development governance framework of myLinkedinMCP before it becomes normative.

## Inputs

- governance/README.md
- governance/ENGINEERING_MANIFESTO.md
- governance/SPRINT_LIFECYCLE_POLICY.md
- governance/AGENT_AUTHORITY_POLICY.md
- governance/GIT_CHANGE_MANAGEMENT_POLICY.md
- sprints/README.md
- sprints/board.md
- sprints/task-template.md
- sprints/sprint-00-foundation/README.md
- sprints/sprint-00-foundation/acceptance-criteria.md

## Scope

Review the governance framework for:

- internal consistency;
- authority separation;
- task lifecycle correctness;
- sprint lifecycle correctness;
- Codex permissions and restrictions;
- Git/GitHub governance;
- traceability;
- human approval gates;
- ambiguity that could allow unsafe or unauthorized actions.

## Non-Goals

- do not implement MCP functionality;
- do not install dependencies;
- do not change application architecture;
- do not modify unrelated files;
- do not approve governance autonomously;
- do not move this task to DONE.

## Required Review Questions

1. Are Human Architect and Codex authorities clearly separated?
2. Can Codex accidentally approve its own work?
3. Are task state transitions unambiguous?
4. Are sprint state transitions unambiguous?
5. Is the relation between task, commit, PR, and sprint closure traceable?
6. Are destructive or external actions sufficiently restricted?
7. Are governance documents consistent with each other?
8. Are there missing rules that could create governance drift?
9. Are there conflicting rules?
10. Is anything unnecessarily bureaucratic for the current maturity level?

## Expected Output

Codex must produce:

- findings;
- inconsistencies;
- governance gaps;
- proposed improvements;
- risks;
- a final recommendation:
  - READY FOR HUMAN APPROVAL
  - CHANGES REQUIRED

## Evidence Required

- files reviewed;
- exact issues found;
- proposed changes, if any;
- git diff only if explicitly authorized to modify files.

## Execution Log

2026-08-08 — Builder/Reviewer Agent governance review completed.

### Files Reviewed

- `AGENTS.md`
- `governance/AGENT_AUTHORITY_POLICY.md`
- `governance/ENGINEERING_MANIFESTO.md`
- `governance/GIT_CHANGE_MANAGEMENT_POLICY.md`
- `governance/README.md`
- `governance/SPRINT_LIFECYCLE_POLICY.md`
- `sprints/README.md`
- `sprints/board.md`
- `sprints/task-template.md`
- `sprints/sprint-00-foundation/README.md`
- `sprints/sprint-00-foundation/acceptance-criteria.md`
- `sprints/sprint-00-foundation/tasks/S00-008-approve-development-governance.md`

### Strengths

- Final authority for scope, architecture, governance, acceptance, merge, task completion, and sprint closure is consistently assigned to the Human Architect.
- Codex is expressly prohibited from approving its own work, moving tasks to DONE, closing sprints, merging to `main`, weakening governance, installing dependencies without authorization, and introducing unauthorized external writes.
- The normal task and sprint lifecycles are concise and understandable.
- Small, focused, task-identified commits and retained execution evidence establish a useful traceability foundation.
- Sprint scope, non-goals, acceptance criteria, and explicit human closure form appropriate approval gates.

### Problems or Ambiguities

1. `governance/README.md` calls the governance documents canonical and normative while every policy is marked `Draft`, and this task says the framework is being reviewed before it becomes normative. The effective status and activation event are unclear.
2. Sprint 00 is `PLANNED`, but S00-008 was `READY` and authorized for execution. The policies do not say whether tasks may enter READY or be executed before the sprint is ACTIVE, allowing the sprint lifecycle to be bypassed.
3. Task exceptional-state transitions are incomplete. Entry to and exit from BLOCKED and CHANGES_REQUESTED are unspecified, as are the actors authorized to perform those transitions. Cancellation and reopening are also undefined.
4. Sprint transitions involving ON_HOLD and CANCELLED are unspecified, including who may invoke them and whether/how a sprint resumes.
5. The ACTIVE -> REVIEW sprint gate uses “all mandatory tasks are ready for human validation,” while the Sprint 00 exit gate says tasks must be “completed and reviewed.” These phrases can mean REVIEW, DONE, or something else and should be normalized.
6. “Mandatory task” is not formally identified in the board or task schema. Sprint 00 also requires initial BDD scenarios, but no corresponding task appears on the current board.
7. Git controls are advisory: `main` is only “protected conceptually,” sprint branches “should” be used, and the integration flow is “preferred.” Required branch protection, pull-request review, status checks, merge authority, and exceptions are not defined.
8. Traceability stops short of the stated review flow. The policy chain omits the PR and sprint closure, the task template has no standard fields for branch/commit/PR/acceptance references, and no rule requires a one-to-one mapping between recorded evidence and the reviewed diff.
9. “Prepare commits when explicitly authorized” is ambiguous: it could mean stage changes, draft a commit message, or create a commit. Commit and push permissions should be stated separately.
10. Destructive local actions are not explicitly governed. External writes require authorization, but deletion, history rewriting, force-push, secret handling, and use of credentials are not addressed.
11. The governance does not define precedence or a conflict-resolution process among normative documents, sprint artifacts, task instructions, and ad hoc Human Architect directions.
12. Approval evidence is not defined: there is no required approver identity, date, decision record, or location for task acceptance, governance activation, PR approval, and sprint closure.

### Governance Gaps

- A governance versioning, effective-date, amendment, and supersession mechanism.
- A state-transition matrix naming actor, prerequisites, evidence, and allowed next states for normal and exceptional task/sprint transitions.
- A rule that an executable task belongs to an ACTIVE sprint, or an explicit controlled exception for pre-sprint work.
- Enforceable GitHub requirements and an emergency/exception path.
- Standard traceability identifiers linking requirement, task, branch, diff, commit, PR, human acceptance, merge, and sprint closure.
- Controls for destructive Git/filesystem operations, secrets, credentials, force-pushes, and external side effects.
- A definition of mandatory tasks and a reconciliation check between sprint acceptance criteria and the board.
- A documented hierarchy and conflict-resolution rule for instructions.

### Recommended Changes

1. Resolve Draft versus normative status and add version, approval date, effective date, and change-control rules.
2. Require sprint activation before READY task execution, or document narrow, human-approved exceptions.
3. Add explicit task and sprint transition tables, including BLOCKED, CHANGES_REQUESTED, ON_HOLD, CANCELLED, reopening, and actor authority.
4. Define mandatory tasks and align the Sprint 00 board with every acceptance criterion, including initial BDD scenarios.
5. Replace advisory Git/GitHub language with a minimal required control set: protected `main`, sprint branch, human-reviewed PR, required checks where available, no force-push, and Human Architect merge approval.
6. Add lightweight task fields for branch, commit(s), PR, review decision, acceptance record, and exceptions; extend traceability through merge and sprint closure.
7. Clarify stage/commit/push permissions independently and prohibit destructive operations or credential use without explicit authorization.
8. Define document precedence and require recorded Human Architect approval for governance activation and amendments.
9. Keep process proportional: permit “not applicable” evidence for documentation-only tasks and avoid requiring one commit per task when a small, explicitly approved grouped documentation change is more reviewable.

### Review Outcome

- Risk level: HIGH. Human authority is well protected in principle, but lifecycle bypasses, advisory Git controls, and incomplete approval/traceability evidence could permit unauthorized or unreviewable changes once implementation begins.
- Final recommendation: CHANGES REQUIRED.
- No governance files, product code, dependencies, commits, pushes, merges, or DONE transitions were made.

## Acceptance Reconciliation

2026-08-08 — Human Architect accepted the review findings, which became the authorized basis for S00-009. S00-013 reconciled the task and board to DONE without inventing additional approval evidence.

## Completion Rule

Codex may move this task from READY to IN_PROGRESS and then to REVIEW.

Codex must not move this task to DONE.

Only the Human Architect may approve governance and move this task to DONE.
