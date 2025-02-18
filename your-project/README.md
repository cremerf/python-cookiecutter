# {{ cookiecutter.project_name }}

{{ cookiecutter.project_description }}

## Features

- Modern Python packaging with `pyproject.toml`
- Code formatting with Black and isort
- Code quality checks with Flake8 and various plugins
- Static type checking with mypy
- Pre-commit hooks for code quality
- GitHub Actions for CI/CD
- PR title linting for conventional commits

## Installation

```bash
# Clone the repository
git clone <repository-url>
cd {{ cookiecutter.project_slug }}

# Create a virtual environment (required)
python -m venv .venv

# Activate the virtual environment
# On Unix/macOS:
source .venv/bin/activate
# On Windows:
.venv\Scripts\activate

# Install the package with development dependencies
pip install -e ".[dev]"

# Set up pre-commit hooks
pre-commit install
pre-commit install --hook-type commit-msg
```

## Development Guide

### Code Quality Tools

This project uses several tools to ensure code quality through pre-commit hooks:

1. **Code Formatting**:
   - `black`: Formats Python code
   ```bash
   # Format all Python files
   pre-commit run black --all-files
   ```

   - `isort`: Sorts imports
   ```bash
   # Sort all Python files
   pre-commit run isort --all-files
   ```

   - `autoflake`: Removes unused imports and variables
   ```bash
   # Remove unused imports and variables
   pre-commit run autoflake --all-files
   ```

2. **Code Quality**:
   - `flake8`: Checks code style and quality
   ```bash
   # Check all files
   pre-commit run flake8 --all-files
   ```

   Includes plugins for:
   - `flake8-docstrings`: Docstring style checking
   - `flake8-bugbear`: Bug and design problem detection
   - `flake8-comprehensions`: List/set/dict comprehension optimization
   - `flake8-simplify`: Code simplification suggestions

3. **Type Checking**:
   - `mypy`: Static type checking
   ```bash
   # Check all files
   pre-commit run mypy --all-files
   ```

### Pre-commit Hooks

Pre-commit hooks run automatically before each commit to ensure code quality. They can also be run manually:

```bash
# Run all hooks on all files
pre-commit run --all-files

# Run specific hooks
pre-commit run black --all-files
pre-commit run isort --all-files
pre-commit run flake8 --all-files
pre-commit run mypy --all-files
```

Note: The pre-commit framework manages its own isolated environments for each hook. Do not try to run these tools directly from the command line unless you have explicitly installed them in your virtual environment.

### Commit Message Format

This project follows [Conventional Commits](https://www.conventionalcommits.org/). Each commit message must start with one of:

- `feat:` - New feature
- `fix:` - Bug fix
- `docs:` - Documentation changes
- `style:` - Formatting changes
- `model:` - Model-related changes
- `refactor:` - Code refactoring
- `test:` - Adding/updating tests
- `build:` - Build system changes
- `chore:` - Other changes
- `revert:` - Revert previous changes

Examples:
```bash
git commit -m "feat: add user authentication"
git commit -m "fix: handle division by zero error"
git commit -m "docs: update API documentation"
```

### Continuous Integration

The project uses GitHub Actions for CI/CD with two main workflows:

1. **PR Title Linting**: Ensures PR titles follow conventional commits format
2. **Quality Checks**: Runs all pre-commit hooks

To see the status of these checks:
1. Go to the GitHub repository
2. Click on "Actions" tab
3. Select the workflow you want to inspect

### Making Changes

1. Create a new branch:
```bash
git checkout -b feature/your-feature-name
```

2. Make your changes and ensure all checks pass:
```bash
# Run all quality checks
pre-commit run --all-files
```

3. Commit your changes:
```bash
git add .
git commit -m "feat: describe your changes"
```

4. Push and create a PR:
```bash
git push origin feature/your-feature-name
```

5. Go to GitHub and create a Pull Request

### Common Issues and Solutions

1. **Pre-commit Hook Failures**:
   ```bash
   # Update all hooks to latest versions
   pre-commit autoupdate

   # Clean pre-commit cache if having issues
   pre-commit clean
   ```

2. **Type Check Errors**:
   - Ensure all functions have type hints
   - Use `# type: ignore` sparingly and only with comments explaining why

3. **Import Sorting Issues**:
   ```bash
   # Fix import order
   isort --profile black .
   ```

4. **Code Style Issues**:
   ```bash
   # Fix style issues
   black .
   flake8 .  # To check what remains to be fixed manually
   ```

### Project Structure

```
{{ cookiecutter.project_slug }}/
├── src/                    # Source code
│   └── __init__.py
├── ci/                     # CI/CD related scripts
│   └── lint_pr_title.py   # PR title validation
├── .github/workflows/      # GitHub Actions workflows
│   └── ci.yml             # CI pipeline configuration
├── .pre-commit-config.yaml # Pre-commit hooks configuration
├── pyproject.toml         # Project configuration
├── Makefile              # Development automation
└── README.md             # This file
```

## License

This project is licensed under the {{ cookiecutter.open_source_license }} License.

## Author

{{ cookiecutter.author_name }} <{{ cookiecutter.author_email }}>
