# Week 1 — Cloud Fundamentals (Days 1–3)

## Day 1 — Cloud computing concepts + AWS account setup

- Cloud fundamentals felt familiar coming in from the AZ-900 cert —
  shared responsibility model, service types, regions and availability
  zones all mapped onto what I already knew from Azure.
- The main shift: seeing the same concepts implemented in AWS rather
  than just knowing them in theory. Different console, different naming,
  same underlying logic.
- Completed: AWS account setup, MFA on root, billing alerts, account
  hardening, exploring AWS services, AWS CLI basics.

## Days 2–3 — IAM users, groups, policies and roles

- Had prior exposure to IAM/RBAC from my pharma job, but that was
  managing an existing environment. Building it from scratch in AWS
  shows you why things are structured the way they are — the security
  logic becomes much clearer when you set it up yourself.
- The depth of AWS policy conditions genuinely surprised me — you can
  specify not just who can access what, but under exactly what
  circumstances (time of day, IP range, MFA state, resource tags).
  Far more granular than I expected.
- Challenged myself with ABAC (attribute-based access control) tagging
  — picked up the concept even if the full syntax isn't muscle memory
  yet. Worth revisiting once core IAM is more automatic.
- Completed: IAM users and groups lab, IAM policies and roles lab,
  IAM basics quiz.

## Ongoing — Git workflow

- Established a working routine: fork → pull to local → work on a
  separate branch → commit in small chunks after each task rather than
  one big push at the end. Keeping commits granular from day one.
- CLI syntax is the current weak spot — commands aren't there yet,
  especially under pressure. Expected at this stage, deliberate
  practice needed.

## What I'd do differently
- Slow down on ABAC until core IAM syntax is more automatic.
  Better to have solid fundamentals than half-understood advanced
  concepts early on.

## Up next — Day 3 (S3 storage)
- S3 fundamentals, security and access control, create S3 bucket lab,
  S3 static website lab.
