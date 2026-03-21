# Git Complete Notes

## 1. What is Git?
Git is a **Distributed Version Control System (DVCS)** used to track changes in source code during software development. It helps multiple developers work together efficiently.

---

## 2. Why Use Git?
- Track changes in code
- Collaborate with teams
- Maintain project history
- Revert to previous versions
- Work on multiple features using branches

---

## 3. Basic Git Workflow
1. Modify files
2. Add changes to staging area
3. Commit changes
4. Push to remote repository

---

## 4. Important Git Terminology

### Repository (Repo)
A project folder tracked by Git.

### Working Directory
Where you modify files.

### Staging Area (Index)
Area where files are added before committing.

### Commit
A snapshot of changes.

### Branch
A separate line of development.

### Remote
A version of your repository hosted online (e.g., GitHub).

---

## 5. Git Configuration

```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
```

Check configuration:

```bash
git config --list
```

---

## 6. Creating a Repository

Initialize new repo:

```bash
git init
```

Clone existing repo:

```bash
git clone <repository_url>
```

---

## 7. Checking Status

```bash
git status
```

---

## 8. Adding Files

```bash
git add filename
git add .
```

---

## 9. Committing Changes

```bash
git commit -m "Your commit message"
```

---

## 10. Viewing History

```bash
git log
git log --oneline
```

---

## 11. Branching

```bash
git branch branch_name
git checkout branch_name
git checkout -b branch_name
git branch
```

---

## 12. Merging

```bash
git checkout main
git merge branch_name
```

---

## 13. Resolving Conflicts
- Fix file manually
- `git add .`
- Commit changes

---

## 14. Remote Repositories

```bash
git remote add origin <url>
git push -u origin main
git pull
git fetch
```

---

## 15. Undoing Changes

```bash
git restore filename
git reset filename
git reset --soft HEAD~1
git reset --hard HEAD~1
```

---

## 16. Stashing

```bash
git stash
git stash apply
git stash list
```

---

## 17. Git Ignore

Create `.gitignore` file:

```
node_modules/
.env
*.log
```

---

## 18. Best Practices
- Write clear commit messages
- Commit small changes
- Use branches for features
- Pull before push
- Use .gitignore properly
