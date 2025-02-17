# Python Project Cookiecutter Template

A comprehensive cookiecutter template for Python projects with best practices, including code quality tools, testing setup, and GitHub Actions CI/CD.

## Features

- Modern Python packaging with `pyproject.toml`
- Code formatting with Black, isort, and docformatter
- Code quality checks with Flake8 and various plugins
- Static type checking with mypy
- Automated testing with pytest
- Pre-commit hooks for code quality
- GitHub Actions for CI/CD
- PR title linting for conventional commits
- Coverage reporting with Codecov

## Requirements

- Python 3.11+
- [Cookiecutter](https://cookiecutter.readthedocs.io/en/latest/installation.html) (`pip install cookiecutter`)

## Usage

There are two ways to use this template:

### 1. Using GitHub (Recommended)

```bash
cookiecutter gh:cremerf/python-cookiecutter
```

### 2. Using Local Template

If you've cloned this repository locally:

```bash
cookiecutter path/to/python-cookiecutter
```

## Template Options

When you create a project, you'll be prompted for these values:

| Option                  | Description                         | Default                                      |
| ----------------------- | ----------------------------------- | -------------------------------------------- |
| `project_name`        | Your project's human-readable name  | "My Python Project"                          |
| `project_slug`        | Your project's Python package name  | Derived from project_name                    |
| `project_description` | A short description of your project | "A Python project with best practices setup" |
| `author_name`         | Your name                           | "Your Name"                                  |
| `author_email`        | Your email                          | "your.email@example.com"                     |
| `python_version`      | Python version to use               | "3.11"                                       |
| `open_source_license` | License to use                      | Choice of MIT, BSD-3, GPL-3, Apache-2        |
| `use_pytest`          | Include pytest testing              | "y"                                          |
| `use_black`           | Include Black code formatting       | "y"                                          |
| `use_flake8`          | Include Flake8 linting              | "y"                                          |
| `use_mypy`            | Include mypy type checking          | "y"                                          |
| `use_isort`           | Include isort import sorting        | "y"                                          |
| `use_pre_commit`      | Include pre-commit hooks            | "y"                                          |
| `use_github_actions`  | Include GitHub Actions CI/CD        | "y"                                          |

## What's Included

After running the template, your project will have:

1. **Project Structure**:

   ```
   your_project/
   ├── .github/
   │   └── workflows/
   │       └── ci.yml
   ├── your_project/
   │   └── __init__.py
   ├── tests/
   ├── .gitignore
   ├── .pre-commit-config.yaml
   ├── pyproject.toml
   ├── README.md
   └── LICENSE
   ```
2. **Development Tools**:

   - Black for code formatting
   - Flake8 for code linting
   - isort for import sorting
   - mypy for static type checking
   - pytest for testing
   - pre-commit for git hooks
   - GitHub Actions for CI/CD
3. **Quality Assurance**:

   - Automated testing with pytest
   - Code coverage reporting
   - PR title linting
   - Comprehensive pre-commit hooks

## After Generation

After generating your project:

1. Create a new GitHub repository
2. Push your code
3. Set up branch protection rules
4. Add any required secrets (e.g., `CODECOV_TOKEN`)

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the BSD-3-Clause License - see the LICENSE file for details.
