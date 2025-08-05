# Part 1: The Basics - First Steps with Git

Now that you understand what Git is, it's time to take your first steps. This involves configuring Git and learning the basic workflow of saving changes.

## 1. Configuring Git

Before you start using Git, you need to tell it who you are. This information is attached to every commit you make. Git uses this information to identify the author of each commit.

There are different levels at which you can configure Git:

*   **System-level:** Applies to all users on your computer and all their repositories. (e.g., `/etc/gitconfig`)
*   **Global-level (`--global`):** Applies to your user account across all your repositories. This is the most common setting for `user.name` and `user.email`. (e.g., `~/.gitconfig` or `~/.config/git/config`)
*   **Local-level:** Applies only to the current repository. This setting overrides global and system settings for that specific repository. (e.g., `.git/config` inside your repository)

For personal use, setting your name and email globally is usually sufficient. Open your terminal and run the following commands, replacing the placeholder text with your name and email address. **Important:** Use the same email address you use for your GitHub account if you plan to push your code there.

```bash
# Set your username globally
git config --global user.name "Your Name"

# Set your email address globally
git config --global user.email "youremail@example.com"
```

To verify your settings, you can use:

```bash
git config --global user.name
git config --global user.email
```

## 2. The Basic Git Workflow: The Three States

Git manages your project files in three main states or areas. Understanding these states is fundamental to using Git effectively:

1.  **Working Directory (or Working Tree):** This is your local project folder where you create, edit, and delete files. These are the files you see and interact with directly on your file system.

2.  **Staging Area (or Index):** This is an intermediate area where you prepare the changes you want to include in your next commit. When you `git add` files, you're taking a snapshot of their current state and placing it in the staging area. This allows you to be selective about which changes (or even parts of changes) you want to commit, giving you fine-grained control over your commit history.

3.  **Local Repository (.git directory):** This is where Git permanently stores all your project's history. When you `git commit`, the snapshot from the staging area is saved as a new, permanent record in your local repository. Each commit is a complete snapshot of your project at a specific point in time, along with metadata like author, date, and a commit message.

**The Workflow Cycle:**

*   You **Modify** files in your **Working Directory**.
*   You **Stage** the desired changes from your Working Directory to the **Staging Area** using `git add`.
*   You **Commit** the staged changes from the Staging Area to your **Local Repository** using `git commit`.

## 3. Key Git Commands for Basic Workflow

Let's explore the essential commands you'll use daily:

*   `git status`: This is your most-used command. It shows the current state of your working directory and staging area, letting you see:
    *   **Untracked files:** New files that Git hasn't started tracking yet.
    *   **Changes not staged for commit (Modified):** Files that Git is tracking, but you've made changes to them that haven't been added to the staging area.
    *   **Changes to be committed (Staged):** Changes that have been added to the staging area and are ready for the next commit.

*   `git add <file>`: This command takes a snapshot of a file in its current version and adds it to the staging area. You can specify individual files or use patterns:
    *   `git add .`: Stages all new (untracked) and modified files in the current directory and its subdirectories. (Does not stage deletions).
    *   `git add -u` (or `--update`): Stages changes only for files that are *already tracked* by Git. This includes modifications and deletions of tracked files, but *not* new untracked files.
    *   `git add -A` (or `--all`): Stages *all* changes (new, modified, and deleted files) in the entire working tree. This is often the most convenient for staging everything.

*   `git commit -m "Your descriptive message"`: This takes everything from the staging area and saves it as a new snapshot (a "commit") in your repository. The message (`-m`) is crucial—it should clearly describe the changes you made.

    **Best Practices for Commit Messages:**
    *   **Subject Line (first line):**
        *   Keep it concise (50-72 characters recommended).
        *   Use the imperative mood (e.g., "Fix bug," "Add feature," not "Fixed bug" or "Adds feature").
        *   Capitalize the first letter and do not end with a period.
    *   **Body (optional, after a blank line):**
        *   Provide a more detailed explanation of *what* was changed and *why*. Explain the problem solved or the feature added.
        *   Wrap lines at around 72 characters.
        *   Reference any related issues or tickets.

*   `git log`: This command shows a log of all the commits you have made, with the most recent commit first. Useful options include:
    *   `git log --oneline`: Shows each commit on a single line (abbreviated hash and message).
    *   `git log --graph`: Draws an ASCII graph of your branch and merge history.
    *   `git log --all`: Shows the history of all branches, not just the current one.
    *   Combine them: `git log --oneline --graph --all` provides a powerful visual overview.

## 4. Let's Try It! (Hands-on Example)

Let's put these commands into practice. Make sure you are in your `git_tutorial` directory.

1.  **Create a new file:**

    ```bash
    # Create a new file named hello.txt with some text
    echo "Hello, Git World!" > hello.txt
    ```

2.  **Check the status (before staging):**

    ```bash
    git status
    ```

    You will see `hello.txt` listed as an "untracked file."

3.  **Stage the new file:**

    ```bash
    git add hello.txt
    ```

4.  **Check the status again (after staging):**

    ```bash
    git status
    ```

    Now Git will show that `hello.txt` is "new file: hello.txt" under "Changes to be committed."

5.  **Commit the file:**

    ```bash
    git commit -m "feat: Add initial hello.txt file"
    ```

6.  **Modify the file:**

    ```bash
    echo "Adding a second line." >> hello.txt
    ```

7.  **Check the status (after modification):**

    ```bash
    git status
    ```

    You will see `hello.txt` listed under "Changes not staged for commit" (modified).

8.  **Stage the modified file:**

    ```bash
    git add hello.txt
    ```

9.  **Check the status again (modified and staged):**

    ```bash
    git status
    ```

    Now `hello.txt` is back under "Changes to be committed."

10. **Commit the modification:**

    ```bash
    git commit -m "refactor: Add second line to hello.txt"
    ```

11. **View the history:**

    ```bash
    git log --oneline
    ```

    You will see both of your commits, complete with their abbreviated hashes and messages.

---

Congratulations, you've successfully navigated the basic Git workflow! Next, we'll learn how to connect our local repository to a remote one on GitHub.