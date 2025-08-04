# Part 1: The Basics - First Steps with Git

Now that you understand what Git is, it's time to take your first steps. This involves configuring Git and learning the basic workflow of saving changes.

## 1. Configuring Git

Before you start using Git, you need to tell it who you are. This information is attached to every commit you make.

Open your terminal and run the following commands, replacing the placeholder text with your name and email address. **Important:** Use the same email address you use for your GitHub account.

```bash
# Set your username
git config --global user.name "Your Name"

# Set your email address
git config --global user.email "youremail@example.com"
```

These settings are stored in a global Git configuration file on your system.

## 2. The Basic Git Workflow

The core Git workflow consists of three main steps:

1.  **Modify** files in your working directory.
2.  **Stage** the files, which adds snapshots of them to your staging area.
3.  **Commit** the changes, which permanently stores the snapshot in your Git repository.

### The Three Areas

*   **Working Directory:** This is your project folder with all its files.
*   **Staging Area (or Index):** This is an intermediate area where you prepare the changes you want to include in your next commit. It allows you to be selective about what you commit.
*   **Repository (.git directory):** This is where Git stores the complete history of your project.

### Key Commands

*   `git status`: This is your most-used command. It shows the current state of your working directory and staging area, letting you see which files are modified, staged, or untracked.

*   `git add <file>`: This command takes a snapshot of a file in its current version and adds it to the staging area. You can also use `git add .` to stage all modified and new files in the current directory.

*   `git commit -m "Your descriptive message"`: This takes everything from the staging area and saves it as a new snapshot (a "commit") in your repository. The message (`-m`) is crucial—it should clearly describe the changes you made.

*   `git log`: This command shows a log of all the commits you have made, with the most recent commit first.

### Let's Try It!

1.  **Create a new file:**

    ```bash
    # Create a new file named file1.txt with some text
    echo "Hello, Git!" > file1.txt
    ```

2.  **Check the status:**

    ```bash
    git status
    ```

    Git will show you that `file1.txt` is an "untracked file."

3.  **Stage the file:**

    ```bash
    git add file1.txt
    ```

4.  **Check the status again:**

    ```bash
    git status
    ```

    Now Git will show that `file1.txt` is staged and ready to be committed.

5.  **Commit the file:**

    ```bash
    git commit -m "Initial commit: Add file1.txt"
    ```

6.  **View the history:**

    ```bash
    git log
    ```

    You will see your first commit, complete with your author information, the date, and the commit message.

---

Congratulations, you've made your first commit! Next, we'll learn how to connect our local repository to a remote one on GitHub.