# Sprint 00 Risks

## RISK-001 — Premature implementation

Risk:
Implementation begins before architecture and governance are stable.

Mitigation:
No functional MCP implementation during Sprint 00 without explicit approval.

## RISK-002 — Agent scope expansion

Risk:
The coding agent performs work beyond the authorized task.

Mitigation:
Only explicitly authorized READY tasks may be executed.

## RISK-003 — Governance drift

Risk:
Operational behavior diverges from repository governance.

Mitigation:
Governance files are normative and require Human Architect approval for changes.

## RISK-004 — Repository protection controls unverified

Risk:
Branch protection, required reviews/checks, and secret-scanning configuration have not been technically verified.

Mitigation:
Continue procedural enforcement of Governance Set 0.3 and require Human Architect review and merge of S00-013.

## RISK-005 — Local bootstrap artifacts pending disposition

Risk:
Ignored pre-baseline bootstrap artifacts remain locally present and are not suitable for publication unchanged.

Mitigation:
Keep them ignored and outside S00-013; disposition remains a separate Human Architect decision.
