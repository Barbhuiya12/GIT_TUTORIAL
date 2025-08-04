# Part 2: Going Remote - Connecting to GitHub

Now that you're comfortable with local Git operations, it's time to connect your local repository to a remote one on GitHub. This is where collaboration and online backups come into play.

## 1. Creating a Repository on GitHub

Before you can push your local code to GitHub, you need a place for it to live. Follow these steps to create a new repository on GitHub:

1.  Go to [github.com](https://github.com/) and log in to your account.
2.  Click the `+` sign in the top right corner and select `New repository`.
3.  **Repository name:** Choose a descriptive name (e.g., `my-first-git-repo`).
4.  **Description (optional):** Add a brief description of your project.
5.  **Public or Private:** Choose whether your repository should be publicly accessible or private.
6.  **Initialize this repository with a README:** **DO NOT** check this box if you are pushing an existing local repository. If you check it, GitHub will create a `README.md` file, which can cause merge conflicts when you try to push your local repository.
7.  Click `Create repository`.

After creation, GitHub will show you a page with instructions. Look for the section that says "...or push an existing repository from the command line."

## 2. Connecting Your Local Repository to GitHub

Once your GitHub repository is created, you need to tell your local Git repository where its remote counterpart is.

### `git remote add origin <URL>`

This command adds a new remote connection to your local repository. `origin` is the conventional name for the primary remote repository. The `<URL>` will be the HTTPS or SSH URL provided by GitHub (e.g., `https://github.com/your-username/your-repo-name.git`).

```bash
# Example: Replace with your actual GitHub repository URL
git remote add origin https://github.com/your-username/your-repo-name.git
```

### `git branch -M main` (Optional, but Recommended)

GitHub now defaults to `main` as the primary branch name instead of `master`. If your local branch is still `master`, it's good practice to rename it to `main` to match GitHub's default.

```bash
git branch -M main
```

### `git push -u origin main`

This command pushes your local `main` branch to the `origin` remote repository. The `-u` (or `--set-upstream`) flag sets the `origin/main` as the upstream branch for your local `main` branch. This means that in the future, you can simply use `git push` and `git pull` without specifying `origin main`.

```bash
git push -u origin main
```

After running this, refresh your GitHub repository page, and you should see your files!

## 3. Getting Changes from GitHub: `git pull`

When you're collaborating with others, or even working on the same repository from different machines, you'll need to fetch and integrate changes from the remote repository.

### `git pull`

This command is a combination of `git fetch` (which downloads changes from the remote repository but doesn't integrate them) and `git merge` (which integrates the downloaded changes into your current local branch).

```bash
git pull origin main
# Or, if you set upstream with -u:
git pull
```

It's good practice to `git pull` before you start working each day or before making significant changes, to ensure your local repository is up-to-date.

## 4. Cloning an Existing Repository: `git clone`

If you want to start working on a project that already exists on GitHub, you can clone it.

### `git clone <URL>`

This command downloads a complete copy of a remote Git repository, including all its files and the entire commit history, to your local machine. It also automatically sets up the `origin` remote.

```bash
# Example: Clone a repository
git clone https://github.com/your-username/another-repo.git
```

This will create a new directory with the repository's name in your current location.

---

Now you know how to connect your local Git projects to GitHub and how to get existing projects from GitHub. Next, we'll look at how to tell Git to ignore certain files.