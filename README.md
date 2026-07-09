# Cloud Engineering Portfolio — Folder Skeleton

This is a starter skeleton for organizing GitHub repos during the Ironhack Cloud
Engineering bootcamp. It is NOT meant to be pushed as one single repo — see below.

## How to actually use this on GitHub

1. **01-learning-log/** → push this as ONE repo (e.g. `cloud-eng-learning-log`).
   This is your running journal across the whole bootcamp. Not pinned — it's proof of
   consistent daily work (GitHub shows your contribution graph from this).

2. **02 through 07** → push EACH of these as its OWN separate repo on GitHub.
   Why separate, not combined: GitHub's pin feature works per-repo (you can pin up to 6),
   so separate repos let each project stand on its own and get pinned individually.
   Suggested repo names:
   - `vpc-three-tier-app`
   - `terraform-iac-modules`
   - `cicd-pipeline-project`
   - `observability-dashboard`
   - `security-compliance-baseline`
   - `cloud-capstone-project` ← pin this one first, it's your best showcase piece

3. **08-social-content-tracker/** → keep this PRIVATE (or just local, not on GitHub at all).
   It's your own working notes for LinkedIn drafts — not something to make public.

## Handling secrets: the `.env.example` workflow

Every project folder (02–07) includes a `.env.example` file with placeholder variable
names for AWS, Azure, and GCP — prefixed (`AWS_`, `AZURE_`, `GCP_`) so you know which
provider each value belongs to. It contains NO real values, so it's safe to commit.

On day 1 of each project:
```bash
cd 02-vpc-three-tier-app
cp .env.example .env
# now open .env and fill in your REAL credentials
```
`.env` is already covered by `.gitignore`, so it will never be committed or pushed.
Only fill in the section(s) (AWS/Azure/GCP) that are actually relevant to that project —
delete or ignore the rest.

If you ever add a new variable while working, add the placeholder version to
`.env.example` too (commit that change), so future-you remembers what's needed.

## Quick start for each project repo
```bash
cd 02-vpc-three-tier-app
git init
git add .
git commit -m "Initial commit: project structure"
git remote add origin <your-new-github-repo-url>
git push -u origin main
```

## Weekly habit
At the end of each class day:
1. Drop a screenshot into that module's `screenshots/` folder
2. Add 2-3 bullets to that module's README under "What I learned"
3. On post days (Tue/Thu), copy those bullets into `08-social-content-tracker/linkedin-drafts/`
