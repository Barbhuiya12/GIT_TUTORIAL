# Part 5: Advanced Topics - Advanced Git Commands

Git offers a rich set of commands that go beyond the basics, allowing for more precise control over your repository's history and workflow. Mastering these advanced commands can significantly enhance your productivity and ability to manage complex scenarios.

## 1. `git rebase` (Rewriting History)

`git rebase` is a powerful command that allows you to rewrite commit history. While `git merge` combines two branches by creating a new merge commit, `git rebase` moves or reapplies a sequence of commits from one branch onto another base commit. This can result in a cleaner, linear history, avoiding the extra merge commits that `git merge` creates.

**When to use `rebase`:**
*   **To keep your feature branch up-to-date with `main`:** Instead of merging `main` into your feature branch (which creates merge commits), you can rebase your feature branch onto `main`. This makes it appear as if you started your feature branch from the latest `main`.
*   **To clean up your commit history before merging:** You can use interactive rebase to combine small, incremental commits into larger, more meaningful ones, reword commit messages, or even remove commits before pushing to a shared remote.

**Caution: Never rebase commits that have already been pushed to a shared remote repository.** Rebasing rewrites history, meaning the commit IDs change. If others have already pulled those commits, rebasing and then pushing will cause conflicts and confusion for your collaborators. Rebase only on local, unpushed branches.

### Interactive Rebase (`git rebase -i`)

Interactive rebase (`-i`) is particularly useful for cleaning up your local commit history before pushing to a remote. It allows you to modify individual commits in a series.

```bash
git rebase -i HEAD~<number-of-commits>
# Example: Rebase the last 3 commits you made
git rebase -i HEAD~3

# Or rebase a feature branch onto main:
git rebase -i main feature/my-feature
```

This command will open an editor (your default Git editor) with a list of your recent commits and a set of commands you can use:

*   `pick` (p): Use the commit as is. This is the default.
*   `reword` (r): Use the commit, but edit the commit message.
*   `edit` (e): Use the commit, but stop to amend the commit (e.g., add more changes, split a commit).
*   `squash` (s): Combine this commit with the previous one. The commit message of the previous commit will be used, and you'll be prompted to edit it to include the squashed commit's message.
*   `fixup` (f): Like `squash`, but discard this commit's log message. Only the previous commit's message is kept.
*   `drop` (d): Remove the commit entirely.
*   `exec` (x): Run a shell command on each commit.

**Interactive Rebase Workflow:**
1.  Run `git rebase -i <base-commit-or-branch>` (e.g., `HEAD~3` or `main`).
2.  The editor opens. Modify the commands next to each commit as desired.
3.  Save and close the editor.
4.  Git will apply the changes. If conflicts occur, resolve them, `git add` the files, and then `git rebase --continue`. If you want to stop, use `git rebase --abort`.

## 2. `git stash` (Temporarily Saving Changes)

Sometimes, you're working on something, and suddenly you need to switch branches to fix an urgent bug or work on something else, but your current changes aren't ready to be committed. `git stash` temporarily saves your uncommitted changes (both staged and unstaged) and reverts your working directory to the last `HEAD` commit. It's like putting your changes on a temporary shelf.

*   **Stash your changes:**

    ```bash
git stash save "Work in progress: feature X"
# Or simply, to stash all changes (tracked and untracked, but not ignored):
git stash

# To include untracked files:
git stash -u

# To include ignored files as well:
git stash -a
    ```

*   **List stashes:**

    ```bash
git stash list
    ```
    This shows a list of your stashed changes, typically indexed as `stash@{0}`, `stash@{1}`, etc.

*   **Apply a stash:**

    ```bash
git stash apply stash@{0}
# Or apply the most recent stash and keep it in the stash list:
git stash apply
    ```
    `apply` will reapply the changes but keep the stash in your list.

*   **Apply and drop a stash:**

    ```bash
git stash pop
    ```
    `pop` will reapply the changes and then remove the stash from your list.

*   **Show stash contents:**

    ```bash
git stash show -p stash@{0}
    ```

*   **Clear all stashes:**

    ```bash
git stash clear
    ```

## 3. `git cherry-pick` (Applying Specific Commits)

`git cherry-pick` allows you to apply the changes introduced by some existing commits from one branch onto another branch. This is useful if you only need a specific commit (e.g., a hotfix) from another branch, rather than merging the entire branch.

```bash
# First, find the commit hash you want to cherry-pick (e.g., from git log)
git log --oneline

# Then, switch to the branch where you want to apply the commit
git switch <target-branch>

# Finally, cherry-pick the commit
git cherry-pick <commit-hash>
# Example:
git cherry-pick a1b2c3d4
```

If conflicts occur during a cherry-pick, resolve them, `git add` the files, and then `git cherry-pick --continue`. You can abort with `git cherry-pick --abort`.

## 4. `git reflog` (Your Safety Net)

`git reflog` (reference log) is an incredibly powerful command and your ultimate safety net in Git. It records every change to `HEAD` and other references in your local repository. This means if you accidentally delete a branch, reset to the wrong commit, mess up a rebase, or lose commits in any way, `reflog` can help you find the commit you were on and recover your work.

```bash
git reflog
```

This will show a history of where your `HEAD` has been, including operations like commits, merges, rebases, and resets. Each entry has an index (e.g., `HEAD@{0}`, `HEAD@{1}`).

To recover a lost state:

```bash
git reset --hard HEAD@{<index>}
# Example: To go back to the state before your last rebase
git reset --hard HEAD@{1}
```

**Important:** `reflog` entries are local to your repository and are eventually pruned. Don't rely on it for long-term backups.

## 5. `git tag` (Marking Important Points)

`git tag` is used to mark specific points in a repository's history as important. Typically, this is used to mark release points (e.g., `v1.0.0`, `v2.0-beta`), but can be used for any significant milestone.

*   **List tags:**

    ```bash
git tag
# To list tags with their messages:
git tag -n
    ```

*   **Create a lightweight tag:** (Just a pointer to a commit, no extra information)

    ```bash
git tag v1.0.0
    ```

*   **Create an annotated tag:** (Recommended; stores tagger name, email, date, and a message, and can be signed with GPG)

    ```bash
git tag -a v1.0.0 -m "Release version 1.0.0 - Initial stable release"
    ```

*   **Push tags to remote:** Tags are not pushed to the remote by default. You need to explicitly push them.

    ```bash
git push origin --tags
# To push a specific tag:
git push origin v1.0.0
    ```

*   **Delete a tag:**

    ```bash
git tag -d v1.0.0 # Delete local tag
git push origin --delete v1.0.0 # Delete remote tag
    ```

---

These advanced commands provide greater flexibility and control over your Git workflow, allowing you to manage your project's history more effectively. Next, we'll explore some key features offered by GitHub beyond just hosting your code.