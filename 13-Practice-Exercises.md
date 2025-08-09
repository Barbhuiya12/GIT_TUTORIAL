# Git Practice Exercises

This file contains practical exercises to help you reinforce your Git skills. Work through these exercises sequentially to build your confidence and proficiency with Git.

## Exercise 1: Basic Git Workflow

**Objective:** Practice the basic Git workflow of initializing a repository, making changes, and committing them.

1. Create a new directory called `git-practice`
2. Initialize a Git repository in this directory
3. Create a file called `README.md` with the content "# My Practice Project"
4. Add the file to the staging area
5. Commit the file with an appropriate message
6. Modify the `README.md` file to add a second line "This is a practice repository for learning Git."
7. Stage and commit this change
8. View your commit history to verify both commits

**Bonus:** Try using different `git log` options to view your history in different formats.

## Exercise 2: Working with Branches

**Objective:** Practice creating, switching between, and merging branches.

1. Create a new branch called `feature/about-page`
2. Switch to this branch
3. Create a file called `about.md` with some content about yourself
4. Commit this file
5. Switch back to the `main` branch
6. Verify that `about.md` is not present in the `main` branch
7. Merge the `feature/about-page` branch into `main`
8. Verify that `about.md` is now present
9. Delete the `feature/about-page` branch

## Exercise 3: Handling Merge Conflicts

**Objective:** Practice resolving merge conflicts.

1. Create a new branch called `feature/update-readme`
2. In this branch, modify the first line of `README.md` to "# My Awesome Practice Project"
3. Commit this change
4. Switch back to the `main` branch
5. In the `main` branch, modify the first line of `README.md` to "# My Git Practice Project"
6. Commit this change
7. Try to merge `feature/update-readme` into `main`
8. Resolve the merge conflict by choosing one of the versions or creating a new combined version
9. Commit the resolved file

## Exercise 4: Working with a Remote Repository

**Objective:** Practice connecting a local repository to a remote repository on GitHub.

1. Create a new repository on GitHub (you can make it private for this exercise)
2. Follow the instructions to connect your local `git-practice` repository to the remote repository
3. Push your commits to the remote repository
4. Verify on GitHub that your files and commit history are present
5. Make a change directly on GitHub (edit the README file using the GitHub web interface)
6. Pull the changes to your local repository

## Exercise 5: Using .gitignore

**Objective:** Practice using `.gitignore` to exclude files from tracking.

1. Create a file called `.gitignore` in your repository
2. Add patterns to ignore:
   - All `.log` files
   - A directory called `temp/`
   - A specific file called `secret.txt`
3. Create these files and directories to test:
   - A file called `debug.log`
   - A directory called `temp` with a file inside it
   - A file called `secret.txt` with some content
   - A file called `important.txt` (this should NOT be ignored)
4. Use `git status` to verify that only `important.txt` shows up as an untracked file
5. Commit `important.txt` and `.gitignore`
6. Verify that the ignored files are not tracked by Git

## Exercise 6: Advanced Git Features

**Objective:** Practice using advanced Git features like stashing and amending commits.

1. Start making changes to your `README.md` file but don't commit them yet
2. Stash these changes
3. Create and switch to a new branch
4. Make a small change and commit it
5. Switch back to the main branch
6. Apply your stashed changes
7. Make a commit with a typo in the commit message
8. Use `git commit --amend` to fix the typo in the commit message

## Exercise 7: Collaborative Workflow

**Objective:** Practice the collaborative workflow using feature branches and pull requests.

1. Create a new branch for a feature (e.g., `feature/contact-page`)
2. Add a contact page file
3. Commit your changes
4. Push the branch to GitHub
5. Create a pull request on GitHub
6. (If possible) Have someone review your pull request
7. Make an additional commit to address feedback
8. Merge the pull request
9. Pull the changes to your local main branch

## Solutions

For the first exercise, here's a sample solution:

```bash
# 1. Create a new directory
mkdir git-practice
cd git-practice

# 2. Initialize a Git repository
git init

# 3. Create README.md
echo "# My Practice Project" > README.md

# 4. Add to staging area
git add README.md

# 5. Commit the file
git commit -m "Initial commit with README"

# 6. Modify README.md
echo "This is a practice repository for learning Git." >> README.md

# 7. Stage and commit
git add README.md
git commit -m "Add description to README"

# 8. View commit history
git log --oneline
```

Try to work through the other exercises on your own before checking solutions online or asking for help. The goal is to build muscle memory and understanding through practice.

## Additional Practice Ideas

1. **Fork and contribute to an open-source project** - Find a small open-source project on GitHub and look for issues labeled "good first issue" or "beginner friendly."

2. **Use Git for a personal project** - Start using Git for all your personal coding projects, even small ones.

3. **Experiment with Git GUI tools** - Try using GitHub Desktop, GitKraken, or the Git integration in your IDE.

4. **Practice Git commands daily** - Use a different Git command each day to build familiarity.

Remember, becoming proficient with Git takes time and practice. Don't worry if you make mistakes - Git is designed to make it difficult to truly lose work, and mistakes are part of the learning process.
