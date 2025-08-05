# Part 3: Branching & Merging - Merging and Conflicts

After working on a feature or bug fix in a separate branch, you'll eventually want to integrate those changes back into your main codebase, typically the `main` branch. This process is called **merging**.

## What is Merging?

Merging in Git is the process of combining the changes from one branch into another. Git attempts to integrate the changes automatically. The outcome of a merge depends on the history of the branches involved.

### Fast-Forward Merge

A fast-forward merge occurs when the branch you are merging from is a direct descendant of the branch you are merging into. This means there have been no new commits on the target branch since the source branch diverged. Git doesn't create a new merge commit; instead, it simply moves the pointer of the target branch forward to the latest commit of the source branch. This results in a linear history.

```
main: A -- B
             \
feature:      C -- D

# After fast-forward merge of feature into main:
main: A -- B -- C -- D
```

### Three-Way Merge (or Recursive Merge)

This is the most common type of merge and occurs when the branches have diverged, meaning there are new commits on both the source and target branches since they last shared a common ancestor. Git identifies a common ancestor commit and then combines the changes from both branches, creating a new "merge commit" that has two parent commits (the tips of the merged branches). This preserves the history of both branches, showing exactly when and where the merge happened.

```
main: A -- B -- E
             \
feature:      C -- D

# After three-way merge of feature into main:
main: A -- B -- E -- F (Merge Commit)
             \
feature:      C -- D /
```

## Key Merging Command

### `git merge <branch-to-merge>`

To merge changes from one branch into your current branch, you first need to switch to the branch you want to merge *into* (this is your target branch).

**Example:** Merging `feature/add-user-auth` into `main`.

1.  **Switch to the target branch (e.g., `main`):**

    ```bash
git switch main
# Or git checkout main
    ```

2.  **Merge the feature branch:**

    ```bash
git merge feature/add-user-auth
    ```

    Git will then attempt to combine the histories. If successful, you'll see a message indicating the merge type (e.g., "Fast-forward" or "Merge made by the 'recursive' strategy.").

## Merge Conflicts

Merge conflicts occur when Git cannot automatically reconcile differing changes in the same part of a file across two branches. This typically happens when:

*   Both branches modify the same lines in the same file.
*   One branch deletes a file that the other branch modified.
*   One branch renames a file while the other modifies its content.

When a conflict occurs, Git will pause the merge process and tell you which files have conflicts. It will mark the conflicting sections within the files, and the merge will be in a "conflicted" state.

### Resolving Merge Conflicts

1.  **Identify Conflicted Files:** After a merge conflict, `git status` will show files that are "unmerged" (or "both modified").

    ```bash
git status
    ```

2.  **Open and Edit Files:** Open each conflicted file in your text editor. Git inserts special markers into the conflicted files to show you the different versions:

    ```
<<<<<<< HEAD
This is the content from the current branch (your HEAD, e.g., main).
=======
This is the content from the branch you are merging (e.g., feature/add-user-auth).
>>>>>>> feature/add-user-auth
    ```

    *   `<<<<<<< HEAD`: Marks the beginning of the changes from your current branch.
    *   `=======`: Separates the content from the two branches.
    *   `>>>>>>> <branch-name>`: Marks the end of the changes from the incoming branch.

3.  **Manually Resolve:** Carefully edit the file to resolve the conflict. You need to decide which changes to keep, combine them, or write new code. **Crucially, you must remove all Git conflict markers** (`<<<<<<<`, `=======`, `>>>>>>>`) from the file.

4.  **Add the Resolved File to the Staging Area:** After resolving conflicts in a file, use `git add <filename>` to stage the changes and tell Git that you've handled the conflict for that file.

    ```bash
git add <conflicted-file-name>
    ```

5.  **Commit the Merge:** Once all conflicts are resolved and staged, complete the merge by committing. Git will often pre-populate a merge commit message for you, which you can accept or modify. This commit finalizes the merge.

    ```bash
git commit -m "Merge branch 'feature/add-user-auth' into main"
    ```

### Aborting a Merge

If you encounter merge conflicts and decide you don't want to proceed with the merge, you can abort the operation and return your repository to its state before the merge attempt.

```bash
git merge --abort
```
This command will clean up the working directory and reset the HEAD to the state before the merge was started.

## Best Practices for Merging

*   **Pull Frequently:** Before starting new work or merging, always `git pull` on your `main` branch to ensure it's up-to-date with the remote. This minimizes the chances of large, complex conflicts.
*   **Keep Branches Small and Focused:** Work on small, isolated features or bug fixes in dedicated branches. This reduces the scope of changes and makes merge conflicts easier to resolve.
*   **Communicate with Your Team:** In a collaborative environment, communicate with your teammates about what you're working on to avoid simultaneous changes to the same code sections.
*   **Understand Merge Strategies:** Be aware of fast-forward vs. three-way merges. While fast-forward merges create a linear history, three-way merges explicitly record the merge event, which can be beneficial for understanding project history.
*   **Use a Merge Tool:** For complex conflicts, consider configuring a graphical merge tool (e.g., KDiff3, Meld, VS Code's built-in merge editor). You can launch it with `git mergetool`.

---

With branching and merging, you have the core tools for collaborative development. Next, we'll put this into practice with the standard GitHub workflow: Pull Requests.
