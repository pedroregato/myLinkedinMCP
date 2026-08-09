# Git & GitHub Versioning Policy — myLinkedinMCP

> Document version: 0.2  
> Governance set: 0.3  
> Authority: Human Architect  
> Effective date: 2026-08-08  
> Status: Active

---

## 1. Purpose

This policy defines the mandatory rules for version control, branching, commits,
GitHub operations, traceability, review, and integration in the myLinkedinMCP project.

Its goals are to ensure that every governed change is:

- authorized;
- traceable;
- reviewable;
- reversible when reasonably possible;
- free from secrets and sensitive data;
- associated with an approved task;
- integrated only through controlled Git and GitHub operations.

This document is normative.

When a task, prompt, agent instruction, or local workflow conflicts with this policy,
the more restrictive rule applies unless the Human Architect explicitly authorizes
a documented exception.

---

## 2. Scope

This policy applies to:

- Human Architect;
- Codex;
- future AI coding agents;
- local Git operations;
- GitHub branches;
- commits;
- pushes;
- Pull Requests;
- reviews;
- merges;
- branch deletion;
- force-push operations;
- repository security checks;
- sprint integration;
- release-oriented versioning when applicable.

This policy applies to both documentation and executable-code changes.

---

## 3. Core Principles

### 3.1 Git is the engineering history

Git is the canonical technical history of changes made to the project.

Conversation context, terminal history, and AI session memory are not substitutes
for committed project history.

### 3.2 Every governed change belongs to a task

Every material change MUST be associated with an authorized task.

A commit MUST reference its Task ID.

Example:

```text
docs: define product vision [S00-001]
```

### 3.3 Small, focused changes

Commits MUST be:

- small;
- cohesive;
- reviewable;
- limited to the authorized task scope.

Unrelated changes MUST NOT be included in the same commit.

Opportunistic refactoring is prohibited unless explicitly authorized.

### 3.4 Human acceptance is distinct from implementation

Implementation does not imply acceptance.

An AI agent may produce code, documentation, tests, diffs, commits, and Pull Requests
within its authorized scope.

Only the Human Architect may perform final acceptance when governance requires it.

### 3.5 Public repository assumption

Unless explicitly changed by the Human Architect, the repository MUST be treated
as publicly visible.

Anything committed or pushed MUST be considered potentially accessible to third parties.

The following MUST NOT be committed or pushed:

- API keys;
- access tokens;
- passwords;
- private certificates;
- `.env` contents;
- credentials;
- authentication cookies;
- personal secrets;
- unnecessary PII;
- private datasets;
- confidential exported files;
- local-machine artifacts containing sensitive information.

---

## 4. Branching Strategy

### 4.1 Integration branch

`main` is the canonical integration branch.

Direct development on `main` is prohibited for governed sprint work.

### 4.2 Sprint branches

Each sprint SHOULD use a dedicated branch.

Naming convention:

```text
sprint/<number>-<short-name>
```

Examples:

```text
sprint/00-foundation
sprint/01-mcp-core
sprint/02-profile-domain
```

### 4.3 Task branches

Task branches MAY be used when isolation provides value.

Naming conventions:

```text
feature/<task-id>-<short-description>
fix/<task-id>-<short-description>
docs/<task-id>-<short-description>
refactor/<task-id>-<short-description>
test/<task-id>-<short-description>
```

Examples:

```text
feature/S01-003-profile-domain
fix/S02-007-provider-timeout
docs/S00-012-versioning-policy
test/S01-005-profile-provenance
```

### 4.4 Branch selection rule

Before modifying files, an agent MUST identify the intended branch.

If branch context is ambiguous, the agent MUST stop before committing or pushing
and request Human Architect clarification.

---

## 5. Commit Policy

### 5.1 Task traceability

Every governed commit MUST include the corresponding Task ID.

Examples:

```text
docs: define product vision [S00-001]
docs: harden development governance [S00-009]
feat: add profile domain model [S01-003]
fix: handle provider timeout [S02-007]
test: add profile provenance coverage [S01-005]
```

### 5.2 Commit message convention

Preferred format:

```text
<type>: <short description> [TASK-ID]
```

Recommended types:

```text
feat
fix
docs
test
refactor
chore
ci
build
perf
security
```

Examples:

```text
docs: formalize Codex autonomy levels [S00-011]
security: add secret handling rules [S00-012]
chore: establish sprint branch baseline [S00-013]
```

### 5.3 Commit quality

Before a governed commit:

- the diff MUST be reviewed;
- relevant checks MUST have been executed;
- unrelated changes MUST be excluded;
- sensitive data MUST be checked;
- the Task ID MUST be correct;
- the working scope MUST match the task authorization.

### 5.4 Grouped commits

A task SHOULD normally produce focused commits.

Multiple small documentation changes MAY be grouped into one commit when:

- they belong to the same authorized task;
- they form one coherent change;
- traceability remains clear;
- the Human Architect has not required finer granularity.

---

## 6. Staging Policy

`git add` is a distinct operation from `git commit`.

Staging MUST NOT be interpreted as approval to commit.

Before staging, the agent SHOULD inspect:

```text
git status
git diff
```

When relevant, the agent SHOULD stage only explicitly intended files.

Example:

```text
git add governance/GIT_GITHUB_VERSIONING_POLICY.md
```

Broad staging such as:

```text
git add .
```

SHOULD be avoided when unrelated or unreviewed files may exist.

---

## 7. Push Policy

### 7.1 Push is a separate authority

Permission to commit does not imply permission to push.

Permission to push MUST be explicitly granted by:

- the task;
- the autonomy level;
- or the Human Architect.

### 7.2 Push to main

Direct push to `main` is prohibited by default.

Expected flow:

```text
working branch
    ↓
commit
    ↓
push branch
    ↓
Pull Request
    ↓
review
    ↓
merge
```

### 7.3 First governed push

Before the first governed push, the repository MUST pass the checklist defined
in Section 14.

---

## 8. Pull Request Policy

### 8.1 Pull Requests as integration gates

Sprint or task integration SHOULD use Pull Requests.

A Pull Request MUST identify:

- sprint;
- relevant Task IDs;
- purpose;
- changed scope;
- verification performed;
- known risks;
- unresolved issues.

### 8.2 Human review

An AI agent MUST NOT approve its own Pull Request.

Where Human Architect approval is required by governance, merge MUST NOT occur
before that approval.

### 8.3 Reviewed head

The commit reviewed by the Human Architect SHOULD be identifiable.

If commits are added after review, the relevant changes MUST be reviewed again
before final merge.

---

## 9. Merge Policy

### 9.1 Main merge authority

Merge into `main` is reserved to the Human Architect by default.

Codex MUST NOT merge into `main` unless a future governance amendment explicitly
permits a narrowly defined operation.

### 9.2 Merge prerequisites

Before merge:

- required task acceptance MUST be complete;
- required checks MUST pass;
- unresolved critical risks MUST be addressed or explicitly accepted;
- relevant review evidence MUST exist;
- the reviewed branch head MUST match the merge candidate.

### 9.3 Sprint merge

A sprint SHOULD normally be integrated after:

```text
all mandatory tasks accepted
        ↓
Sprint REVIEW
        ↓
Pull Request reviewed
        ↓
Human approval
        ↓
merge to main
        ↓
Sprint CLOSED
```

---

## 10. Force-Push and Branch Deletion

### 10.1 Force-push

Force-push is prohibited by default.

Force-push to protected branches is prohibited.

An exception requires:

- explicit Human Architect authorization;
- recorded reason;
- affected branch;
- expected impact;
- recovery plan.

### 10.2 Branch deletion

Protected branches MUST NOT be deleted by AI agents.

Task or sprint branches MAY be deleted only when:

- the work has been integrated or intentionally abandoned;
- no necessary evidence depends on the branch;
- deletion is authorized.

---

## 11. Authority Matrix

| Operation | LOW | STANDARD | ELEVATED | Human Architect |
|---|---|---|---|---|
| `git status` | Allowed | Allowed | Allowed | Allowed |
| `git diff` | Allowed | Allowed | Allowed | Allowed |
| `git log` | Allowed | Allowed | Allowed | Allowed |
| `git branch` inspection | Allowed | Allowed | Allowed | Allowed |
| `git add` | Approval required | Allowed within task scope | Allowed within task scope | Allowed |
| `git commit` | Approval required | Only if task explicitly permits | Allowed if explicitly authorized | Allowed |
| Create branch | Approval required | Approval required unless task permits | Allowed if explicitly authorized | Allowed |
| `git push` task/sprint branch | Prohibited | Human approval required | Allowed if explicitly authorized | Allowed |
| Create/update Pull Request | Prohibited | Human approval required | Allowed if explicitly authorized | Allowed |
| Approve Pull Request | Prohibited | Prohibited | Prohibited | Allowed |
| Merge into `main` | Prohibited | Prohibited | Prohibited by default | Allowed |
| Force-push protected branch | Prohibited | Prohibited | Prohibited | Explicit exception only |
| Delete protected branch | Prohibited | Prohibited | Prohibited | Explicit exception only |
| Modify credentials/secrets | Prohibited | Prohibited without dedicated approval | Dedicated authorization required | Allowed when appropriate |
| Rewrite public Git history | Prohibited | Prohibited | Prohibited by default | Explicit exception only |

### 11.1 Operation-Specific Authority

Git permissions are granted per operation.

An autonomy level MUST NOT be interpreted as unrestricted Git authority.

For example:

```text
Autonomy-Level: ELEVATED
```

does not automatically authorize:

```text
git push
git merge
git push --force
branch deletion
```

Each sensitive Git operation requires explicit authorization under this policy.

### 11.2 Restrictive precedence

Task-specific restrictions override general autonomy permissions.

When authorization is ambiguous:

> The more restrictive interpretation applies.

The agent MUST request Human Architect clarification before proceeding.

---

## 12. Naming Conventions

### 12.1 Sprint branches

```text
sprint/00-foundation
sprint/01-mcp-core
sprint/02-profile-domain
```

### 12.2 Feature branches

```text
feature/S01-003-profile-domain
feature/S02-004-github-provider
```

### 12.3 Fix branches

```text
fix/S02-007-provider-timeout
fix/S03-012-profile-null-handling
```

### 12.4 Documentation branches

```text
docs/S00-012-versioning-policy
```

### 12.5 Commit examples

```text
docs: define product vision [S00-001]
docs: harden development governance [S00-009]
docs: formalize Codex autonomy levels [S00-011]
feat: add profile domain model [S01-003]
fix: handle provider timeout [S02-007]
test: add provenance coverage [S01-005]
```

---

## 13. Traceability Model

Every governed change SHOULD be traceable through the following chain:

```text
Requirement / Acceptance Criterion
              ↓
             Task
              ↓
       Authorized Scope
              ↓
            Git Diff
              ↓
            Commit
              ↓
         Pull Request
              ↓
          Human Review
              ↓
           Acceptance
              ↓
             Merge
              ↓
        Sprint Closure
```

Task evidence SHOULD record, when applicable:

```text
Requirement:
Task ID:
Autonomy Level:
Authorized Scope:
Branch:
Files Changed:
Diff Summary:
Checks Executed:
Commit Hash:
Pull Request:
Reviewed Head:
Human Acceptance:
Merge Reference:
Sprint Closure Reference:
```

A field MAY use:

```text
N/A — <reason>
```

only when that evidence is genuinely unnecessary or the operation was not authorized.

`N/A` MUST NOT be used to bypass a required control.

---

## 14. First Governed Push Checklist

Before the first governed push:

- [ ] establish a known Git baseline;
- [ ] inspect `git status`;
- [ ] identify staged files;
- [ ] identify untracked files;
- [ ] review `.gitignore`;
- [ ] verify `.env` and secret files are ignored;
- [ ] inspect the complete intended diff;
- [ ] check for API keys, tokens, credentials, passwords, private keys, and secrets;
- [ ] check for unnecessary PII;
- [ ] check for confidential exported data or private artifacts;
- [ ] confirm the configured `origin`;
- [ ] confirm the active branch;
- [ ] create or switch to the authorized sprint/task branch;
- [ ] verify Task ID references;
- [ ] execute applicable checks;
- [ ] verify no unrelated files are staged;
- [ ] review commit message;
- [ ] ensure push is authorized;
- [ ] do not push directly to `main`.

If suspicious sensitive content is found:

1. stop;
2. do not stage, commit, or push it;
3. do not print the secret value;
4. report only the file/location and suspected secret type;
5. request Human Architect review.

---

## 15. Public Repository Security

Because the repository is currently public, every commit MUST be treated as potentially permanent public disclosure.

Deleting a secret in a later commit does not reliably remove it from Git history.

Therefore sensitive content MUST be prevented from entering Git history in the first place.

The following SHOULD be included in `.gitignore` when applicable:

```text
.env
.env.*
!.env.example

.idea/
.venv/
venv/

__pycache__/
*.py[cod]

.pytest_cache/
.mypy_cache/
.ruff_cache/

.coverage
htmlcov/

dist/
build/
*.egg-info/

*.pem
*.key
*.p12
*.pfx
```

Additional project-specific private artifacts MUST be added as they appear.

---

## 16. Credentials and Secrets

AI agents MUST NOT:

- invent credentials;
- expose credentials in logs;
- echo secret values unnecessarily;
- commit credentials;
- push credentials;
- copy credentials into Markdown;
- store raw secrets in task evidence.

If a secret is suspected:

```text
Detected:
- file/path
- suspected secret type

Not permitted:
- raw secret value
```

Secret rotation, revocation, or history rewriting requires explicit Human Architect direction.

---

## 17. Repository State and Clean Baseline

Before reliable task-to-commit traceability begins, the repository SHOULD have a known baseline.

A baseline includes:

- initialized Git repository;
- configured origin;
- reviewed `.gitignore`;
- known branch;
- understood tracked/untracked state;
- initial governed commit or explicitly documented pre-governance history.

Agents MUST NOT assume that an untracked file is safe to commit merely because it exists in the project directory.

---

## 18. GitHub Protection Controls

Where GitHub configuration supports it, the Human Architect SHOULD consider enabling:

- protected `main`;
- prohibition of force-push;
- Pull Request requirement;
- required reviews;
- required status checks;
- branch deletion protection;
- secret scanning;
- dependency/security alerts where appropriate.

Until technical protection is verified, governance MUST assume these protections may not exist and enforce the rules procedurally.

---

## 19. Checks Before Commit

Applicable checks depend on task type.

### Documentation-only task

```text
Markdown consistency
Git diff review
secret inspection
governance consistency
```

Tests MAY be:

```text
N/A — no executable behavior changed
```

### Python implementation task

Potential checks:

```text
ruff
mypy
pytest
coverage
security checks
dependency checks
```

Exact checks MUST follow project CI policy and task scope.

---

## 20. Pull Request Minimum Evidence

A governed Pull Request SHOULD contain:

```text
Sprint:
Tasks:
Purpose:
Scope:
Files Changed:
Checks:
Risks:
Known Limitations:
Required Human Decisions:
```

For sprint integration, the PR SHOULD also reference:

```text
Sprint acceptance criteria
Sprint execution log
Residual risks
Retrospective when required
```

---

## 21. Exception Handling

Any exception to this policy MUST record:

```text
Exception ID:
Requested operation:
Reason:
Risk:
Affected files/branches:
Requested by:
Approved by:
Approval date:
Expiration or scope:
Recovery/rollback plan:
```

An AI agent MUST NOT grant itself an exception.

---

## 22. Escalation

If an operation is needed but not authorized:

1. stop before executing it;
2. record the required operation;
3. explain why it is needed;
4. describe expected effect and risk;
5. request Human Architect authorization;
6. continue only after explicit approval.

---

## 23. Relationship With Autonomy Levels

This policy works together with:

```text
governance/AGENT_AUTHORITY_POLICY.md
governance/CODEX_AUTONOMY_LEVEL_POLICY.md
```

Autonomy determines the general execution envelope.

This policy defines the Git/GitHub-specific rules inside that envelope.

The following rule always applies:

> Autonomy is granted per task. Git authority is granted per operation.

A task may further reduce permissions.

A task MUST NOT silently expand them.

---

## 24. Relationship With Sprint Governance

This policy works together with:

```text
governance/SPRINT_LIFECYCLE_POLICY.md
```

Git operations MUST preserve sprint lifecycle controls.

For example:

```text
Codex implementation
       ↓
task REVIEW
       ↓
Human acceptance
       ↓
task DONE
```

does not automatically mean:

```text
Sprint CLOSED
```

Sprint closure remains governed separately.

---

## 25. Relationship With AGENTS.md

`AGENTS.md` SHOULD reference this policy rather than duplicate its complete contents.

Recommended repository-level rule:

```text
All Git and GitHub operations MUST comply with
governance/GIT_GITHUB_VERSIONING_POLICY.md.

When task-level instructions conflict with Git governance,
the more restrictive rule applies unless the Human Architect
explicitly authorizes and records an exception.
```

---

## 26. Versioning and Change Control

This policy itself is governed.

Any modification MUST:

- increment the document version when substantive;
- preserve change history;
- identify the reason for change;
- be associated with a governed task;
- receive Human Architect approval before becoming effective.

AI agents MUST NOT weaken or remove mandatory controls autonomously.

---

## 27. Supersession

Upon Human Architect approval, this document is intended to supersede:

```text
governance/GIT_CHANGE_MANAGEMENT_POLICY.md
```

The superseded document SHOULD NOT remain as a competing source of truth.

Its historical content may be:

- archived;
- referenced in version history;
- or replaced with a short pointer to this policy.

The active governance set MUST contain only one canonical Git/GitHub change-management policy.

---

## 28. Current Initial Decision

For the current project maturity:

```text
main
  ↓
protected conceptually and later technically

sprint/00-foundation
  ↓
current governed development branch

task commits
  ↓
Task ID required

push
  ↓
requires explicit authorization

Pull Request
  ↓
human-reviewed integration gate

merge to main
  ↓
Human Architect authority
```

Until governance explicitly changes these rules, AI agents MUST interpret them conservatively.

---

## 29. Golden Rule

> No Git or GitHub convenience overrides traceability, security, explicit authority, or Human Architect acceptance.
