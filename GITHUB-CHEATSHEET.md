# GitHub & Git Cheatsheet

## Git Setup
```bash
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
git config --list  # View all config
```

## Initialize & Clone
```bash
git init                           # Initialize repo in current directory
git clone <url>                    # Clone remote repo
git clone <url> <folder-name>      # Clone into specific folder
```

## Basic Workflow
```bash
git status                         # Check status of files
git add <file>                     # Stage single file
git add .                          # Stage all changes
git commit -m "message"            # Commit staged changes
git push                           # Push commits to remote
git pull                           # Fetch and merge from remote
```

## Branches
```bash
git branch                         # List local branches
git branch -a                      # List all branches (local + remote)
git branch <branch-name>           # Create new branch
git checkout <branch-name>         # Switch to branch
git checkout -b <branch-name>      # Create and switch to branch
git switch <branch-name>           # Switch (newer syntax)
git switch -c <branch-name>        # Create and switch (newer)
git branch -d <branch-name>        # Delete local branch
git push origin <branch-name>      # Push branch to remote
git push origin --delete <branch-name>  # Delete remote branch
```

## Commits
```bash
git log                            # View commit history
git log --oneline                  # Compact log view
git log --graph --all --oneline    # Visual branch graph
git show <commit-hash>             # Show commit details
git diff                           # Show unstaged changes
git diff --staged                  # Show staged changes
git diff <branch1> <branch2>       # Compare branches
```

## Undo Changes
```bash
git restore <file>                 # Discard changes in file (unstaged)
git restore --staged <file>        # Unstage file
git reset HEAD~1                   # Undo last commit (keep changes)
git reset --soft HEAD~1            # Undo commit, keep staged
git reset --hard HEAD~1            # Undo commit, discard changes ⚠️
git revert <commit-hash>           # Create new commit that undoes change
git clean -fd                      # Remove untracked files ⚠️
```

## Stash (Temporary Storage)
```bash
git stash                          # Save current changes temporarily
git stash list                     # List all stashes
git stash pop                      # Apply and delete last stash
git stash apply stash@{0}          # Apply stash without deleting
git stash drop stash@{0}           # Delete stash
git stash clear                    # Delete all stashes
```

## Merging
```bash
git merge <branch-name>            # Merge branch into current branch
git merge --no-ff <branch-name>    # Merge with merge commit
git merge --squash <branch-name>   # Squash commits before merging
```

## Rebasing (Rewrite history)
```bash
git rebase <branch-name>           # Rebase current branch onto branch
git rebase -i HEAD~3               # Interactive rebase last 3 commits
# In interactive rebase editor: pick, reword, squash, fixup, drop
git rebase --abort                 # Cancel rebase
git rebase --continue              # Continue after resolving conflicts
```

## Remote
```bash
git remote -v                      # List remote repositories
git remote add origin <url>        # Add remote repo
git remote remove origin           # Remove remote
git remote rename origin upstream  # Rename remote
git fetch                          # Fetch updates from remote (no merge)
git fetch origin <branch>          # Fetch specific branch
git pull origin <branch>           # Fetch and merge specific branch
git push origin <branch>           # Push branch to remote
git push -u origin <branch>        # Push and set upstream
git push origin --all              # Push all branches
git push origin --tags             # Push all tags
```

## Tags
```bash
git tag                            # List tags
git tag <tag-name>                 # Create lightweight tag
git tag -a <tag-name> -m "msg"     # Create annotated tag
git show <tag-name>                # Show tag details
git push origin <tag-name>         # Push single tag
git push origin --tags             # Push all tags
git tag -d <tag-name>              # Delete local tag
git push origin --delete <tag-name> # Delete remote tag
```

## Cherry-pick
```bash
git cherry-pick <commit-hash>      # Apply specific commit to current branch
git cherry-pick <hash1> <hash2>    # Apply multiple commits
git cherry-pick --continue         # Continue after resolving conflicts
git cherry-pick --abort            # Cancel cherry-pick
```

## Search & Find
```bash
git grep "search-term"             # Search repo for text
git log -S "search-term"           # Find commits that changed search-term
git log --author="name"            # Find commits by author
git log --since="2 weeks ago"      # Find recent commits
git blame <file>                   # Show who changed each line
git bisect                         # Binary search for bad commit
```

## GitHub-Specific Workflows

### Fork & Pull Request
```bash
# 1. Fork repo on GitHub (click "Fork" button)
# 2. Clone your fork
git clone <your-fork-url>

# 3. Add upstream remote
git remote add upstream <original-repo-url>

# 4. Create feature branch
git checkout -b feature/my-feature

# 5. Make changes and commit
git add .
git commit -m "Add feature"

# 6. Push to your fork
git push origin feature/my-feature

# 7. Open Pull Request on GitHub

# 8. Keep fork synced
git fetch upstream
git rebase upstream/main
git push origin main
```

### Sync Fork with Original
```bash
git remote add upstream <original-repo-url>  # One-time setup
git fetch upstream
git checkout main
git merge upstream/main
git push origin main
```

## Conflicts Resolution
```bash
# After conflicting merge/rebase
# 1. Edit files and remove conflict markers (<<<<<<, ======, >>>>>>)
# 2. Stage resolved files
git add <file>

# 3. Complete the operation
git merge --continue   # or git rebase --continue
# or for merge: git commit
```

## Advanced

### Amend Commit
```bash
# Add forgotten changes to last commit
git add <file>
git commit --amend --no-edit      # Keep same message
git commit --amend                # Edit message
```

### Squash Commits
```bash
git rebase -i HEAD~3              # Interactive rebase last 3 commits
# Change "pick" to "squash" (or "s") for commits to squash
git push -f origin <branch>       # Force push (only on your branches!)
```

### Force Push (Use Carefully!)
```bash
git push -f origin <branch>       # Force push (overwrites remote)
git push --force-with-lease       # Safer force push
```

## GitHub CLI Commands
```bash
gh repo create                    # Create new repo
gh repo clone <owner/repo>        # Clone repo
gh pr create                      # Create pull request
gh pr list                        # List open PRs
gh pr view <number>               # View PR details
gh issue create                   # Create issue
gh issue list                     # List issues
gh release create <tag>           # Create release
```

## Common Workflows

### Daily workflow
```bash
git pull                          # Get latest changes
# Make changes
git add .
git commit -m "Fix: description"
git push
```

### Feature branch
```bash
git checkout -b feature/name
# Make changes
git add .
git commit -m "Feature: description"
git push -u origin feature/name
# Open PR on GitHub
```

### Keep branch updated
```bash
git fetch origin
git rebase origin/main            # Rebase current branch
# OR
git merge origin/main             # Merge main into current branch
git push -u origin <branch>       # Push updates
```

## Tips & Best Practices
1. **Commit messages:** Use present tense ("Add feature" not "Added feature")
2. **Atomic commits:** One logical change per commit
3. **Pull before push:** Always pull latest before pushing
4. **Branch naming:** Use `feature/`, `fix/`, `docs/` prefixes
5. **Never force push** to shared branches (main, develop)
6. **Review before merge:** Always review code in PRs
7. **Sync frequently:** Keep branches updated with main
8. **Use .gitignore:** Exclude files (node_modules, .env, build/)
9. **Write meaningful messages:** Future you will thank you
10. **Test before push:** Verify changes work locally

## Useful Aliases
```bash
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.ci commit
git config --global alias.unstage 'restore --staged'
git config --global alias.last 'log -1 HEAD'
git config --global alias.visual 'log --graph --oneline --all'
```

## Resources
- [Git Official Docs](https://git-scm.com/doc)
- [GitHub Docs](https://docs.github.com)
- [GitHub CLI Docs](https://cli.github.com/manual)
