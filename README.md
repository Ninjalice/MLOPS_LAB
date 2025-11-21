# MLOps Lab 1 - Image Classification System

![CI Pipeline](https://github.com/Ninjalice/MLOPS_LAB/actions/workflows/ci.yml/badge.svg)

## 📋 Project Overview

This project implements an **Image Classification System** with a complete MLOps pipeline using GitHub Actions for Continuous Integration. The system provides functionality for image classification, resizing, and preprocessing through three interfaces:

- **Logic Module**: Core functionality for image processing and classification
- **CLI**: Command-line interface for local operations
- **API**: RESTful API built with FastAPI for web-based interactions

## 🎯 Features

### Image Classification
- Random class prediction from predefined categories
- Support for 10 classes: cat, dog, bird, fish, horse, deer, frog, car, airplane, ship

### Image Processing
- **Resize**: Change image dimensions to any size
- **RGB Conversion**: Convert images to RGB mode
- **Preprocessing**: Combined RGB conversion and resizing (default: 224x224)
- **Image Info**: Get image dimensions and color mode

## 🏗️ Project Structure

```
MLOPS_LAB/
├── .github/
│   └── workflows/
│       └── ci.yml              # CI/CD pipeline configuration
├── api/
│   ├── __init__.py
│   └── api.py                  # FastAPI application
├── cli/
│   ├── __init__.py
│   └── cli.py                  # Command-line interface
├── logic/
│   ├── __init__.py
│   └── classifier.py           # Core logic for classification
├── templates/
│   └── home.html               # API homepage template
├── tests/
│   ├── __init__.py
│   ├── test_api.py            # API tests
│   ├── test_cli.py            # CLI tests
│   └── test_logic.py          # Logic tests
├── .gitignore
├── Makefile                    # Build automation
├── pyproject.toml              # Project dependencies and configuration
├── README.md                   # This file
└── Lab1.pdf                    # Assignment document
```

## 🚀 Getting Started

### Prerequisites

- Python 3.8 or higher
- [uv](https://github.com/astral-sh/uv) package manager

### Installation

1. Clone the repository:
```bash
git clone https://github.com/Ninjalice/MLOPS_LAB.git
cd MLOPS_LAB
```

2. Install dependencies:
```bash
make install
# or manually:
uv sync
```

## 💻 Usage

### Command Line Interface (CLI)

The CLI provides several commands for image processing:

#### Predict Image Class
```bash
uv run python -m cli.cli predict <image_path>
```

#### Resize Image
```bash
uv run python -m cli.cli resize <image_path> <width> <height> <output_path>
```

#### Preprocess Image
```bash
uv run python -m cli.cli preprocess <image_path> <output_path> --width 224 --height 224
```

#### Convert to RGB
```bash
uv run python -m cli.cli to-rgb <image_path> <output_path>
```

#### Get Image Information
```bash
uv run python -m cli.cli info <image_path>
```

### API

Start the FastAPI server:
```bash
uv run python -m api.api
```

The API will be available at `http://localhost:8000`

#### API Endpoints

- `GET /` - Homepage with API documentation
- `GET /health` - Health check endpoint
- `POST /predict` - Classify an image
- `POST /resize` - Resize an image
- `POST /preprocess` - Preprocess an image (RGB + resize)
- `POST /classify_and_resize` - Combined classification and resizing

Visit `http://localhost:8000/docs` for interactive API documentation (Swagger UI).

## 🧪 Testing

Run all tests:
```bash
make test
# or manually:
uv run pytest tests/ -v --cov=logic --cov=cli --cov=api
```

## 🛠️ Development

### Available Make Commands

```bash
make install    # Install dependencies
make format     # Format code with Black
make lint       # Lint code with Pylint
make test       # Run tests with Pytest
make refactor   # Format and lint code
make all        # Run all tasks (install, format, lint, test)
make clean      # Clean up generated files
```

### Code Quality

- **Formatting**: Black (line length: 100)
- **Linting**: Pylint
- **Testing**: Pytest with coverage reporting

## 🔄 Continuous Integration

This project uses GitHub Actions for CI/CD. The pipeline automatically:

1. Checks out the code
2. Sets up Python environment
3. Installs dependencies with uv
4. Formats code with Black
5. Lints code with Pylint
6. Runs tests with Pytest
7. Uploads coverage reports

The CI pipeline is triggered on:
- Push to `main` or `develop` branches
- Pull requests to `main` or `develop` branches

## 📦 Dependencies

### Core Dependencies
- **click**: Command-line interface framework
- **fastapi**: Modern web framework for APIs
- **uvicorn**: ASGI server
- **jinja2**: Template engine for HTML
- **httpx**: HTTP client
- **pillow**: Image processing library
- **python-multipart**: File upload support

### Development Dependencies
- **pylint**: Code linting
- **pytest**: Testing framework
- **pytest-cov**: Coverage reporting
- **black**: Code formatting

## 📝 Assignment Requirements

This project fulfills all requirements for MLOps Lab 1:

✅ Machine learning project structure with incremental methodology  
✅ Logic module with image classification and preprocessing  
✅ Command-line interface (CLI) using Click  
✅ RESTful API using FastAPI  
✅ Comprehensive test suite for all components  
✅ Virtual environment management with uv  
✅ HTML homepage for API  
✅ Makefile for automation (install, lint, format, test)  
✅ CI/CD pipeline with GitHub Actions  
✅ Status badge in README  
✅ Proper project documentation  

## 👥 Authors

- Endika - [Ninjalice](https://github.com/Ninjalice)

## 📄 License

This project is part of the MLOps course at UPNA (Universidad Pública de Navarra).

## 🙏 Acknowledgments

- Based on the MLOps Lab 1 demo repository: [JoseanSanz/MLOps-Lab1-demo](https://github.com/JoseanSanz/MLOps-Lab1-demo)
- UPNA MLOps Course instructors

---

**Note**: In this initial version (Lab 1), the image classification uses random prediction. Future labs will implement actual deep learning models for real image classification.
