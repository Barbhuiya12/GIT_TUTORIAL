# Part 6: GitHub Features - Beyond Code

GitHub is more than just a place to host your Git repositories. It provides a suite of powerful features that enhance collaboration, automate workflows, and even host websites. This section introduces some of these key features.

## 1. GitHub Issues

GitHub Issues are a fantastic way to track tasks, enhancements, and bugs for your projects. They serve as a centralized place for discussions and progress tracking.

**Key uses:**
*   **Bug Tracking:** Report and manage software defects.
*   **Feature Requests:** Propose and discuss new features.
*   **Task Management:** Break down larger projects into smaller, manageable tasks.
*   **Discussions:** Engage with collaborators and users about project-related topics.

**Features:**
*   **Labels:** Categorize issues (e.g., `bug`, `enhancement`, `documentation`).
*   **Assignees:** Assign issues to specific team members.
*   **Milestones:** Group issues into larger project goals or release cycles.
*   **Projects (Kanban boards):** Visualize and manage issues using Kanban-style boards.
*   **Mentions and References:** Link issues to pull requests or other issues using `#` followed by the issue number.

**How to use:**
1.  Navigate to the "Issues" tab in your GitHub repository.
2.  Click "New issue."
3.  Provide a clear title and detailed description. You can use Markdown for formatting.
4.  Add labels, assignees, and milestones as needed.

## 2. GitHub Actions

GitHub Actions is a powerful **Continuous Integration/Continuous Delivery (CI/CD)** platform that allows you to automate workflows directly within your GitHub repository. You can build, test, and deploy your code right from GitHub.

**Key uses:**
*   **Automated Testing:** Run unit tests, integration tests, and end-to-end tests automatically on every push or pull request.
*   **Code Linting and Formatting:** Ensure code quality and consistency.
*   **Build Automation:** Compile code, create packages, or generate documentation.
*   **Deployment:** Automatically deploy your application to various environments (e.g., production, staging).
*   **Custom Workflows:** Automate almost any task related to your repository.

**How it works:**
*   Workflows are defined in YAML files (`.yml` or `.yaml`) located in the `.github/workflows/` directory of your repository.
*   Each workflow consists of one or more **jobs**, and each job consists of a series of **steps**.
*   Steps can run commands, execute scripts, or use pre-built **actions** from the GitHub Marketplace.

**Example (simplified `ci.yml`):**

```yaml
name: CI

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  build-and-test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Set up Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20'
      - name: Install dependencies
        run: npm install
      - name: Run tests
        run: npm test
```

## 3. GitHub Pages

GitHub Pages is a free static site hosting service that takes HTML, CSS, and JavaScript files straight from a repository on GitHub, optionally runs them through a build process, and publishes a website.

**Key uses:**
*   **Project Documentation:** Host documentation for your open-source projects.
*   **Personal Websites/Portfolios:** Create a simple personal website or portfolio.
*   **Blogs:** Host a blog using static site generators like Jekyll.

**How to use:**
1.  **Create a `gh-pages` branch:** For project sites, you typically create a branch named `gh-pages` and push your static site files to it.
2.  **Configure in settings:** Go to your repository's "Settings" tab, then navigate to "Pages" in the left sidebar. Select the branch (e.g., `gh-pages` or `main` with a `/docs` folder) and folder you want to publish from.
3.  Your site will be available at `https://your-username.github.io/your-repository-name/`.

---

This concludes our comprehensive Git and GitHub tutorial! You've learned everything from the basics of version control to advanced Git commands and powerful GitHub features. Keep practicing, and happy coding!