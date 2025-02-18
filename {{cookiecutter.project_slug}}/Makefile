.PHONY: help init-git setup install init-hooks clean

# Default Python version from cookiecutter
PYTHON_VERSION = {{ cookiecutter.python_version }}
# Get project name from directory
PROJECT_NAME = $(shell basename $(CURDIR))

help:
	@echo "Available commands:"
	@echo "make init-git      - Initialize git repository and create initial commit"
	@echo "make setup         - Create Python virtual environment"
	@echo "make install       - Install project dependencies"
	@echo "make init-hooks    - Set up pre-commit hooks"
	@echo "make clean         - Clean up generated files"

init-git:
	@if [ ! -d .git ]; then \
		echo "📦 Initializing git repository..."; \
		git init; \
		git add .; \
		git commit -m "feat: initial project structure"; \
		BRANCH_NAME=$$(git branch --show-current); \
		if [ "$$BRANCH_NAME" = "master" ]; then \
			echo "🔄 Renaming default branch to main..."; \
			git branch -m master main; \
		fi; \
		echo "✨ Git repository initialized with initial commit"; \
		echo "Next steps:"; \
		echo "1. Create a repository on GitHub"; \
		echo "2. Run: git remote add origin <your-repo-url>"; \
		echo "3. Run: git push -u origin main"; \
	else \
		echo "🔍 Git repository already initialized"; \
	fi

setup: init-git
	@echo "🐍 Creating Python virtual environment..."
	python3 -m venv .venv
	@echo "🔌 To activate the virtual environment, run:"
	@echo "source .venv/bin/activate  # On Unix/macOS"
	@echo ".venv\\Scripts\\activate    # On Windows"
	@if [ ! -f .gitignore ]; then \
		echo "❌ Error: .gitignore file is missing. Please check your project structure."; \
		exit 1; \
	fi

install:
	@if [ -z "$${VIRTUAL_ENV}" ]; then \
		echo "❌ Virtual environment is not activated. Please activate it first."; \
		echo "Run: source .venv/bin/activate  # On Unix/macOS"; \
		echo "  or: .venv\\Scripts\\activate    # On Windows"; \
		exit 1; \
	fi
	@echo "📚 Installing dependencies..."
	python3 -m pip install --upgrade pip setuptools wheel
	pip install -e ".[dev]"

init-hooks:
	@if [ -z "$${VIRTUAL_ENV}" ]; then \
		echo "❌ Virtual environment is not activated. Please activate it first."; \
		exit 1; \
	fi
	@echo "🔧 Setting up pre-commit hooks..."
	pre-commit install
	pre-commit install --hook-type commit-msg

clean:
	@echo "🧹 Cleaning up..."
	rm -rf build/
	rm -rf dist/
	rm -rf *.egg-info
	find . -type d -name "__pycache__" -exec rm -rf {} +
	find . -type d -name "*.pyc" -exec rm -rf {} +
	find . -type d -name ".pytest_cache" -exec rm -rf {} +
	find . -type d -name ".coverage" -exec rm -rf {} +
	find . -type d -name ".mypy_cache" -exec rm -rf {} +

# Default target when just running 'make'
all: help 