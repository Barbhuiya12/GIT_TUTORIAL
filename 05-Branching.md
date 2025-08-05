# Part 3: Branching & Merging - Understanding Branches

One of Git's most powerful and fundamental features is its branching model. Branches allow you to diverge from the main line of development, work on new features or bug fixes in isolation, and then integrate those changes back into the main codebase. This is absolutely essential for teamwork, parallel development, and maintaining a stable project.

## What are Branches?

In Git, a branch is simply a lightweight, movable pointer to a commit. When you create a branch, you're not creating a copy of your entire project; you're just creating a new pointer that points to the same commit your current branch is pointing to. As you make new commits on that branch, the branch pointer automatically moves forward to the latest commit.

Think of it like this:
*   Your **commits** are snapshots of your project at a specific point in time.
*   Your **branches** are labels that point to a specific commit in your history.

By default, when you initialize a Git repository, you are on the `main` (or historically `master`) branch. This branch is typically considered the stable, production-ready version of your project.

## Why Use Branches? The Power of Isolation

Branches provide a powerful way to isolate your work, leading to several benefits:

*   **Feature Development:** You can work on a new feature on a dedicated branch without affecting the stable `main` branch. This means you can experiment, make mistakes, and iterate without breaking the main codebase for others or for deployment.
*   **Bug Fixes:** When a bug is found in the `main` branch, you can quickly create a bugfix branch, fix the issue, and then merge the fix back without disrupting ongoing feature development.
*   **Experimentation and Prototyping:** Want to try out a radical new idea or a different approach? Create an experimental branch. If it doesn't work out, you can simply delete the branch without leaving any trace in your main history.
*   **Parallel Development:** Multiple developers can work on different features simultaneously, each on their own branch. This significantly speeds up development cycles.
*   **Code Review:** Branches are integral to the Pull Request workflow (which we'll cover later), allowing for thorough code review before changes are integrated into the main codebase.

## Key Branching Commands

### `git branch`

This command is used to list, create, or delete branches.

*   **List all local branches:**

    ```bash
git branch
    ```
    The branch you are currently on (your `HEAD`) will be highlighted (e.g., with an asterisk `*` and often in a different color).

*   **List all local and remote branches:**

    ```bash
git branch -a
    ```

*   **Create a new branch:**

    ```bash
git branch <new-branch-name>
    ```
    This command creates a new branch pointer, but you remain on your current branch. The new branch will point to the same commit as your current branch.

*   **Delete a branch:**

    ```bash
git branch -d <branch-to-delete>
    ```
    This command safely deletes a branch. Git will prevent deletion if the branch contains unmerged changes, ensuring you don't lose work. You also cannot delete the branch you are currently on.

*   **Force delete a branch:**

    ```bash
git branch -D <branch-to-delete>
    ```
    Use `-D` (uppercase) to force delete a branch, even if it contains unmerged changes. **Use with extreme caution**, as this can lead to data loss if you haven't backed up or merged the changes elsewhere.

### `git checkout` (Traditional Branch Switching)

Historically, `git checkout` was the primary command for switching between branches, restoring files, and more. While still widely used, Git 2.23 introduced `git switch` and `git restore` to provide more focused commands.

*   **Switch to an existing branch:**

    ```bash
git checkout <branch-name>
    ```
    This command moves your `HEAD` pointer to the specified branch, updating your working directory to reflect the state of that branch.

*   **Create and switch to a new branch (shortcut):**

    ```bash
git checkout -b <new-branch-name>
    ```
    This is a very common and convenient command. It's equivalent to running `git branch <new-branch-name>` followed by `git checkout <new-branch-name>`.

### `git switch` (Modern Branch Switching)

Introduced in Git 2.23, `git switch` is a more intuitive and safer command specifically designed for switching branches. It separates the concerns of branch switching from file restoration (`git restore`).

*   **Switch to an existing branch:**

    ```bash
git switch <branch-name>
    ```

*   **Create and switch to a new branch:**

    ```bash
git switch -c <new-branch-name>
    ```

    Using `git switch` is generally recommended for branch operations as it provides clearer intent and better error messages than `git checkout`.

## Branching Workflow Example

Let's walk through a common branching scenario to illustrate the process:

1.  **Start on `main`:** Always ensure you are on the `main` branch and it's up-to-date before starting new work.

    ```bash
git checkout main
# Or git switch main
git pull origin main # Ensure your local main is in sync with remote
    ```

2.  **Create a new feature branch:** Let's say you want to add a new user authentication feature.

    ```bash
git switch -c feature/add-user-auth
# Or git checkout -b feature/add-user-auth
    ```
    You are now on the `feature/add-user-auth` branch. Your working directory reflects the state of `main` at the time you created the branch.

3.  **Make changes and commit them:** Work on your feature. Create new files, modify existing ones, and make regular, atomic commits.

    ```bash
# Create a new file for authentication logic
echo "// User authentication logic" > src/auth.js

# Modify an existing file (e.g., add a call to auth.js)
echo "import { authenticateUser } from './auth.js';" >> src/app.js

git add src/auth.js src/app.js
git commit -m "feat: Implement basic user authentication module"
    ```

4.  **Continue working and committing on the feature branch:** You can make multiple commits on this branch as you develop the feature.

    ```bash
echo "// Add login function" >> src/auth.js
git add src/auth.js
git commit -m "feat: Add login function to auth module"
    ```

5.  **Switch back to `main` (optional, for context):** You can switch back to `main` to see that your changes on `feature/add-user-auth` are *not* present here. The `main` branch remains stable.

    ```bash
git switch main
    ```

6.  **Switch back to your feature branch:** To continue development on your feature.

    ```bash
git switch feature/add-user-auth
    ```

This independent development is the core power of branching. Once your feature is complete and thoroughly tested on its dedicated branch, the next step is to integrate it back into the `main` branch, which we'll cover in the next section: merging and resolving conflicts.

---

Now that you understand how to create and switch between branches, let's learn how to bring those changes together using `git merge` and how to handle conflicts.