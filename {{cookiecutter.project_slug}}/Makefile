.PHONY: help setup install init-git init-hooks clean

# Default Python version from cookiecutter
PYTHON_VERSION = {{ cookiecutter.python_version }}
# Get project name from directory
PROJECT_NAME = $(shell basename $(CURDIR))

help:
	@echo "Available commands:"
	@echo "make setup         - Create and setup Python venv environment"
	@echo "make install       - Install project dependencies"
	@echo "make init-git      - Initialize git repository"
	@echo "make init-hooks    - Initialize pre-commit hooks"
	@echo "make clean         - Clean up generated files"

setup:
	@echo "🐍 Creating Python virtual environment..."
	python -m venv .venv
	@echo "🔌 Activating virtual environment..."
	@echo "To activate the virtual environment, run:"
	@echo "source .venv/bin/activate  # On Unix/macOS"
	@echo ".venv\\Scripts\\activate    # On Windows"

install:
	@echo "📚 Installing dependencies..."
	python -m pip install --upgrade pip
	pip install -e ".[dev]"

init-git:
	@if [ ! -d .git ]; then \
		echo "📦 Initializing git repository..."; \
		git init; \
		if [ ! -f .git/refs/heads/main ]; then \
			git add .; \
			git commit -m "feat: initial commit"; \
		fi \
	fi

init-hooks:
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