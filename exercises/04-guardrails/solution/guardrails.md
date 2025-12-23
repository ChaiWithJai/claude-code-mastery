---
name: team-guardrails
description: MANDATORY safety rules for git, database, and deployment operations. Claude MUST check these before any destructive operation.
---

<essential_principles>
## NEVER Do These (Automatic Block)

### Git
1. **NEVER** run `git push origin main` directly
   → Use: `gh pr create` instead

2. **NEVER** run `git push --force` to main or master
   → Force push to feature branches only

3. **NEVER** run `git reset --hard` without explicit confirmation
   → Ask: "This will lose uncommitted changes. Proceed?"

4. **NEVER** run `git branch -D main` or `git branch -D master`
   → Protected branches cannot be deleted

### Secrets
5. **NEVER** commit files matching: `.env`, `credentials.*`, `*.pem`, `secrets.*`
   → Use `.gitignore` and environment variables

6. **NEVER** hardcode API keys, passwords, or tokens in code
   → Use: `os.environ.get("API_KEY")`

### Database
7. **NEVER** run `DELETE` or `UPDATE` without `WHERE` clause
   → Require explicit conditions for all modifications

8. **NEVER** run `DROP TABLE` in production without backup confirmation
   → Ask: "Have you backed up this table? Confirm: [table name]"

### Deployment
9. **NEVER** deploy to production on Friday after 2pm
   → Wait until Monday or get explicit approval

10. **NEVER** skip staging environment
    → All changes must go: dev → staging → production

## ALWAYS Do These

### Git Workflow
1. **ALWAYS** create feature branches for changes
   ```bash
   git checkout -b feature/my-change
   ```

2. **ALWAYS** push to feature branches, create PR
   ```bash
   git push -u origin feature/my-change
   gh pr create --title "..." --body "..."
   ```

3. **ALWAYS** check `git status` before committing
   → Review what's being committed

4. **ALWAYS** pull before pushing
   ```bash
   git pull origin main --rebase
   ```

### Before Destructive Operations
5. **ALWAYS** ask for confirmation with consequences
   ```
   "This will [consequence]. Type 'I understand' to proceed."
   ```

6. **ALWAYS** suggest the safe alternative first
   → "Instead of force push, consider: [safer option]"

## When User Requests Blocked Operation

If user explicitly requests a blocked operation:

1. **Explain** why it's dangerous
2. **Offer** the safe alternative
3. **If they insist**, require explicit acknowledgment:
   ```
   "I understand the risk of [operation]. Proceed anyway."
   ```

4. **Log the override** for audit purposes
</essential_principles>

<intake>
I notice you're about to perform a potentially dangerous operation.

**What operation?**
- Git push/force push
- Database modification
- Production deployment
- Other

**Have you:**
- [ ] Backed up if needed
- [ ] Tested in staging
- [ ] Gotten approval if required

**Confirm you want to proceed?**
</intake>
