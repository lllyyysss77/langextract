```markdown
# langextract Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill teaches you the core development patterns and conventions used in the `langextract` Python codebase. You'll learn how to structure files, write imports and exports, and follow the project's conventions for naming and testing. This guide also provides step-by-step workflows and suggested commands to streamline your development process.

## Coding Conventions

### File Naming
- Use **snake_case** for all file names.
  - Example: `text_parser.py`, `language_utils.py`

### Import Style
- Use **relative imports** within the package.
  - Example:
    ```python
    from .utils import extract_language
    from .models import LanguageModel
    ```

### Export Style
- Use **named exports** (explicitly define what is exported).
  - Example:
    ```python
    __all__ = ['extract_language', 'LanguageModel']
    ```

### Commit Patterns
- Commits are **freeform** (no strict prefixing).
- Average commit message length: **54 characters**.
  - Example:
    ```
    Add initial language extraction logic and tests
    ```

## Workflows

### Running Tests
**Trigger:** When you want to verify your code changes.
**Command:** `/run-tests`

1. Identify test files (pattern: `*_test.py`).
2. Run tests using your preferred Python test runner (e.g., `pytest` or `unittest`).
   ```bash
   python -m unittest discover
   # or
   pytest
   ```
3. Review test output and fix any failing tests.

### Adding a New Module
**Trigger:** When you need to add new functionality.
**Command:** `/add-module`

1. Create a new Python file using snake_case (e.g., `feature_extractor.py`).
2. Use relative imports to reference other modules.
   ```python
   from .utils import helper_function
   ```
3. Define functions/classes and add them to `__all__` for named exports.
   ```python
   __all__ = ['new_feature']
   ```
4. Write corresponding tests in a file named `feature_extractor_test.py`.

### Writing a Commit
**Trigger:** When saving changes to version control.
**Command:** `/commit`

1. Stage your changes.
   ```bash
   git add .
   ```
2. Write a concise, descriptive commit message (no strict prefix required).
   ```bash
   git commit -m "Describe your change here"
   ```
3. Push your commit to the repository.

## Testing Patterns

- Test files follow the pattern: `*_test.py`
  - Example: `langextract_test.py`
- Testing framework is **unknown**; use standard Python testing tools (`unittest`, `pytest`).
- Place test files alongside the modules they test or in a dedicated `tests/` directory.

**Example test file:**
```python
import unittest
from .langextract import extract_language

class TestLangExtract(unittest.TestCase):
    def test_extract_language(self):
        self.assertEqual(extract_language("Bonjour"), "fr")

if __name__ == '__main__':
    unittest.main()
```

## Commands
| Command      | Purpose                                      |
|--------------|----------------------------------------------|
| /run-tests   | Run all test files to verify code correctness|
| /add-module  | Add a new module following conventions       |
| /commit      | Commit changes with a descriptive message    |
```
