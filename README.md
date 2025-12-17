# Calculator Project with GitHub Actions

A simple Python calculator project demonstrating GitHub Actions CI/CD pipeline.

## 🚀 Features

- Basic arithmetic operations (add, subtract, multiply, divide)
- Comprehensive unit tests with pytest
- Automated CI/CD with GitHub Actions
- Code linting with flake8
- Test coverage reporting

## 📁 Project Structure

```
├── .github/
│   └── workflows/
│       └── ci.yml          # GitHub Actions workflow
├── src/
│   ├── __init__.py
│   └── calculator.py       # Calculator module
├── tests/
│   ├── __init__.py
│   └── test_calculator.py  # Unit tests
├── .gitignore
├── README.md
└── requirements.txt
```

## 🛠️ Setup

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd github_actions
   ```

2. Create a virtual environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

## 🧪 Running Tests

```bash
# Run all tests
pytest tests/ -v

# Run with coverage
pytest tests/ -v --cov=src --cov-report=term-missing
```

## 📋 Linting

```bash
flake8 src/ tests/ --max-line-length=100
```

## 🔄 GitHub Actions Workflow

The CI pipeline automatically runs on:
- Push to `main` or `master` branch
- Pull requests to `main` or `master` branch

### Pipeline Jobs:

1. **Test Job**: Runs on Python 3.9, 3.10, 3.11, and 3.12
   - Checks out code
   - Sets up Python
   - Caches pip dependencies
   - Installs dependencies
   - Runs flake8 linting
   - Runs pytest with coverage
   - Uploads coverage artifacts

2. **Build Job**: Runs after tests pass
   - Confirms successful build
   - Runs the calculator demo

## 📝 Usage Example

```python
from src.calculator import add, subtract, multiply, divide

result = add(5, 3)       # Returns 8
result = subtract(10, 4) # Returns 6
result = multiply(3, 7)  # Returns 21
result = divide(15, 3)   # Returns 5.0
```

## 📄 License

MIT License

