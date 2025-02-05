
# Development Best Practices and Standards

## 1. Testing Standards
All code must be tested with a combination of **unit tests**, **functional tests**, or **integration tests** as appropriate. Testing ensures reliability and maintainability.

### Coverage Requirements
- **Minimum Coverage**: 80%
- Use automated tools to track and report coverage. Strive for higher coverage where feasible.

### Example Using Pytest
```python
# Function example with pytest coverage
def add(a, b):
    """Add two numbers."""
    return a + b

# Unit test using pytest
def test_add():
    assert add(1, 2) == 3
```
Use **fixtures** and **mocking** for robust testing.

### Pytest Fixture Example
```python
import pytest

@pytest.fixture
def sample_data():
    return {"key": "value"}

def test_sample(sample_data):
    assert sample_data["key"] == "value"
```

## 2. Code Documentation
- Use **Sphinx-compliant** docstrings in English.
- Document all functions, classes, and modules with clear descriptions, parameters, and return values.

### Sphinx Docstring Example
```python
def calculate_area(length, width):
    """
    Calculate the area of a rectangle.

    :param length: The length of the rectangle (float)
    :param width: The width of the rectangle (float)
    :return: The calculated area (float)
    """
    return length * width
```

## 3. Git Workflow (Modified Gitflow)
We use a modified version of **Gitflow**. Here’s a detailed workflow:

### Feature Branch Workflow
- **Create a Feature Branch**: Always create from `develop`.
- **Development**: Commit regularly and run tests and quality checks.
- **Pull Requests (PRs)**: Must be used for merging code. Never push directly to `develop` or `main`.

### Pull Request and Merge Policy
1. All code must be reviewed and merged via **GitHub Pull Requests**. Developers should **never merge** directly into `develop` or `main`.
2. Use **SonarCloud** for quality checks and assign a reviewer for every PR.
3. Only the **Repository Leader** or an authorized team member can perform the final merge into `develop` or `main`.

### Merging Policy
- Use **squash and merge** to maintain a clean commit history.
- Avoid using `git flow feature finish`. Instead, finalize changes using GitHub’s PR system.

## 4. Release Branch Workflow
- **Create a Release Branch** from `develop` when ready.
- Perform final checks and quality tests.
- Use a PR to merge into `main`. Only the **Repository Leader** can complete this merge.
- Tag the release and then merge `main` back into `develop` using a PR.

### Git Commands for Release Branch
```bash
# Create and switch to a new release branch
git checkout develop
git pull origin develop
git checkout -b release/v1.0.0
```
Finalize all merges via a GitHub Pull Request.

## Using the `git flow` CLI Tool (Revised)
To simplify the workflow, use the **git flow** CLI tool for branching only. Do **not** use `git flow feature finish` or `git flow release finish`. Always use GitHub Pull Requests for merging.

### Git Flow for Feature Branch
```bash
git flow feature start <feature-name>
```
- Develop and commit code.
- Use GitHub Pull Requests for merging.

## 5. Handling Requirements with pip-tools
We manage Python package dependencies using **pip-tools**. Follow these steps for adding new requirements:

### Steps for Handling Requirements
1. Add the new package to `requirements.in`.
2. Use `pip-tools` to compile the dependencies into `requirements.txt`.
   ```bash
   pip-compile requirements.in
   ```
3. Sync the requirements in your virtual environment.
   ```bash
   pip-sync
   ```

### Example Update Process
1. Add the package:
   ```
   # requirements.in
   new-package==1.2.3
   ```
2. Compile and sync:
   ```bash
   pip-compile requirements.in
   pip-sync
   ```

## 6. Creating GitHub Issues
Developers are encouraged to create **issues** using GitHub's **BUG** and **FEATURE** templates at any time for any necessary improvements, enhancements, or bug reporting. This helps in keeping track of the project’s needs and ensuring a clear path for future development.

### How to Create an Issue
1. Navigate to the **Issues** tab in the repository.
2. Click **New Issue** and select the appropriate template: **BUG** for defects or **FEATURE** for enhancements.
3. Fill out the issue details clearly, providing as much context as possible.

---

## Tool Utilization Overview
- **Python**: Primary programming language.
- **Pytest**: Testing framework.
- **SonarCloud**: Code quality and coverage tool.
- **GitHub**: Version control and PR management.
- **pip-tools**: Dependency management.

---

### Quick Reference
1. Ensure code has **80%+ coverage**.
2. Use **Sphinx docstrings**.
3. Develop using **feature branches**, never push to `develop` or `main` directly.
4. Use GitHub PRs for all merges, even for `develop` and `main`.
5. Manage dependencies using **pip-tools**.
6. Create **GitHub Issues** for any new features or bug reports.
