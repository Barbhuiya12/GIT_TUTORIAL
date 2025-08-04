# Part 5: Advanced Topics - Advanced Git Commands

Git offers a rich set of commands that go beyond the basics, allowing for more precise control over your repository's history and workflow. This section introduces some powerful advanced commands.

## 1. `git rebase` (Interactive)

`git rebase` is a powerful command that allows you to rewrite commit history. While `git merge` combines two branches by creating a new merge commit, `git rebase` moves or combines a sequence of commits to a new base commit. This can result in a cleaner, linear history.

**When to use `rebase`:**
*   To keep your feature branch up-to-date with `main` without creating merge commits.
*   To clean up your commit history before merging into `main` (e.g., combining small commits into larger, more meaningful ones).

**Caution:** Never rebase commits that have already been pushed to a shared remote repository, as it rewrites history and can cause issues for collaborators.

### Interactive Rebase (`git rebase -i`)

Interactive rebase is particularly useful for cleaning up your local commit history before pushing to a remote.

```bash
git rebase -i HEAD~<number-of-commits>
# Example: Rebase the last 3 commits
git rebase -i HEAD~3
```

This command will open an editor with a list of your recent commits and a set of commands you can use:

*   `pick`: Use the commit as is.
*   `reword`: Use the commit, but edit the commit message.
*   `edit`: Use the commit, but stop to amend the commit (e.g., add more changes).
*   `squash`: Combine this commit with the previous one.
*   `fixup`: Like `squash`, but discard this commit's log message.
*   `drop`: Remove the commit.

**Workflow:**
1.  Run `git rebase -i HEAD~N`.
2.  Modify the commands next to each commit in the editor.
3.  Save and close the editor.
4.  Git will apply the changes. If conflicts occur, resolve them, `git add` the files, and then `git rebase --continue`.

## 2. `git stash`

Sometimes, you're working on something, and suddenly you need to switch branches to fix a bug or work on something urgent, but your current changes aren't ready to be committed. `git stash` temporarily saves your uncommitted changes (both staged and unstaged) and reverts your working directory to the last `HEAD` commit.

*   **Stash your changes:**

    ```bash
git stash save "Work in progress: feature X"
# Or simply:
git stash
    ```

*   **List stashes:**

    ```bash
git stash list
    ```

*   **Apply a stash:**

    ```bash
git stash apply stash@{0}
# Or apply the most recent stash and keep it in the stash list:
git stash apply
    ```

*   **Apply and drop a stash:**

    ```bash
git stash pop
    ```

*   **Clear all stashes:**

    ```bash
git stash clear
    ```

## 3. `git cherry-pick`

`git cherry-pick` allows you to apply the changes introduced by some existing commits from one branch onto another branch. This is useful if you only need a specific commit from another branch, rather than merging the entire branch.

```bash
git cherry-pick <commit-hash>
# Example:
git cherry-pick a1b2c3d4
```

If conflicts occur, resolve them, `git add` the files, and then `git cherry-pick --continue`.

## 4. `git reflog`

`git reflog` (reference log) is your safety net! It records every change to `HEAD` and other references in your local repository. This means if you accidentally delete a branch, reset to the wrong commit, or mess up a rebase, `reflog` can help you find the commit you were on and recover your work.

```bash
git reflog
```

This will show a history of where your `HEAD` has been. You can then use `git reset --hard <reflog-entry>` to go back to a specific state.

## 5. `git tag`

`git tag` is used to mark specific points in a repository's history as important. Typically, this is used to mark release points (e.g., `v1.0`, `v2.0-beta`).

*   **List tags:**

    ```bash
git tag
    ```

*   **Create a lightweight tag:** (Just a pointer to a commit)

    ```bash
git tag v1.0.0
    ```

*   **Create an annotated tag:** (Recommended; stores tagger name, email, date, and message)

    ```bash
git tag -a v1.0.0 -m "Release version 1.0.0"
    ```

*   **Push tags to remote:** Tags are not pushed by default.

    ```bash
git push origin --tags
    ```

---

These advanced commands provide greater flexibility and control over your Git workflow. Next, we'll explore some key features offered by GitHub beyond just hosting your code.