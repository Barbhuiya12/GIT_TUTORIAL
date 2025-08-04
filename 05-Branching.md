# Part 3: Branching & Merging - Understanding Branches

One of Git's most powerful features is its branching model. Branches allow you to diverge from the main line of development and continue to work independently without affecting the main codebase. This is essential for teamwork, feature development, and bug fixes.

## What are Branches?

Think of a branch as a separate line of development. When you create a branch, you're essentially creating a new, independent version of your project. You can make changes, commit them to this branch, and those changes won't affect other branches until you explicitly merge them.

By default, when you initialize a Git repository, you are on the `main` (or `master`) branch. This is typically considered the stable, production-ready version of your project.

## Why Use Branches?

*   **Feature Development:** Work on new features in isolation without breaking the main codebase.
*   **Bug Fixes:** Quickly fix bugs on a separate branch and then merge the fix back.
*   **Experimentation:** Try out new ideas or approaches without fear of messing up the stable version.
*   **Collaboration:** Multiple developers can work on different features simultaneously on their own branches.

## Key Branching Commands

### `git branch`

This command allows you to list, create, or delete branches.

*   **List all branches:**

    ```bash
git branch
    ```
    The branch you are currently on will be highlighted (e.g., with an asterisk).

*   **Create a new branch:**

    ```bash
git branch <new-branch-name>
    ```
    This creates a new branch, but you remain on your current branch.

*   **Delete a branch:**

    ```bash
git branch -d <branch-to-delete>
    ```
    You can only delete a branch if you are not currently on it and if its changes have been merged into its upstream branch. Use `-D` (force delete) to delete an unmerged branch (use with caution!).

### `git checkout`

This command is used to switch between branches or restore files.

*   **Switch to an existing branch:**

    ```bash
git checkout <branch-name>
    ```

*   **Create and switch to a new branch (shortcut):**

    ```bash
git checkout -b <new-branch-name>
    ```
    This is a very common command, combining `git branch <new-branch-name>` and `git checkout <new-branch-name>`.

### `git switch` (Modern Alternative to `git checkout` for branches)

Git 2.23 introduced `git switch` as a more intuitive command specifically for switching branches, separating its functionality from `git restore` (for restoring files).

*   **Switch to an existing branch:**

    ```bash
git switch <branch-name>
    ```

*   **Create and switch to a new branch:**

    ```bash
git switch -c <new-branch-name>
    ```

## Branching Workflow Example

Let's walk through a common branching scenario:

1.  **Start on `main`:** Ensure you are on the `main` branch.

    ```bash
git checkout main
    ```

2.  **Create a new feature branch:** Let's say you want to add a new feature.

    ```bash
git checkout -b feature/add-user-auth
    ```
    You are now on the `feature/add-user-auth` branch.

3.  **Make changes and commit:** Work on your feature, add new files, modify existing ones.

    ```bash
# Make some changes to your files
echo "User authentication logic" > auth.js
git add auth.js
git commit -m "feat: Implement basic user authentication"
    ```

4.  **Switch back to `main` (optional):** You can switch back to `main` to see that your changes on `feature/add-user-auth` are not present here.

    ```bash
git checkout main
    ```

5.  **Continue working on the feature:** Switch back to your feature branch to continue development.

    ```bash
git checkout feature/add-user-auth
    ```

This independent development is the power of branching. Once your feature is complete, the next step is to integrate it back into the `main` branch, which we'll cover in the next section: merging and resolving conflicts.

---

Now that you understand how to create and switch between branches, let's learn how to bring those changes together using `git merge` and how to handle conflicts.