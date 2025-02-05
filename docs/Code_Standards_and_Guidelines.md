# Version Control and Development Flow

ROMBO AI uses Git for version control, primarily adhering to a **modified Git Flow** model.

## Git Flow Overview

1. **Main Branch**  
   - Represents the production-ready codebase.  
   - Only thoroughly tested and approved changes get merged here.

2. **Develop Branch**  
   - Central branch for ongoing development.  
   - Features and bug fixes are merged here after passing review and automated tests.

3. **Feature Branches**  
   - One branch per feature or bug fix, named clearly (e.g., `feature/auth-module` or `fix/payment-errors`).
   - Merged into `develop` via Pull Request (PR) after review.

## Pull Requests (PRs)

- **Mandatory Code Reviews**: Every PR to `develop` or `main` requires at least one peer review.
- **Automated Testing**: We use **GitHub Actions** and **SonarCloud** to run test suites and code-quality checks.
- **Test Coverage**: Projects must maintain a **minimum of 80%** coverage. If coverage falls below this threshold, the PR should be revisited to include additional tests.

## Release Process

- When `develop` reaches a stable state and is ready for production, changes are merged into `main` with a versioned release tag.
- Hotfixes can be branched off `main` if critical issues arise, then merged back into both `develop` and `main`.

This flow helps ensure code quality, maintainability, and visibility into ongoing work.