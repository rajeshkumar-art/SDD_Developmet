# SDD Development - Employee Internal Transfer

This repository contains the Software Design Document (SDD) discovery work for the Employee Internal Transfer journey in the One-Point Employee Portal.

## Project Breakthrough

The core project objective is to convert the current fragmented internal transfer process into a single employee-facing digital journey. Instead of requiring an employee to coordinate separately with managers, HR, organisation-information owners, payroll, IT, and facilities teams, the portal should let the employee initiate a transfer request, submit the required proposal details, and track the request status from one place.

The first discovery pass focused on the Employee Internal Transfer Request feature and produced the initial business requirements record in `.ai-context/BRD.md`.

## Feature Scope

- Employee initiates an internal transfer request.
- Employee selects proposed department or business unit.
- Employee selects proposed location.
- Employee selects proposed role or job position.
- Employee provides an effective date.
- Employee may provide an optional transfer reason.
- Employee submits the request through the portal.
- Employee can view current request status.
- Employee can view actions pending with other stakeholders.
- The portal coordinates downstream activities with manager, HR, payroll, IT, and facilities stakeholders.

## Current Discovery Status

Day 1 discovery is complete and documented as a draft for business clarification.

The discovery output includes:

- Business objective and user journey.
- Primary and secondary stakeholders.
- Confirmed business requirements.
- Business rules and open decision points.
- Assumptions and dependencies.
- Failure and edge-case discovery.
- Security considerations.
- Day 1 readiness summary.

## Technology Direction

The confirmed technology direction from the source material is:

- Frontend: Next.js
- Backend: Node.js
- Database: PostgreSQL

Further architecture decisions remain open, including API framework, authentication, authorization, workflow orchestration, integration approach, audit logging, notifications, and retry/failure recovery.

## Repository Contents

- `.ai-context/BRD.md` - Day 1 business requirements discovery and requirement analysis.
- `README.md` - Initial project overview.
- `.gitignore` - Keeps local Excel, PDF, and Word files out of source control.

## Files Not Committed

The source documents and day-to-day activity workbook are intentionally excluded from git:

- Excel files
- PDF files
- Word files

These files remain local only and are ignored by `.gitignore`.

## Next Step

The next SDD step is to resolve the P0 business questions documented in `.ai-context/BRD.md`, then proceed to the Day 2 feature specification with API contracts, acceptance criteria, and test-case derivation.
