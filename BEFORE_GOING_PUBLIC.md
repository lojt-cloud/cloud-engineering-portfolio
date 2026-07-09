# Before Going Public — Checklist & Step-by-Step

Use this every time you're about to flip a repo from Private → Public.
Takes 5 minutes. Do it every single time, even if you "already checked."

---

## ✅ The Checklist

Run through these in order, for the SPECIFIC repo you're about to flip:

- [ ] **1. No secrets in any file** — search the whole repo for AWS keys, passwords,
      tokens, `.pem` files, `.env` values. (See Step 3 below for the exact command.)
- [ ] **2. `.gitignore` exists and was committed from the start** — not added after
      the fact. If it was added late, secrets may still be sitting in old commits.
- [ ] **3. No `.tfstate` or `.tfvars` files tracked by git** — these often contain
      real account IDs, IPs, or resource names you don't want public.
- [ ] **4. README is filled in** — at minimum: what it is, tools used, what you learned.
      An empty README looks unfinished even if the code is fine.
- [ ] **5. No broken / half-written code on the main branch** — if it's not done,
      either finish it, or note clearly in the README that it's a work in progress.
- [ ] **6. Screenshots folder has at least one image** (if relevant to the project) —
      visual proof matters more than people expect.
- [ ] **7. Repo name and description are clear** — not "test" or "project1".

If all 7 are checked → safe to flip public.
If ANY are unchecked → fix that first, OR keep it private one more week.

---

## 🔍 Step 3 Detail: How to actually check for secrets

Before flipping ANY repo public, run this from inside the repo folder (Git Bash):

```bash
# Search tracked files for common secret patterns
git grep -i -E "AKIA[0-9A-Z]{16}|aws_secret|password\s*=|api_key|BEGIN PRIVATE KEY" -- . 2>/dev/null
```

If this returns nothing → clean.
If it returns ANY matches → STOP. Do not flip public yet. Remove the secret,
rotate/regenerate that credential (treat it as compromised), and re-check.

> ⚠️ Important: if a secret was ever committed — even once, even if you deleted it
> in a later commit — it still exists in git history. Deleting the file is NOT enough.
> If this happens, the safest fix is usually to delete the repo and recreate it fresh
> from your current clean files (you lose history, but history isn't the priority here).

---

## 📋 Step-by-Step: Full Workflow From Today Until Week 9

### Phase A — Do this now, before the bootcamp starts

1. Create GitHub repos for each project (see naming list below) — set ALL to **Private**.
2. For each repo, push the matching folder from your skeleton:
   ```bash
   cd 02-vpc-three-tier-app
   git init
   git add .gitignore
   git commit -m "Add gitignore before any other files"
   git add .
   git commit -m "Initial commit: project structure"
   git branch -M main
   git remote add origin <your-private-repo-url>
   git push -u origin main
   ```
   Note the order: `.gitignore` gets committed FIRST, on its own, before anything else.
   This guarantees nothing sensitive sneaks into commit #1.
3. Confirm in GitHub's web UI that each repo shows as **Private** (look for the
   "Private" tag next to the repo name).
4. Do NOT push `08-social-content-tracker` to GitHub at all — keep it local only,
   or in a private repo you never plan to flip public.

### Phase B — During each bootcamp week (repeat weekly)

5. Work normally — commit as you go (daily small commits, real messages).
6. End of each class day: drop a screenshot in, add 2-3 "what I learned" bullets
   to that module's README (per your existing habit).
7. When a project/module feels "done enough to show":
   - Run through the ✅ Checklist above for that specific repo.
   - Run the Step 3 secret-search command.
8. If everything passes:
   - GitHub → that repo → **Settings → General → Danger Zone → Change visibility
     → Make public** → type the repo name to confirm.
9. Pin it (if it's one of your best 6): GitHub profile → **Customize your pins**
   → select the repo.
10. Same day → post on LinkedIn (Tue/Thu) linking to the now-public repo.

### Phase C — Capstone (week 9)

11. Same checklist, extra care — this is your #1 most-viewed repo.
12. Make sure the architecture diagram and final README are genuinely polished
    before flipping public — this one is worth spending extra time on.

---

## 📁 Suggested repo names (private → public when ready)

- `cloud-eng-learning-log` (stays semi-private/personal — your call)
- `vpc-three-tier-app`
- `terraform-iac-modules`
- `cicd-pipeline-project`
- `observability-dashboard`
- `security-compliance-baseline`
- `cloud-capstone-project` ← your best showcase, pin this one first
