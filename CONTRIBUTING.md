# Contributing to MedAssist

Thank you for your interest in contributing to MedAssist! 🎉

## How to Contribute

### 🐛 Reporting Bugs
1. Check existing [Issues](https://github.com/rajaganaa/medassist-backend/issues)
2. Open a new issue with:
   - Clear title and description
   - Steps to reproduce
   - Expected vs actual behavior
   - Screenshots if applicable

### 💡 Feature Requests
1. Open an issue with the `enhancement` label
2. Describe the feature and why it would be useful
3. Include any relevant examples or mockups

### 🔧 Pull Requests
1. Fork the repository
2. Create a feature branch: `git checkout -b feature/your-feature`
3. Make your changes
4. Test thoroughly
5. Commit with clear messages: `git commit -m "feat: add new tool for drug interactions"`
6. Push to your fork: `git push origin feature/your-feature`
7. Open a Pull Request

## Development Setup

### Prerequisites
- Python 3.9+
- Azure Functions Core Tools v4
- Git

### Local Setup
```bash
# Clone the repo
git clone https://github.com/rajaganaa/medassist-backend.git
cd medassist-backend

# Create virtual environment
python -m venv .venv
source .venv/bin/activate  # Linux/Mac
.venv\Scripts\activate     # Windows

# Install dependencies
pip install -r requirements.txt

# Set up environment variables
cp .env.example .env
# Edit .env with your API keys

# Run locally
func start
```

## Code Style
- Follow PEP 8 for Python code
- Add docstrings to all functions and classes
- Keep functions focused and modular

## Adding New Tools
To add a new tool to the agent:

1. Create a new file in `tools/` (e.g., `drug_interactions.py`)
2. Use the `@tool` decorator from LangChain
3. Add clear tool description (the LLM reads this!)
4. Register in `tools/__init__.py`
5. Update the system prompt in `function_app.py`

## License
By contributing, you agree that your contributions will be licensed under the MIT License.

---

*Built with ❤️ by RAJAGANAPATHY M*
