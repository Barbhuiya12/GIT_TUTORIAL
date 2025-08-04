# Part 3: Branching & Merging - Merging and Conflicts

After working on a feature or bug fix in a separate branch, you'll eventually want to integrate those changes back into your main codebase, typically the `main` branch. This process is called **merging**.

## What is Merging?

Merging in Git is the process of combining the changes from one branch into another. Git attempts to integrate the changes automatically. If there are no conflicting changes (i.e., different changes to the same lines of code in both branches), Git performs a fast-forward merge or a three-way merge automatically.

## Key Merging Command

### `git merge <branch-to-merge>`

To merge changes from one branch into your current branch, you first need to switch to the branch you want to merge *into*.

**Example:** Merging `feature/add-user-auth` into `main`.

1.  **Switch to the target branch (e.g., `main`):**

    ```bash
git checkout main
    ```

2.  **Merge the feature branch:**

    ```bash
git merge feature/add-user-auth
    ```

    Git will then attempt to combine the histories. If successful, you'll see a message indicating the merge type (e.g., "Fast-forward" or "Merge made by the 'recursive' strategy.").

## Merge Conflicts

Merge conflicts occur when Git cannot automatically reconcile changes between two branches. This typically happens when:

*   Two branches modify the same lines in the same file.
*   One branch deletes a file that the other branch modified.

When a conflict occurs, Git will pause the merge process and tell you which files have conflicts. It will mark the conflicting sections within the files.

### Resolving Merge Conflicts

1.  **Identify conflicted files:** After a merge conflict, `git status` will show files that are "unmerged."

    ```bash
git status
    ```

2.  **Open the conflicted file(s):** Git inserts special markers into the conflicted files to show you the different versions.

    ```
    <<<<<<< HEAD
    This is the content from the current branch (e.g., main).
    =======
    This is the content from the branch you are merging (e.g., feature/add-user-auth).
    >>>>>>> feature/add-user-auth
    ```

    *   `<<<<<<< HEAD`: Marks the beginning of the conflict and the content from your current branch (`HEAD`).
    *   `=======`: Separates the content from the two branches.
    *   `>>>>>>> <branch-name>`: Marks the end of the conflict and the content from the branch you are merging.

3.  **Manually edit the file:** You need to manually edit the file to resolve the conflict. Decide which changes to keep, combine them, or discard them. **Remove all Git conflict markers** (`<<<<<<<`, `=======`, `>>>>>>>`).

4.  **Add the resolved file to the staging area:** After resolving the conflict, tell Git that you've handled it.

    ```bash
git add <conflicted-file-name>
    ```

5.  **Commit the merge:** Once all conflicts are resolved and staged, complete the merge by committing.

    ```bash
git commit -m "Merge branch 'feature/add-user-auth' into main"
    ```
    Git will often pre-populate a merge commit message for you, which you can accept or modify.

## Best Practices for Merging

*   **Pull frequently:** Before starting new work or merging, always `git pull` on your `main` branch to ensure it's up-to-date.
*   **Keep branches small:** Work on small, focused features in branches. This reduces the likelihood and complexity of merge conflicts.
*   **Communicate:** If working in a team, communicate with your teammates about what you're working on to avoid simultaneous changes to the same code.

---

With branching and merging, you have the core tools for collaborative development. Next, we'll put this into practice with the standard GitHub workflow: Pull Requests.