# Business Requirements Discovery

## BRD-001: Employee Internal Transfer Request

**Feature Slug:** `employee-internal-transfer`

**Raised by:** INT Engineering SDD Developer Assessment

**Source Documents Read:**
- `source-docs/Requirement for SDD.pdf`
- `source-docs/INT SDD BluePrint - V1.0.pdf`

**Discovery Date:** 2026-08-27

**Discovery Status:** Draft for business clarification

### Day 1 - Discovery & Requirement Analysis

#### 1. Business Objective

The current internal transfer process requires the employee to interact with multiple teams and systems, creating a fragmented journey across manager confirmation, HR validation, organisation information changes, and possible payroll, IT, and facilities activities. The organisation wants a single digital journey in the One-Point Employee Portal so employees can initiate a transfer request, track progress in one place, and see which stakeholder actions are still pending while the portal orchestrates the downstream activities.

#### 2. Primary User

Employee.

#### 3. Secondary Stakeholders

| Stakeholder | Role in Journey | Expected Action | Source Status |
| --- | --- | --- | --- |
| Manager | Early stakeholder in transfer journey | Confirms the transfer | Confirmed that manager confirms transfer in current process; portal interaction model is open |
| HR | Eligibility/validation stakeholder | Validates eligibility | Confirmed |
| Organisation information owner/process | Updates employee organisational information | Updates organisation information after approval/validation | Confirmed that update occurs; ownership and trigger are open |
| Payroll | Downstream stakeholder when transfer impacts pay setup | May need to be updated | Confirmed as conditional activity; exact rules open |
| IT | Downstream stakeholder for access changes | May need to provision or remove access | Confirmed as conditional activity; exact rules open |
| Facilities | Downstream stakeholder for workplace arrangements | May need to arrange new location | Confirmed as conditional activity; exact rules open |
| Employee | Request initiator and status viewer | Submits request and receives confirmation | Confirmed |

#### 4. Business Journey

**Confirmed Journey Steps**

1. Employee initiates an Internal Transfer Request in the One-Point Employee Portal.
2. Employee selects proposed new department/business unit.
3. Employee selects proposed new location.
4. Employee selects proposed new role/job position.
5. Employee provides an effective date.
6. Employee may provide an optional reason for the transfer.
7. Employee submits the request.
8. Manager confirmation is part of the transfer journey.
9. HR validates eligibility.
10. Employee organisational information is updated.
11. Payroll may need to be updated.
12. IT may need to provision or remove access.
13. Facilities may need to arrange the employee's new location.
14. Employee receives confirmation.
15. Employee can view current request status and pending stakeholder actions through the portal.

**Journey Steps Requiring Clarification**

- Whether manager confirmation happens before or after employee submission in the portal.
- Whether manager confirmation is a hard approval gate or an advisory/recorded acknowledgement.
- Whether HR validation occurs before all downstream actions or in parallel with some of them.
- Which downstream activities are mandatory versus conditional by transfer type.
- Whether organisational information is updated before all downstream tasks complete or only after final completion.
- What event triggers employee confirmation and whether intermediate notifications are required.
- Whether the employee can edit or cancel a request after submission.
- What the end-state statuses are and which stakeholder owns each transition.

#### 5. Journey Stages

1. Request initiation
2. Proposal data capture
3. Request submission
4. Manager confirmation
5. HR validation
6. Downstream operational processing
7. Employee progress visibility
8. Final confirmation

#### 6. Confirmed Business Requirements

| ID | Requirement | Source |
| --- | --- | --- |
| FR-01 | The journey is for an employee internal transfer request through the One-Point Employee Portal. | Requirement document |
| FR-02 | The employee can initiate an Internal Transfer Request. | Requirement document |
| FR-03 | The employee can select the proposed new department/business unit. | Requirement document |
| FR-04 | The employee can select the proposed new location. | Requirement document |
| FR-05 | The employee can select the proposed new role/job position. | Requirement document |
| FR-06 | The employee provides an effective date. | Requirement document |
| FR-07 | The employee may provide an optional reason for the transfer. | Requirement document |
| FR-08 | The employee can submit the request. | Requirement document |
| FR-09 | The employee can view the current status of the request. | Requirement document |
| FR-10 | The employee can view actions pending with other stakeholders. | Requirement document |
| FR-11 | The portal should orchestrate downstream activities. | Requirement document |
| FR-12 | The portal should provide the employee with a single view of progress. | Requirement document |

#### 7. Business Rules

| ID | Business Rule | Source Status |
| --- | --- | --- |
| BR-01 | Employee is the requester for this journey. | Confirmed |
| BR-02 | Department/business unit selection is part of request submission. | Confirmed |
| BR-03 | Location selection is part of request submission. | Confirmed |
| BR-04 | Role/job position selection is part of request submission. | Confirmed |
| BR-05 | Effective date must be provided. | Confirmed |
| BR-06 | Reason for transfer is optional. | Confirmed |
| BR-07 | Employee can submit the request through the portal. | Confirmed |
| BR-08 | Employee can view current status after submission. | Confirmed |
| BR-09 | Employee can view pending actions with other stakeholders. | Confirmed |
| BR-10 | Manager confirmation is part of the overall business journey. | Confirmed |
| BR-11 | HR validates eligibility as part of the journey. | Confirmed |
| BR-12 | Payroll activity may be required for some transfers. | Confirmed |
| BR-13 | IT activity may be required for some transfers. | Confirmed |
| BR-14 | Facilities activity may be required for some transfers. | Confirmed |
| BR-15 | Only eligible employees may proceed with transfer processing. | Open |
| BR-16 | Duplicate active transfer requests from the same employee are prevented or handled explicitly. | Open |
| BR-17 | Submitted requests can be edited before approval/processing begins. | Open |
| BR-18 | Submitted requests can be cancelled by the employee or an administrator under defined conditions. | Open |
| BR-19 | Rejection conditions and consequences are defined for manager/HR/downstream stakeholders. | Open |
| BR-20 | Notification events and recipients are defined. | Open |
| BR-21 | Effective date must satisfy minimum lead time, future-date, or payroll cutoff rules. | Open |
| BR-22 | Status lifecycle values are defined and stable across stakeholders. | Open |

#### 8. Business Decisions

**Decided**

- The primary requester is the employee.
- The journey is exposed through the One-Point Employee Portal.
- The request captures proposed department/business unit, location, role/job position, effective date, and optional reason.
- The employee can submit the request.
- The employee can view request status.
- The employee can view pending actions with other stakeholders.
- The portal is intended to orchestrate downstream activities and provide a single progress view.

**Open Business Decisions**

- Employee eligibility criteria for initiating a transfer.
- Whether manager confirmation is mandatory in all cases.
- Whether HR validation is mandatory in all cases.
- Which downstream activities are mandatory, conditional, or optional.
- Approval and rejection rules.
- Status lifecycle and completion definition.
- Duplicate request handling.
- Edit and cancellation rules.
- Effective-date validation rules.
- Notification requirements and SLA expectations.

#### 9. Technical Decisions

**Decided**

- Frontend technology: Next.js
- Backend technology: Node.js
- Database technology: PostgreSQL

**Open Technical Decisions / Needs Architecture Review**

- API framework
- ORM or data-access approach
- Authentication mechanism
- Authorisation model
- Workflow/orchestration implementation approach
- Integration approach to HR/payroll/IT/facilities systems or processes
- Notification mechanism
- Audit-log implementation
- Retry/failure recovery approach for downstream activity failures
- Reference-data source for departments, locations, and roles

#### 10. Assumptions

| ID | Assumption | Why Needed | Must Be Confirmed? |
| --- | --- | --- | --- |
| A-01 | The transfer request is for existing authenticated employees of the portal. | The requirement names the employee portal but does not define access entry conditions. | Yes |
| A-02 | Department/business unit, location, and role/job position options come from an existing reference source or process. | The employee must select these values, but the source of truth is not stated. | Yes |
| A-03 | Status visibility applies after submission, not only at final completion. | The requirement says the employee can view current status, but timing is not defined. | Yes |
| A-04 | Pending actions shown to the employee are stakeholder-level, not detailed internal sub-tasks. | The granularity of pending-action visibility is not defined. | Yes |
| A-05 | Payroll, IT, and facilities activities are conditional based on transfer details. | The source uses "may need," implying conditional execution. | No |
| A-06 | Organisational information update occurs after at least one business validation step. | Sequence is not defined, but some ordering is required to map the journey. | Yes |
| A-07 | The portal orchestrates existing downstream systems or manual processes rather than replacing them. | The requirement frames the portal as a single journey over multiple teams/systems. | Yes |
| A-08 | The feature should produce an auditable request history even though the exact audit requirement is not yet defined. | Enterprise HR-related journeys usually need traceability, and the blueprint emphasizes accountability. | Yes |

#### 11. Dependencies

**Business Dependencies**

- Manager confirmation process
- HR eligibility validation process
- Organisation information update process
- Payroll update process
- IT access provisioning/de-provisioning process
- Facilities arrangement process
- Business ownership for approval, rejection, and completion decisions

**Technical Dependencies**

- Existing employee authentication capability needs to be confirmed.
- Employee identity and profile source needs to be confirmed.
- Department/business unit reference-data source needs to be confirmed.
- Location reference-data source needs to be confirmed.
- Role/job position reference-data source needs to be confirmed.
- Existing HR system/process integration needs to be confirmed.
- Existing payroll system/process integration needs to be confirmed.
- Existing IT system/process integration needs to be confirmed.
- Existing facilities system/process integration needs to be confirmed.
- Existing notification mechanism needs to be confirmed.
- Existing audit/logging standards for employee workflows need to be confirmed.

#### 12. Failure / Edge-Case Discovery

| Scenario | Current Requirement | What Is Known | What Is Unknown | Decision Required | Priority |
| --- | --- | --- | --- | --- | --- |
| Manager rejects request | Manager is part of journey | Manager confirms transfer in current process | Whether rejection exists in portal flow, and what happens next | Define rejection path and employee visibility | P0 |
| HR rejects eligibility | HR validates eligibility | HR validation is confirmed | Rejection criteria, downstream impact, resubmission path | Define HR rejection rules | P0 |
| Downstream system/process unavailable | Portal orchestrates downstream activities | Multiple downstream activities exist | Retry, fallback, manual handling, employee messaging | Define failure handling policy | P0 |
| Payroll activity fails | Payroll may need update | Payroll can be part of journey | Whether request can complete partially or remain blocked | Define partial completion rules | P1 |
| IT activity fails | IT may provision/remove access | IT can be part of journey | Whether access failure blocks effective transfer | Define dependency criticality | P1 |
| Facilities activity fails | Facilities may arrange location | Facilities can be part of journey | Whether facilities is mandatory before completion | Define completion dependency | P1 |
| Multiple downstream activities fail | Portal orchestrates several stakeholders | Parallel/serial model is unspecified | Consolidated status, retry ownership, escalation | Define orchestration failure model | P0 |
| Request remains pending beyond effective date | Effective date is captured | Effective date exists | Breach handling, escalation, employee messaging | Define overdue behaviour | P1 |
| Selected role becomes unavailable | Employee selects proposed role | Role selection is required | Reservation, validation timing, rejection path | Define stale reference-data handling | P1 |
| Selected location becomes unavailable | Employee selects proposed location | Location selection is required | Revalidation and alternate selection flow | Define unavailable-location handling | P1 |
| Employee submits duplicate requests | Employee can initiate and submit request | Submission is confirmed | Whether multiple active requests are allowed | Define duplicate handling | P0 |
| Employee attempts to edit submitted request | Submission is confirmed | Post-submit behaviour is unspecified | Edit window, approval impact, audit handling | Define edit policy | P0 |
| Employee wants to cancel request | Submission is confirmed | Cancellation is unspecified | Allowed stages, stakeholder impact, rollback rules | Define cancellation policy | P0 |
| Downstream activity partially completes | Multi-team journey is confirmed | Some steps may finish while others fail | Final status, rollback, retry, employee visibility | Define partial completion semantics | P0 |

#### 13. Security Discovery

- Authentication model for employee access is not defined and must be confirmed before specification.
- Authorisation boundaries for employee, manager, HR, payroll, IT, and facilities users/processes are not defined.
- Rules for who can view only their own request versus team/assigned worklists are not defined.
- PII categories in the transfer journey must be identified so specs and prompts remain clean of sensitive data.
- Audit trail requirements for submission, approvals, rejections, status transitions, and downstream actions are not defined.
- Logging rules for employee workflow data need confirmation; the blueprint prohibits secrets and PII in artefacts and prompt history.
- Encryption requirements for data at rest and in transit are not yet stated for this project.
- API rate-limit decisions will be required once API contracts are defined.
- Secret management approach for any downstream integrations is not yet defined.
- Security scanning, dependency vetting, and least-privilege integration access must be applied at later stages per the blueprint.

#### 14. Out of Scope

- Building a new HR system
- Building a new payroll system
- Building a new IT provisioning system
- Building a new facilities management system
- Recruitment functionality
- Performance management functionality
- Unrelated employee profile management changes
- Replacing downstream enterprise systems

**Scope Decision Required**

- Whether the portal performs direct system integration, workflow handoff, or manual task orchestration only
- Whether notifications are in scope for the first feature version
- Whether manager/HR stakeholder UIs are part of this same feature or separate features

#### 15. Open Questions

**P0 - Must be answered before specification can be considered ready**

1. What are the employee eligibility rules for initiating an internal transfer request?
2. Is manager confirmation mandatory, and at what exact point in the journey does it occur?
3. What exact checks does HR perform when validating eligibility?
4. Which downstream activities are mandatory, conditional, or optional for a given transfer?
5. What are the rejection behaviours for manager and HR outcomes?
6. What is the canonical request status lifecycle?
7. How should duplicate active requests be handled?
8. Can the employee edit a submitted request, and if so, under what constraints?
9. Can the employee cancel a submitted request, and how are downstream actions rolled back or stopped?
10. How should partial failure or downstream unavailability be handled and surfaced to the employee?

**P1 - Important for specification and planning**

1. What validation rules apply to the effective date?
2. What is the source of truth for department/business unit, location, and role/job position data?
3. What system or process is the source of truth for request status?
4. What notification events, channels, and recipients are required?
5. What level of detail should be shown for pending stakeholder actions?
6. What audit trail data must be captured and retained?

**P2 - Can be clarified later without blocking initial specification draft if assumptions are marked**

1. Are there SLA expectations for each stakeholder stage?
2. Is employee confirmation a portal status update only or an additional notification event?
3. Are attachments, comments, or supporting documents part of the journey?

#### 16. Prioritised Decisions Required

1. P0: Confirm eligibility, approval, rejection, edit, cancellation, duplicate, and status-lifecycle rules.
2. P0: Confirm downstream orchestration rules, including mandatory versus conditional stakeholder activities.
3. P0: Confirm failure and partial-completion behaviour.
4. P1: Confirm reference-data ownership and status source of truth.
5. P1: Confirm notification and audit expectations.
6. P1: Confirm stakeholder access boundaries for later security and API design.

#### 17. Day 1 Exit Criteria

- [x] Business problem understood
- [x] Primary user identified
- [x] Stakeholders identified
- [x] Journey mapped
- [x] Confirmed requirements separated from assumptions
- [x] Business decisions separated from technical decisions
- [x] Open questions identified
- [x] Dependencies identified
- [x] Failure scenarios identified
- [x] Security questions identified
- [x] Out-of-scope items identified
- [x] No implementation started
- [x] No unsupported requirements presented as confirmed requirements
- [x] No PII or secrets included
- [x] Feature slug established
- [ ] Discovery is sufficient to begin Day 2 specification work

#### 18. Next SDD Step

Per the INT SDD Blueprint, discovery is the source for specification authoring and the spec should not be the first place a requirement is written down. Day 2 specification authoring for `employee-internal-transfer` should begin only after the P0 business decisions above are confirmed or explicitly accepted as assumptions by the relevant business/security/architecture owners.

### Day 1 Self-Review

- [x] Business problem understood
- [x] Primary user identified
- [x] Stakeholders identified
- [x] Journey mapped
- [x] Confirmed requirements separated from assumptions
- [x] Business decisions separated from technical decisions
- [x] Open questions identified
- [x] Dependencies identified
- [x] Failure scenarios identified
- [x] Security questions identified
- [x] Out-of-scope items identified
- [x] No implementation started
- [x] No unsupported requirements invented
- [x] No PII or secrets included
- [x] Feature slug established
- [ ] Discovery is sufficient to begin Day 2 specification work

### Day 1 Report

- Files read from `source-docs/`: `Requirement for SDD.pdf`, `INT SDD BluePrint - V1.0.pdf`
- BRD/discovery file created: `.ai-context/BRD.md`
- Proposed feature slug: `employee-internal-transfer`
- Number of confirmed requirements: 12
- Number of assumptions: 8
- Number of P0 open questions: 10
- Number of P1 open questions: 6
- Key blockers before Day 2: eligibility rules, manager/HR decision rules, downstream activity rules, status lifecycle, duplicate/edit/cancellation policy, failure/partial-completion handling
- Readiness for specification authoring: Blocked pending P0 business clarification

Day 2 specification authoring is blocked until these business decisions are confirmed.
