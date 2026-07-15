# Before Going Public 

This is my checklist before presenting anything from private to public,
to ensure that no secrets are committed at any stage of my learning process
and later on, when I'm confident enough to present my work straight to the public.

---
## Checklist: 

- [ ] **1. No secrets in any file** — search the whole repo for AWS keys, passwords,
      tokens, `.pem` files, `.env` values.
      
- [ ] **2. `.gitignore` exists and was committed from the start** — not added after
      the fact. If it was added late, secrets may still be sitting in old commits.
      
- [ ] **3. No `.tfstate` or `.tfvars` files tracked by git** — to ensure it doesn't
      contain real account IDs, IPs, or resource names.
      
- [ ] **4. README is filled in** — at minimum: what it is, tools used, what I learned.
      
- [ ] **5. No broken / half-written code on the main branch** — if it's not done,
      either finish it, or note clearly in the README that it's a work in progress.
      
- [ ] **6. Screenshots folder has all the essential images** 
      -if relevant to the project or for the documentation
      
- [ ] **7. Repo name and description are clear**
      —descriptive name and clear guidance on why I did it that way.
            

If all 7 are checked → safe to flip public.
If ANY are unchecked → fix that first, OR keep it private one more week.



## **Secret checking methods**

Before flipping ANY repo public, run this from inside the repo folder (Git Bash):

# Search tracked files for common secret patterns
git grep -i -E "AKIA[0-9A-Z]{16}|aws_secret|password\s*=|api_key|BEGIN PRIVATE KEY" -- . 2>/dev/null

If this returns nothing → clean.
If it returns ANY matches → STOP. Do not flip the public yet. Remove the secret,
rotate/regenerate that credential (treat it as compromised), and re-check.

 ⚠️ Important:  The internet **never** forgets. If a secret was ever committed
 in a later commit, it still exists in git history. **Deleting the file is NOT enough**.

**IF happens**
-  The safest fix is usually to delete the repo and recreate it fresh.
-  From the current clean files (it loses history, but history isn't the priority here).

---

## 📋 Step-by-Step for github commmit

**1.** .gitignore gets committed FIRST, on its own, before anything else.
   This guarantees nothing sensitive sneaks into commit #1.
   
**2.**  If my commit should be private, then confirm in GitHub's web UI
    that each repo shows as **Private** (look for the "Private" tag next to the repo name).

### During each bootcamp week (repeated weekly)

3. Work normally — commit how I go (after each meaningful task is done).

4. End of each class day: sum up what I've learnt while it's fresh
    and write it up.

5. When a project/module feels "done enough to show":
   - Run through the  Checklist for that specific repo.
   - Run the Step 3 secret-search command.
   - then commit
  
   - 
6. Same day as I post my learning log or showcase a bigger project,
   I should also post it on my LinkedIn.


**Thanks for reading it through. 
If you have a suggestion on how I should tailor my repo/ my work, text me on LinkedIn**
