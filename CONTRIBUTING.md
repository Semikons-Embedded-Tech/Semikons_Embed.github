# Contributing to Semikons Embedded Technologies

Thank you for your interest in contributing to Semikons Embedded Technologies projects! This document provides guidelines for contributing code, documentation, and other improvements.

---

## 🎯 Code of Conduct

We are committed to providing a welcoming and inclusive environment for all contributors. Please review our [Code of Conduct](CODE_OF_CONDUCT.md) before contributing.

---

## 🚀 Getting Started

### 1. Fork the Repository
```bash
# Clone your fork
git clone https://github.com/YOUR_USERNAME/repository-name.git
cd repository-name
```

### 2. Create a Branch
```bash
# Create a feature branch (not on main/master)
git checkout -b feature/your-feature-name
# or for bug fixes:
git checkout -b bugfix/issue-description
```

### 3. Make Changes
- Follow the coding standards specified in the repository
- Add comments for complex logic
- Include unit tests for new functionality
- Update documentation as needed

### 4. Commit with Clear Messages
```bash
git commit -m "Add clear, descriptive commit message"
# Format: "[Category] Brief description"
# Examples:
# [Feature] Add UART timeout configuration
# [Bugfix] Fix ADC initialization race condition
# [Docs] Update FreeRTOS configuration guide
```

### 5. Push & Create Pull Request
```bash
git push origin feature/your-feature-name
```

Then create a pull request on GitHub with:
- Clear description of changes
- Reference to related issues (if any)
- Test results or validation proof
- Screenshots (for hardware/UI changes)

---

## 📝 Coding Standards

### C/C++ Code
- **Standard**: MISRA-C 2012 (for safety-critical code)
- **Indentation**: 2 spaces (not tabs)
- **Line Length**: Max 100 characters (80 preferred)
- **Naming**:
  - Functions: `snake_case()`
  - Variables: `snake_case`
  - Constants: `UPPER_SNAKE_CASE`
  - File-scoped statics: `_snake_case`

### Example
```c
// Good: Clear, follows conventions
#define MAX_BUFFER_SIZE 256
#define UART_TIMEOUT_MS 1000

static uint8_t _rx_buffer[MAX_BUFFER_SIZE];

void uart_init(uint32_t baud_rate)
{
    // Implementation with proper indentation
}
```

### Python Code
- **Standard**: PEP 8
- **Type Hints**: Required for public functions
- **Docstrings**: Use Google style docstrings

```python
def calculate_activity(acceleration: np.ndarray) -> str:
    """Classify human activity from IMU data.
    
    Args:
        acceleration: Nx3 array of acceleration values (m/s²)
    
    Returns:
        Activity classification string ('walking', 'running', 'static', etc.)
    """
    # Implementation
    pass
```

### Documentation
- **Markdown**: Use standard Markdown format
- **Code Blocks**: Specify language (```c, ```python, etc.)
- **Examples**: Include practical usage examples
- **Links**: Use relative paths for internal docs

---

## 📋 Pull Request Checklist

Before submitting a PR, ensure:

- [ ] Code follows project coding standards
- [ ] All tests pass locally (`make test` or equivalent)
- [ ] New code includes unit tests (minimum 80% coverage)
- [ ] Documentation is updated or added
- [ ] Commit messages are clear and descriptive
- [ ] No merge conflicts with main/master branch
- [ ] Changes are focused on a single feature/fix (not mixed concerns)
- [ ] Sensitive information (API keys, credentials) is NOT included

### For Hardware/PCB Changes
- [ ] Schematic reviewed for correctness
- [ ] All component values verified against datasheets
- [ ] Power budget calculated and verified
- [ ] EMI/EMC considerations documented
- [ ] Bill of Materials (BOM) updated

### For Firmware Changes
- [ ] Code compiles without warnings
- [ ] Tested on target hardware
- [ ] Memory usage verified (heap/stack usage documented)
- [ ] Performance impact assessed (timing, power consumption)
- [ ] Error handling is robust

---

## 🧪 Testing Requirements

### Unit Tests
```bash
# Example for C projects
cd test/
make test
# Output should show all tests passing
```

### Integration Tests
- Test on actual hardware when possible
- Include reproducible test steps in PR description

### Code Coverage
- Aim for **≥80% code coverage** on new code
- Use coverage tools: `gcov`, `coverage.py`, etc.
- Run: `make coverage` (or equivalent)

---

## 📚 Documentation Standards

### README Files
Each repository and major project folder should include a README.md with:
1. **Project Title** - Clear, descriptive name
2. **Overview** - 2-3 sentences explaining purpose
3. **Features** - Bulleted list of key capabilities
4. **Hardware Requirements** - MCU, peripherals, sensors needed
5. **Software Stack** - RTOS, compiler, tools, versions
6. **Installation** - Step-by-step setup instructions
7. **Usage** - How to build, compile, and run
8. **Examples** - Sample code and expected output
9. **Testing** - How to validate functionality
10. **Contributing** - Link to CONTRIBUTING.md
11. **License** - License type and link to LICENSE file

### Code Comments
- **Function Headers**:
  ```c
  /**
   * @brief Brief description of what function does
   * @param param1 Description of parameter 1
   * @param param2 Description of parameter 2
   * @return Description of return value
   */
  ```

- **Complex Logic**: Explain the "why", not just the "what"
  ```c
  // Wait for DMA to complete before proceeding to avoid data corruption
  while (!dma_is_complete()) {
      // Spin until transfer finishes
  }
  ```

- **Hacks/Workarounds**: Clearly mark and explain
  ```c
  // FIXME: Bug in HAL version 1.2 requires this workaround
  // Remove when upgrading to HAL >= 1.3
  NVIC_EnableIRQ(UART_IRQn);
  ```

---

## 🔍 Review Process

### What to Expect
1. **Automated Checks**: CI/CD pipeline runs (linting, builds, tests)
2. **Code Review**: Maintainer reviews code for quality and standards compliance
3. **Feedback**: We'll request changes if needed
4. **Approval**: Once approved, your PR is merged

### Response Time
- Simple PRs (docs, small fixes): 1-3 days
- Medium PRs (features): 3-7 days
- Complex PRs (major changes): 1-2 weeks

### Merge Criteria
- All automated checks pass
- At least one maintainer approval
- No unresolved comments
- Branch is up-to-date with main/master

---

## 🐛 Reporting Bugs

### Before Filing an Issue
1. Check existing issues and pull requests
2. Ensure you're using the latest version
3. Try to reproduce the bug consistently

### Issue Template
```markdown
### Description
Brief description of the bug

### Steps to Reproduce
1. Step 1
2. Step 2
3. Step 3

### Expected Behavior
What should happen

### Actual Behavior
What actually happens

### Environment
- Hardware: [e.g., STM32H747, Hikvision NVR]
- Software: [e.g., FreeRTOS 11.0, ESP-IDF 5.1]
- Compiler: [e.g., GCC 11.2]
- OS: [e.g., Ubuntu 22.04, Windows 10]

### Additional Context
Screenshots, logs, error messages, etc.
```

---

## 💡 Feature Requests

### Proposal Template
```markdown
### Feature Description
What feature or enhancement would you like?

### Motivation
Why is this feature needed?

### Proposed Solution
How should it work?

### Alternatives Considered
Are there other ways to solve this?

### Additional Context
Examples, references, or related issues
```

---

## 📖 Documentation Contributions

We welcome documentation improvements:
- **Fix typos** → Direct PR welcome
- **Clarify explanations** → PR with proposed changes
- **Add examples** → Include code that compiles/runs
- **Translation** → Discuss scope first (create an issue)

---

## 🏢 Corporate Contributions

If you're contributing on behalf of a company:
1. Ensure you have authorization to contribute
2. Sign our [Corporate Contributor Agreement](docs/CCA.md) (if applicable)
3. Include company information in PR (when relevant)
4. All contributions follow the same standards

---

## 📜 Licensing

By contributing, you agree that your contributions will be licensed under the same license as the project. This typically includes:
- **MIT** for open-source projects
- **Apache 2.0** for broader compatibility
- **Proprietary** for commercial products

---

## 🏆 Recognition

Contributors are recognized in:
- **README** - Contributors section
- **CHANGELOG** - Release notes
- **GitHub** - Automatic contributor credit
- **Annual Report** - Major contributors highlighted

---

## ❓ Getting Help

### Resources
- **GitHub Discussions**: Ask questions in repository discussions
- **Issues**: File bugs and feature requests
- **Email**: [contact@semikonstech.com](mailto:contact@semikonstech.com)
- **Website**: [www.semikonstech.com](https://www.semikonstech.com)

### Community
- Join discussions on embedded systems topics
- Participate in code reviews
- Help other contributors

---

## 🙏 Thank You

Thank you for contributing to Semikons projects! Your improvements help make better embedded systems for everyone.

---

**Last Updated**: 2025
**Maintained By**: Semikons Embedded Technologies Team
