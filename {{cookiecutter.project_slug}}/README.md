# My Python Cookie Cutter Project

A Python project with best practices setup

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

## Installation

```bash
# Clone the repository
git clone <repository-url>
cd {{ cookiecutter.project_slug }}

# Create a virtual environment (optional but recommended)
python -m venv .venv
source .venv/bin/activate  # On Windows, use `.venv\Scripts\activate`

# Install the package with development dependencies
pip install -e ".[dev]"

# Set up pre-commit hooks
pre-commit install  # Install pre-commit hooks
pre-commit install --hook-type commit-msg  # Install commit message hook
```

## Development

This project uses several tools to ensure code quality:

- **Black**: Code formatting
- **isort**: Import sorting
- **Flake8**: Code style and quality checking
- **mypy**: Static type checking
- **pytest**: Testing framework
- **pre-commit**: Git hooks for code quality

### Pre-commit Setup and Usage

Pre-commit is a framework for managing and maintaining multi-language pre-commit hooks. Here's how to work with it:

#### Initial Setup

```bash
# Install pre-commit in your environment
pip install pre-commit

# Install the git hooks
pre-commit install  # Install pre-commit hooks
pre-commit install --hook-type commit-msg  # Install commit message hook

# (Optional) Update hooks to latest version
pre-commit autoupdate
```

#### Daily Usage

Pre-commit hooks run automatically on `git commit`. However, you can also run them manually:

```bash
# Run all pre-commit hooks on all files
pre-commit run --all-files

# Run a specific hook on all files
pre-commit run black --all-files
pre-commit run isort --all-files

# Run hooks on specific files
pre-commit run --files path/to/file1.py path/to/file2.py
```

#### Fixing Issues

When pre-commit hooks fail, here's how to fix common issues:

1. **Code Formatting Issues (Black, isort)**:

```bash
# Format all Python files with Black
black .

# Sort imports in all Python files
isort .
```

2. **Docstring Formatting Issues**:

```bash
# Format docstrings
docformatter --in-place --wrap-summaries=88 --wrap-descriptions=88 **/*.py
```

3. **Unused Imports/Variables**:

```bash
# Remove unused imports and variables
autoflake --in-place --remove-all-unused-imports --remove-unused-variables **/*.py
```

4. **Type Checking Issues (mypy)**:

```bash
# Run mypy to see detailed type errors
mypy .
```

5. **Flake8 Issues**:

```bash
# Run flake8 to see style issues
flake8 .
```

After fixing the issues:

```bash
# Stage the changes
git add .

# Try committing again
git commit -m "type: your commit message"
```

#### Skipping Hooks

In rare cases, you might need to skip pre-commit hooks (not recommended):

```bash
git commit -m "your message" --no-verify
```

#### Commit Message Format

Commit messages must follow the conventional commits format and start with one of:

- `feat:` (new feature)
- `fix:` (bug fix)
- `docs:` (documentation changes)
- `style:` (formatting, missing semi colons, etc)
- `model:` (model-related changes)
- `refactor:` (refactoring code)
- `test:` (adding tests, refactoring tests)
- `build:` (build system, deployment changes)
- `chore:` (updating grunt tasks etc)
- `revert:` (reverting changes)

Example: `feat: add user authentication system`

### Running Tests

```bash
# Run tests with coverage
pytest tests/ --cov={{ cookiecutter.project_slug }}
```

## Contributing

1. Fork the repository
2. Create a new branch (`git checkout -b feature/amazing-feature`)
3. Make your changes
4. Run the tests and quality checks
5. Commit your changes (following [conventional commits](https://www.conventionalcommits.org/))
6. Push to the branch
7. Open a Pull Request

## License

This project is licensed under the BSD-3-Clause License - see the LICENSE file for details.

## Author

Fede Cremer . [cremerf.mle@gmail.com](mailto:cremerf.mle@gmail.com)
