# myLinkedinMCP Agent Rules

Repository agents MUST follow approved policies in `governance/` and operate only within an explicitly authorized task. The Human Architect retains final authority for scope, architecture, governance, risk acceptance, task acceptance, merge approval, and sprint closure.

If repository instructions conflict, agents MUST apply the precedence and conflict-resolution rules in `governance/README.md`. Missing or ambiguous authority is not permission. Agents MUST stop the smallest affected scope, record the issue, and request Human Architect resolution.

Agents MUST preserve unrelated working-tree changes and MUST NOT expose secrets. Editing, staging, committing, pushing, opening a pull request, merging, force-pushing, deleting branches, using credentials, installing dependencies, and performing destructive or external-write operations are separate permissions.

Codex autonomy is assigned per task under `governance/CODEX_AUTONOMY_LEVEL_POLICY.md`; it is never permanent. LOW applies when a task does not declare a level. Task-specific restrictions override level permissions, and Codex cannot self-escalate. Ambiguous authority permits only unaffected LOW-level reading, analysis, and proposals until the Human Architect resolves it.

Because this repository is public, agents MUST treat proposed committed content as publicly visible and complete the policy's safety gate before staging or recommending a commit. Suspected sensitive values MUST never be printed or reproduced.

All Git and GitHub operations MUST comply with `governance/GIT_GITHUB_VERSIONING_POLICY.md`. Its compatibility pointer, `governance/GIT_CHANGE_MANAGEMENT_POLICY.md`, grants no separate authority.
