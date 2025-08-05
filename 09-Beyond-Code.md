# Part 6: GitHub Features - Beyond Code

GitHub is far more than just a place to host your Git repositories. It provides a rich ecosystem of features that enhance collaboration, automate workflows, manage projects, and even host websites. This section introduces some of these key features that extend beyond basic code versioning.

## 1. GitHub Issues (Project Tracking & Communication)

GitHub Issues are a powerful, built-in system for tracking tasks, enhancements, bug reports, and general discussions related to your project. They serve as a centralized, transparent place for communication and progress tracking.

**Key Uses & Benefits:**
*   **Bug Tracking:** Report, prioritize, and manage software defects.
*   **Feature Requests:** Propose, discuss, and plan new features.
*   **Task Management:** Break down larger projects into smaller, manageable tasks.
*   **Discussions & Feedback:** Engage with collaborators, users, and the community about project-related topics, gather feedback, and answer questions.
*   **Transparency:** All discussions and decisions are publicly visible (for public repositories), fostering an open development process.

**Core Features:**
*   **Labels:** Categorize issues for better organization (e.g., `bug`, `enhancement`, `documentation`, `help wanted`, `good first issue`).
*   **Assignees:** Assign issues to specific team members responsible for addressing them.
*   **Milestones:** Group issues into larger project goals, release cycles, or sprints, providing a clear timeline.
*   **Projects (Kanban Boards):** Visualize and manage issues using flexible Kanban-style boards, allowing you to track progress through custom columns (e.g., "To Do," "In Progress," "Done").
*   **Mentions and References:** Easily link issues to pull requests, other issues, or specific code lines using `#` followed by the issue number (e.g., `Fixes #123`, `Closes #456`). Mention users with `@username`.
*   **Issue Templates:** Define custom templates for new issues (e.g., Bug Report, Feature Request) to guide users in providing necessary information.

**How to Use:**
1.  Navigate to the "Issues" tab in your GitHub repository.
2.  Click "New issue."
3.  Provide a clear, concise title and a detailed description. Use Markdown for formatting, code blocks, and checklists.
4.  Utilize the sidebar to add labels, assignees, link to milestones, and connect to project boards.

## 2. GitHub Actions (CI/CD & Workflow Automation)

GitHub Actions is a powerful, flexible **Continuous Integration/Continuous Delivery (CI/CD)** platform that allows you to automate virtually any software development workflow directly within your GitHub repository. You can build, test, and deploy your code, and automate other tasks like linting, security scans, and documentation generation.

**Key Uses & Benefits:**
*   **Automated Testing:** Automatically run unit tests, integration tests, and end-to-end tests on every push, pull request, or schedule.
*   **Code Quality Checks:** Enforce coding standards with linters, formatters, and static analysis tools.
*   **Build Automation:** Compile code, create packages, generate artifacts, and build Docker images.
*   **Deployment:** Automatically deploy your application to various environments (e.g., staging, production, cloud providers) upon successful builds.
*   **Custom Workflows:** Automate almost any task related to your repository, such as sending notifications, managing issues, or generating reports.

**How it Works:**
*   Workflows are defined in YAML files (`.yml` or `.yaml`) located in the `.github/workflows/` directory of your repository.
*   Each workflow is triggered by specific events (e.g., `push`, `pull_request`, `schedule`, `workflow_dispatch` for manual triggers).
*   A workflow consists of one or more **jobs**, which run in parallel by default.
*   Each job runs on a specified runner (e.g., `ubuntu-latest`, `windows-latest`, `macos-latest`).
*   Each job consists of a series of **steps**. Steps can run shell commands, execute scripts, or use pre-built **actions** from the GitHub Marketplace.

**Example: Basic CI Workflow (`.github/workflows/ci.yml`)**

This workflow runs tests on every push to `main` and every pull request targeting `main`.

```yaml
name: CI Pipeline

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  build-and-test:
    runs-on: ubuntu-latest # Specifies the runner environment

    steps:
      - name: Checkout code # Uses a pre-built action to checkout the repository
        uses: actions/checkout@v4

      - name: Set up Node.js # Uses a pre-built action to set up Node.js
        uses: actions/setup-node@v4
        with:
          node-version: '20' # Specify the Node.js version

      - name: Install dependencies # Runs a shell command
        run: npm install

      - name: Run tests # Runs a shell command
        run: npm test

      - name: Lint code # Example of another step for code quality
        run: npm run lint
```

## 3. GitHub Pages (Static Site Hosting)

GitHub Pages is a free, simple, and powerful static site hosting service that takes HTML, CSS, and JavaScript files directly from a repository on GitHub, optionally runs them through a build process (like Jekyll), and publishes a website.

**Key Uses & Benefits:**
*   **Project Documentation:** Host beautiful, version-controlled documentation for your open-source projects.
*   **Personal Websites/Portfolios:** Create a simple personal website, blog, or portfolio to showcase your work.
*   **Blogs:** Host a blog using static site generators like Jekyll, Hugo, or Next.js.
*   **Landing Pages:** Create simple landing pages for projects or events.

**How to Use:**
GitHub Pages can be configured in a few ways:

1.  **User/Organization Site:** Create a repository named `username.github.io` (or `organization.github.io`). The content of the `main` branch of this repository will be published.
    *   URL: `https://username.github.io`

2.  **Project Site:** For any other repository, you can publish a site from:
    *   The `main` branch (or any other branch) in the root directory.
    *   The `main` branch (or any other branch) from a `/docs` folder.
    *   A dedicated `gh-pages` branch.

    *   URL: `https://username.github.io/repository-name/`

**Configuration Steps:**
1.  **Prepare your static files:** Ensure your `index.html` and other static assets are in the correct location (e.g., the root of your `main` branch, or within a `docs/` folder).
2.  **Configure in repository settings:** Go to your repository's "Settings" tab, then navigate to "Pages" in the left sidebar.
3.  **Select source:** Choose the branch (e.g., `main`, `gh-pages`) and the folder (e.g., `/ (root)`, `/docs`) from which you want to publish your site.
4.  **Custom Domain (Optional):** You can configure a custom domain (e.g., `www.yourdomain.com`) for your GitHub Pages site by adding a `CNAME` file to your repository and configuring your DNS records.

---

This concludes our comprehensive Git and GitHub tutorial! You've learned everything from the basics of version control to advanced Git commands and powerful GitHub features. Keep practicing, and happy coding!