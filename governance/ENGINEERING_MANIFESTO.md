# Engineering Manifesto — myLinkedinMCP

> Document version: 0.2  
> Governance set: 0.3  
> Authority: Human Architect  
> Effective date: 2026-08-08  
> Status: Active

## Purpose

These are the durable engineering principles governing myLinkedinMCP.

## Core Principles

1. Human intent has final authority.
2. Specifications precede implementation.
3. AI agents operate only within explicit task and authority boundaries.
4. Changes MUST be small enough to review and trace.
5. Security and evaluation are part of development.
6. Generated code and generated evidence MUST be independently reviewable.
7. External side effects and destructive operations require explicit authority.
8. Git is the canonical history of accepted engineering changes.
9. Sprint artifacts preserve operational memory but do not override governance.
10. Governance MUST NOT be weakened or activated autonomously by an AI agent.
11. Credentials and secrets MUST be minimized, protected, and excluded from repository history.
12. Evidence MUST be proportional to risk and change type, without sacrificing required traceability.
13. Autonomy is task-scoped, defaults to LOW when undeclared, and cannot be self-escalated by an AI agent.

## Human-in-the-Loop

The Human Architect owns product intent, architecture, scope, governance approval, risk acceptance, task authorization and acceptance, merge approval, and sprint closure. AI agents MAY propose and implement changes within an authorized task but possess no final acceptance authority.
