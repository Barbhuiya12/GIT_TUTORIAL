# Part 4: The GitHub Workflow - Pull Requests

Now that you understand branching and merging, it's time to introduce the **Pull Request (PR)**, a cornerstone of collaborative development on GitHub (and similar platforms like GitLab or Bitbucket). Pull Requests are not just about merging code; they are a powerful tool for code review, discussion, and ensuring code quality.

## What is a Pull Request?

A Pull Request (often abbreviated as PR) is a mechanism for a developer to notify team members that they have completed a feature, bug fix, or other changes on a dedicated branch and want to merge those changes into a target branch (e.g., `main`).

## The Pull Request Workflow: A Step-by-Step Guide

### 1. Create a Feature Branch
```bash
git checkout -b feature/your-feature-name
```

### 2. Make Your Changes
Make your code changes in the feature branch.

### 3. Commit Your Changes
```bash
git add .
git commit -m "Add your commit message here"
```

### 4. Push to Remote
```bash
git push -u origin feature/your-feature-name
```

### 5. Create a Pull Request
1. Go to your repository on GitHub
2. Click on "Compare & pull request"
3. Add a title and description
4. Click "Create pull request"

### 6. Code Review
- Team members review your code
- Make changes if requested
- Push new commits to the same branch

### 7. Merge the Pull Request
Once approved, you can merge your PR:
1. Click "Merge pull request"
2. Choose merge method (merge commit, squash, or rebase)
3. Delete the feature branch

## Best Practices
- Keep PRs small and focused
- Write clear commit messages
- Include tests when applicable
- Update documentation if needed
- Get required approvals before merging

## Resolving Merge Conflicts
If there are conflicts:
1. Pull the latest changes from main
2. Resolve conflicts locally
3. Commit the resolved changes
4. Push to your feature branch

## Common Commands
```bash
# Update your local main branch
git checkout main
git pull origin main

# Create and switch to new branch
git checkout -b feature/name

# After making changes
git add .
git commit -m "Your message"
git push -u origin feature/name
```

## Next Steps
After your PR is merged, remember to:
1. Delete the local feature branch
2. Update your local main branch
3. Start a new feature branch for your next task

---

This is a concise guide to working with Pull Requests. For more detailed information, refer to the official GitHub documentation.