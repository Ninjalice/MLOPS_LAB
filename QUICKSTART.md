# Quick Start Guide

## Setup

1. Install dependencies:
```bash
make install
# or
uv sync --all-extras
```

## Run Tests

```bash
make test
# or
uv run pytest tests/ -v --cov
```

## Format and Lint

```bash
make refactor
# or
make format && make lint
```

## CLI Usage Examples

### Predict image class
```bash
uv run python -m cli.cli predict tests/test_images/sample.png
```

### Resize image
```bash
uv run python -m cli.cli resize tests/test_images/sample.png 224 224 output.png
```

### Get image info
```bash
uv run python -m cli.cli info tests/test_images/sample.png
```

### Preprocess image
```bash
uv run python -m cli.cli preprocess tests/test_images/sample.png preprocessed.png
```

## API Usage

### Start the server
```bash
uv run python -m api.api
```

Then visit:
- Homepage: http://localhost:8000
- API Docs: http://localhost:8000/docs
- Health Check: http://localhost:8000/health

## Git Workflow

After making changes:

```bash
# Add files
git add .

# Commit
git commit -m "Your commit message"

# Push (triggers CI pipeline)
git push origin main
```

## Check CI Status

View the CI pipeline status at:
https://github.com/Ninjalice/MLOPS_LAB/actions

## Makefile Commands

- `make install` - Install all dependencies
- `make format` - Format code with Black
- `make lint` - Lint code with Pylint  
- `make test` - Run tests with coverage
- `make refactor` - Format + Lint
- `make all` - Install + Format + Lint + Test
- `make clean` - Remove generated files
