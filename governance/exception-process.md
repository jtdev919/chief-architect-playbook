# Architecture Exception Process

## Purpose
Exceptions allow delivery to continue when standards or reference architectures cannot be followed.
They also prevent “temporary” deviations from becoming permanent technical debt.

## When an Exception Is Required
- Introducing a new platform/tool not in the standards catalog
- Bypassing reference architecture patterns (API, security, data, integration)
- Major deviations that increase operational risk or long-term cost

## Required Inputs (One Page Max)
1. **What standard is being bypassed?**
2. **Why is the standard not feasible here?**
3. **Proposed alternative** and rationale
4. **Risk assessment** (security, reliability, compliance, cost)
5. **Time-bound plan** (expire, remediate, or formalize)
6. **Owner** (person accountable)

## Approval Levels
- **Level 1 (Team / Domain):** low risk, localized impact
- **Level 2 (ARB):** cross-domain impact, security/compliance impact
- **Level 3 (Exec):** material cost/risk, precedent-setting exception

## Governance Mechanics
- Exceptions are logged with:
  - ID, owner, scope, approval date
  - expiration date or re-review date
  - remediation plan
- Exceptions are reviewed monthly/quarterly to ensure closure.

## Success Criteria
- Exceptions are rare, time-bound, and tracked to closure.
- Exceptions inform future standards updates when patterns recur.
