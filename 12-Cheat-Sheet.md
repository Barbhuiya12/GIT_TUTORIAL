# Git Cheat Sheet

This cheat sheet provides a quick reference for the most commonly used Git commands.

## Configuration

```bash
# Set your username globally
git config --global user.name "Your Name"

# Set your email address globally
git config --global user.email "youremail@example.com"

# View all global configurations
git config --global --list

# Set default editor
git config --global core.editor "code"
```

## Basic Workflow

```bash
# Initialize a new Git repository
git init

# Clone an existing repository
git clone <repository-url>

# Check the status of your working directory and staging area
git status

# Add files to the staging area
git add <file-name>     # Add specific file
git add .               # Add all new and modified files
git add -A              # Add all changes (new, modified, deleted)

# Commit changes
git commit -m "Descriptive commit message"

# View commit history
git log
git log --oneline       # Compact view
git log --graph         # Show branch graph
```

## Branching

```bash
# List all branches
git branch

# Create a new branch
git branch <branch-name>

# Switch to a branch
git switch <branch-name>

# Create and switch to a new branch
git switch -c <branch-name>

# Delete a branch
git branch -d <branch-name>

# Merge a branch into the current branch
git merge <branch-name>
```

## Remote Repositories

```bash
# View remote repositories
git remote -v

# Add a remote repository
git remote add origin <repository-url>

# Rename the current branch to main
git branch -M main

# Push changes to remote repository
git push -u origin main  # First push
git push                 # Subsequent pushes (if upstream is set)

# Pull changes from remote repository
git pull origin main
git pull                 # If upstream is set

# Fetch changes from remote (without merging)
git fetch origin
```

## Viewing Changes

```bash
# View changes in working directory
git diff

# View changes in staging area
git diff --staged

# View changes between two commits
git diff <commit1> <commit2>

# View commit details
git show <commit-hash>
```

## Undoing Changes

```bash
# Unstage a file
git restore --staged <file-name>

# Discard changes in working directory
git restore <file-name>

# Revert a commit (creates a new commit)
git revert <commit-hash>

# Reset to a previous commit (destructive)
git reset --hard <commit-hash>

# Amend the last commit
git commit --amend
```

## Stashing

```bash
# Save changes temporarily
git stash

# Save changes with a description
git stash push -m "Work in progress"

# View stashed changes
git stash list

# Apply the most recent stash
git stash pop

# Apply a specific stash
git stash apply stash@{n}

# Delete a stash
git stash drop stash@{n}
```

## Useful Tips

1. **Use aliases** to save time on frequently used commands:
   ```bash
   git config --global alias.st status
   git config --global alias.co checkout
   git config --global alias.br branch
   git config --global alias.ci commit
   ```

2. **Colorize output** for better readability:
   ```bash
   git config --global color.ui auto
   ```

3. **Set up automatic line endings conversion**:
   ```bash
   # On Windows
   git config --global core.autocrlf true
   
   # On Mac/Linux
   git config --global core.autocrlf input
   ```

4. **Use `.gitignore`** to exclude files from tracking.

5. **Write good commit messages**:
   - Use the imperative mood ("Add feature" not "Added feature")
   - Keep the first line under 50 characters
   - Add a blank line after the first line, then more detailed explanation if needed

This cheat sheet covers the most essential Git commands. For more advanced features, refer to the other sections of this tutorial.
