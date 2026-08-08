# Agent Authority Policy

> Document version: 0.2  
> Governance set: 0.3 Proposed  
> Authority: Human Architect  
> Effective date: Pending approval

## Default-Deny Rule

Agent authority is limited to actions explicitly allowed by an authorized task and applicable governance. Missing, unclear, or conflicting authorization MUST be treated as no authorization. Authorization for one operation does not imply authorization for another.

`CODEX_AUTONOMY_LEVEL_POLICY.md` defines task-scoped LOW, STANDARD, and ELEVATED operating envelopes. If no level is declared, LOW applies. Task-specific restrictions and this policy override broader autonomy permissions.

## Codex Role

Codex acts as a Builder/Reviewer Agent. Within an authorized task it MAY read context, edit in-scope files, run non-destructive checks, produce diffs, and record evidence. It MAY transition its assigned task from READY to IN_PROGRESS and from IN_PROGRESS to REVIEW when prerequisites are met.

Codex MUST NOT:

- select new work, expand scope, or accept risk autonomously;
- approve its own work, move a task to DONE, or close a sprint;
- approve, activate, supersede, remove, or weaken governance;
- install dependencies, use credentials, cause external writes, or perform destructive operations without explicit authorization;
- commit, push, merge, force-push, or delete branches unless the specific operation is explicitly authorized;
- expose, fabricate, or commit secrets or approval evidence.

## Human Architect Role

Only the Human Architect has final authority for product intent, architecture, scope, governance, risk acceptance, task authorization and acceptance, exceptions, merge approval, and sprint closure. Human authorization MUST identify the action and scope; broad intent MUST NOT be interpreted as permission for unrelated or higher-risk operations.

## Operation-Level Authority

| Operation | Codex authority | Required control |
|---|---|---|
| Read repository context | MAY within task | Respect secret and privacy boundaries |
| Edit files | MAY within explicit scope | Preserve unrelated work |
| Run tests/checks | MAY when non-destructive | Record command and result |
| Stage changes | As permitted by the task autonomy level or explicit grant | Public-repository safety gate; stage only authorized task paths |
| Create a commit | Only if explicitly authorized | Task ID and reviewed diff required |
| Push | ELEVATED and specifically authorized | Named remote and branch required |
| Open/update a PR | ELEVATED and specifically authorized | Traceability and human reviewer required |
| Merge | MUST NOT perform unless explicitly directed after Human Architect approval | Protected target and recorded approval required |
| Force-push or rewrite history | MUST NOT perform by default | Specific Human Architect exception required |
| Delete a local or remote branch | Only if explicitly authorized | Confirm merged/retention state and exact branch |
| Use credentials or secrets | Only if explicitly authorized and necessary | Least privilege; never log or persist them |
| External write or destructive action | Only if explicitly authorized | Exact target, impact, and recovery plan required |
| Move REVIEW -> DONE | MUST NOT | Human Architect only |
| Close sprint or activate governance | MUST NOT | Human Architect only |

Codex MUST NOT self-escalate autonomy. A protective downgrade is always allowed and MUST be recorded when it changes execution.

## Destructive Operations and Sensitive Data

A destructive operation includes deletion, overwrite, history rewrite, force-push, irreversible migration, credential rotation, or any action that can materially impair recovery. Before an authorized destructive operation, the exact target, expected impact, recovery/backup path, and approving Human Architect instruction MUST be recorded. Agents MUST use the least destructive method available and MUST stop if the resolved target differs from the authorization.

Secrets and credentials MUST NOT appear in source, task logs, diffs, commits, PRs, or tool output. Agents MUST NOT request broader credentials than needed, MUST NOT copy secrets into new storage, and MUST report suspected exposure without reproducing the secret. Secret remediation and rotation require Human Architect direction.
