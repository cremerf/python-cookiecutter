# Python Project Cookiecutter Template

A streamlined cookiecutter template for Python projects that enforces code quality, type checking, and CI/CD best practices.

## Why This Template?

This template provides a standardized project structure with integrated tools for:
- Code formatting and quality (Black, isort, Flake8)
- Static type checking (mypy)
- Automated CI/CD with GitHub Actions
- Pre-commit hooks for consistent code quality

## Directory Structure

After using this template, your project will have this structure:
```
project_name/
├── .github/
│   └── workflows/
│       └── ci.yml
├── ci/
├── scripts/
├── src/
│   └── __init__.py
├── .pre-commit-config.yaml
├── pyproject.toml
├── Makefile
└── README.md
```

## Requirements

- Python {{ cookiecutter.python_version }}+
- Cookiecutter (`pip install cookiecutter`)
- Make (usually pre-installed on Unix/macOS, for Windows install via chocolatey or scoop)
- Git (required for version management and pre-commit hooks)

## Quick Start

1. Generate your project:
   ```bash
   cookiecutter gh:cremerf/python-cookiecutter
   ```

2. Navigate to your project and initialize git:
   ```bash
   cd your_project_name
   make init-git
   ```

3. Create and activate the virtual environment:
   ```bash
   make setup
   
   # On Unix/macOS
   source .venv/bin/activate
   
   # On Windows
   .venv\Scripts\activate
   ```

4. Install dependencies:
   ```bash
   make install
   ```

5. Set up pre-commit hooks:
   ```bash
   make init-hooks
   ```

## Configuration Options (cookiecutter.json)

The `cookiecutter.json` file customizes your project during generation. You'll be prompted for:

| Option                | Description                         | Default                                    |
|----------------------|-------------------------------------|----------------------------------------------|
| `project_name`       | Your project's human-readable name  | "My Python Project"                         |
| `project_slug`       | Your project's package name         | Derived from project_name                   |
| `project_description`| Short project description           | "A Python project with best practices setup"|
| `author_name`        | Your name                           | "Your Name"                                 |
| `author_email`       | Your email                          | "your.email@example.com"                    |
| `python_version`     | Python version to use               | "3.11"                                      |
| `open_source_license`| Project license                     | Choice of MIT, BSD-3, GPL-3, Apache-2       |

## Available Make Commands

- `make help` - Show available commands
- `make init-git` - Initialize git repository and create initial commit
- `make setup` - Create Python virtual environment
- `make install` - Install project dependencies (requires activated virtual environment)
- `make init-hooks` - Set up pre-commit hooks (requires activated virtual environment)
- `make clean` - Clean up generated files

Note: The commands `make install` and `make init-hooks` require an activated virtual environment. The Makefile will check for this and provide helpful error messages if the environment is not activated.

## Project Structure Explained

1. **Source Code**:
   - `src/` - Main package directory for your Python modules
   - `scripts/` - Utility scripts and tools
   - `ci/` - Continuous Integration related scripts

2. **Development Tools**:
   - `.github/workflows/` - GitHub Actions CI/CD configurations
   - `.pre-commit-config.yaml` - Pre-commit hook configurations
   - `pyproject.toml` - Project configuration and dependencies
   - `Makefile` - Development workflow automation

## What's Included

1. **Code Quality Tools**:
   - Black for code formatting
   - Flake8 for code linting
   - isort for import sorting
   - mypy for static type checking

2. **Development Workflow**:
   - Pre-commit hooks for automated code quality checks
   - GitHub Actions for CI/CD
   - PR title linting for conventional commits

## After Generation

1. Create a new GitHub repository

2. Link and push to your repository:
   ```bash
   git remote add origin your-repo-url
   git push -u origin main
   ```

3. Set up branch protection rules in GitHub

4. Start developing in the `src/` directory

## License

This project is licensed under the BSD-3-Clause License - see the LICENSE file for details.
