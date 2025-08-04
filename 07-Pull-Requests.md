# Part 4: The GitHub Workflow - Pull Requests

Now that you understand branching and merging, it's time to introduce the **Pull Request (PR)**, a cornerstone of collaborative development on GitHub (and similar platforms like GitLab or Bitbucket).

## What is a Pull Request?

A Pull Request is a mechanism for a developer to notify team members that they have completed a feature or bug fix and want to merge their changes from a feature branch into a target branch (e.g., `main`). It's not just a request to pull code; it's a **discussion forum** for code review.

When you open a Pull Request, you're essentially saying:

*   "Here are the changes I've made."
*   "Please review them."
*   "If they look good, please pull them into the main codebase."

## The Pull Request Workflow

Here's a typical workflow for contributing changes via a Pull Request:

1.  **Ensure your `main` branch is up-to-date:** Before starting any new work, always pull the latest changes from the remote `main` branch to your local `main` branch.

    ```bash
git checkout main
git pull origin main
    ```

2.  **Create a new feature branch:** Create a new branch for your specific feature or bug fix. Give it a descriptive name (e.g., `feature/new-dashboard`, `bugfix/login-issue`).

    ```bash
git checkout -b feature/new-feature
    ```

3.  **Make your changes and commit them:** Work on your feature, making as many commits as necessary on your feature branch.

    ```bash
# Make changes to files
git add .
git commit -m "feat: Implement new feature functionality"
    ```

4.  **Push your feature branch to GitHub:** Once you're ready to propose your changes, push your feature branch to your remote repository on GitHub.

    ```bash
git push -u origin feature/new-feature
    ```
    The `-u` flag sets the upstream, so future pushes from this branch can just be `git push`.

5.  **Open a Pull Request on GitHub:**
    *   Go to your repository on GitHub. You'll usually see a prominent button or banner suggesting you open a Pull Request from your newly pushed branch.
    *   Alternatively, navigate to the "Pull requests" tab and click "New pull request."
    *   **Compare changes:** Select your feature branch as the "compare" branch and the `main` branch as the "base" branch.
    *   **Write a clear title and description:**
        *   **Title:** A concise summary of the changes (e.g., "feat: Add user profile page").
        *   **Description:** Explain *what* the PR does, *why* it was done, and any relevant context (e.g., screenshots, links to issues).
    *   **Assign reviewers, add labels, link issues:** Use GitHub's sidebar options to assign team members for review, categorize your PR with labels, and link it to any relevant issues.
    *   Click "Create pull request."

6.  **Code Review and Discussion:**
    *   Reviewers will examine your code, leave comments, and suggest changes directly on GitHub.
    *   You can respond to comments, push new commits to your feature branch (which automatically update the PR), and address feedback.

7.  **Merge the Pull Request:**
    *   Once the code is reviewed, approved, and all checks (like automated tests or linting) pass, a team member (often the original author or a designated maintainer) can merge the Pull Request.
    *   GitHub offers different merge options: "Merge pull request" (creates a merge commit), "Squash and merge" (combines all PR commits into one), or "Rebase and merge" (reapplies commits on top of the base branch).

8.  **Delete the feature branch (optional but recommended):** After merging, GitHub usually offers a button to delete the feature branch. It's good practice to keep your repository clean.

    ```bash
git branch -d feature/new-feature
    ```

## Benefits of Pull Requests

*   **Code Quality:** Ensures code is reviewed by peers, catching bugs and improving design.
*   **Knowledge Sharing:** Team members learn about new features and changes.
*   **Documentation:** The PR description and comments serve as valuable historical context.
*   **Controlled Integration:** Prevents direct pushes to `main`, maintaining a stable codebase.

---

Pull Requests are central to modern collaborative development. Next, we'll explore some advanced Git commands that can help you manage your history and workflow more effectively.