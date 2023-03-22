# Webilicious.in CI/CD Pipeline: A Journey of Continuous Deployment

![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white) ![Netlify](https://img.shields.io/badge/netlify-%23000000.svg?style=for-the-badge&logo=netlify&logoColor=#00C7B7)

Welcome to the Webilicious.in CI/CD pipeline documentation, a journey of continuous deployment that ensures every change goes through rigorous testing and review before being deployed to production. Buckle up and let's explore the exciting process that powers our website!

## Introduction

In this project, there are three branches in GitHub:`release/production`, `release/staging`, and `release/development`. Features and bug fixes can only be merged with the `release/development` branch, which can only be merged with `release/staging`, and only `release/staging` can merge with `release/production`. This check is performed using a GitHub Actions workflow file that runs before each pull request.

The website is hosted on Netlify, with one site linked to each branch (`release/production`, `release/staging`, and `release/development`). Whenever a pull request occurs, the site corresponding to the affected branch is built.


## Workflow

The following is the workflow of the CI/CD pipeline:

1. 🛠️ A new feature or bug fix is developed in a feature branch.
2. 🚀 A pull request is opened to merge the feature branch into the     `release/development branch`.
3. 🤖 Before the pull request is merged, the GitHub Actions workflow file runs, which performs the following checks:
     * If `releases/development` is base, it will check if the merging branch is other than `release/production` and `release/staging`.
    * If `releases/staging` is base, it will check if the merging branch is `release/development`.
    * If `releases/production` is base, it will check if the merging branch is `release/staging`.
4. ✅ If the checks pass, the pull request is merged into the `release/development` branch.
5. 🏗️ Netlify detects the change in the `release/development` branch and starts building the corresponding site.
6. 🌐 The site is deployed to a staging URL for testing and review.
7. 👍 Once the changes have been reviewed and approved, a pull request is opened to merge the `release/development` branch into the `release/staging` branch.
8. 🤖 The GitHub Actions workflow file runs again to perform the same checks as in step 3.
9. ✅ If the checks pass, the `release/development` branch is merged into the `release/staging` branch.
10. 🏗️ Netlify detects the change in the `release/staging` branch and starts building the corresponding site.
11. 🌐 The site is deployed to a staging URL for final testing and review.
12. 👍 Once the changes have been fully tested and approved, a pull request is opened to merge the `release/staging` branch into the `release/production` branch.
13. 🤖 The GitHub Actions workflow file runs again to perform the same checks as in step 3.
14. ✅ If the checks pass, the `release/staging` branch is merged into the `release/production` branch.
15. 🏗️ Netlify detects the change in the `release/production` branch and starts building the corresponding site.
16. 🌐 The site is deployed to the production URL.

## Conclusion

The CI/CD pipeline created for the website webilicious.in ensures that all changes go through a rigorous testing and review process before being deployed to production. By using GitHub Actions and Netlify, the pipeline is fully automated and reduces the risk of errors and downtime. 🚀👨‍💻👩‍💻


