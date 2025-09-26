# Contributing to Real-Time Disease Tracking System

We welcome contributions to the Real-Time Disease Tracking System! This document provides guidelines for contributing to the project.

## 🎯 How to Contribute

### Reporting Issues

1. **Check existing issues** first to avoid duplicates
2. **Use issue templates** when available
3. **Provide detailed information** including:
   - Steps to reproduce
   - Expected vs actual behavior
   - Environment details (OS, Python version, browser)
   - Screenshots if applicable

### Suggesting Features

1. **Open a feature request** issue
2. **Describe the problem** your feature would solve
3. **Explain your proposed solution**
4. **Consider alternatives** and mention them

### Code Contributions

1. **Fork the repository**
2. **Create a feature branch** from `main`:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Make your changes** following our coding standards
4. **Add tests** for new functionality
5. **Update documentation** as needed
6. **Commit your changes** with clear messages
7. **Push to your fork** and **create a pull request**

## 🔧 Development Setup

### Prerequisites
- Python 3.8+
- MySQL 5.7+
- Git
- Virtual environment tool

### Setup Instructions

1. **Clone your fork:**
   ```bash
   git clone https://github.com/YOUR_USERNAME/real-time-disease-tracking.git
   cd real-time-disease-tracking
   ```

2. **Set up virtual environment:**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure environment:**
   ```bash
   cp .env.example .env
   # Edit .env with your database credentials
   ```

5. **Set up database:**
   ```bash
   python manage.py migrate
   python manage.py createsuperuser
   ```

6. **Run development server:**
   ```bash
   python manage.py runserver
   ```

## 📝 Coding Standards

### Python Code Style

- Follow **PEP 8** guidelines
- Use **meaningful variable names**
- Write **docstrings** for functions and classes
- Keep **line length under 88 characters**
- Use **type hints** where appropriate

### Code Formatting

We use automated tools for code formatting:

```bash
# Format code with black
black .

# Sort imports with isort
isort .

# Lint with flake8
flake8 .
```

### Django Best Practices

- Use **class-based views** when appropriate
- Follow **Django naming conventions**
- Keep **models simple** and focused
- Use **Django's built-in validators**
- Write **comprehensive tests**

### Frontend Standards

- Use **semantic HTML**
- Follow **accessibility guidelines**
- Keep **JavaScript modular**
- Use **Bootstrap classes** consistently
- Ensure **mobile responsiveness**

## 🧪 Testing Requirements

### Running Tests

```bash
# Run all tests
python manage.py test

# Run specific test file
python manage.py test tests.test_models

# Run with coverage
coverage run --source='.' manage.py test
coverage report
```

### Test Guidelines

- **Write tests** for all new features
- **Maintain >80% code coverage**
- Use **descriptive test names**
- **Mock external dependencies**
- Test **both success and failure cases**

### Test Types

1. **Unit Tests**: Test individual functions/methods
2. **Integration Tests**: Test component interactions
3. **API Tests**: Test REST API endpoints
4. **Frontend Tests**: Test user interface behavior

## 📚 Documentation

### Documentation Requirements

- **Update README.md** if adding new features
- **Document API changes** in API_DOCUMENTATION.md
- **Add installation steps** for new dependencies
- **Include code examples** in documentation
- **Write clear commit messages**

### Documentation Style

- Use **clear, concise language**
- Include **code examples**
- Add **screenshots** for UI changes
- Keep **documentation up-to-date**

## 🚀 Pull Request Process

### Before Submitting

1. **Ensure all tests pass**
2. **Update documentation**
3. **Check code formatting**
4. **Write clear commit messages**
5. **Rebase on latest main branch**

### Pull Request Template

```markdown
## Description
Brief description of the changes

## Type of Change
- [ ] Bug fix (non-breaking change that fixes an issue)
- [ ] New feature (non-breaking change that adds functionality)
- [ ] Breaking change (fix or feature that would cause existing functionality to not work as expected)
- [ ] Documentation update

## Testing
- [ ] Tests pass locally
- [ ] Added tests for new functionality
- [ ] Tested on multiple browsers (if applicable)

## Checklist
- [ ] My code follows the project's style guidelines
- [ ] I have performed a self-review of my code
- [ ] I have commented my code where necessary
- [ ] I have made corresponding changes to the documentation
- [ ] My changes generate no new warnings
```

### Review Process

1. **Automated checks** must pass (CI/CD pipeline)
2. **Code review** by maintainers
3. **Testing** on staging environment
4. **Approval** by project maintainers
5. **Merge** into main branch

## 🎨 Design Guidelines

### UI/UX Principles

- **Mobile-first** design approach
- **Accessibility** compliance (WCAG 2.1)
- **Consistent** visual hierarchy
- **Clear** navigation and feedback
- **Fast** loading and responsive

### Color Scheme

- Primary: Health/medical themed colors
- Secondary: Complementary accent colors
- Ensure **sufficient contrast** for accessibility
- Use **semantic colors** for status indicators

## 🔒 Security Guidelines

### Security Practices

- **Validate all input** data
- **Sanitize** user-generated content
- **Use HTTPS** in production
- **Protect sensitive** information
- **Follow OWASP** security guidelines

### Sensitive Data

- **Never commit** secrets or credentials
- **Use environment variables** for configuration
- **Encrypt** sensitive health data
- **Implement** proper access controls

## 📞 Getting Help

### Communication Channels

- **GitHub Issues**: For bugs and feature requests
- **GitHub Discussions**: For questions and ideas
- **Email**: Contact project maintainers directly

### Resources

- [Django Documentation](https://docs.djangoproject.com/)
- [Python Style Guide](https://pep8.org/)
- [Git Best Practices](https://git-scm.com/doc)
- [Project Wiki](https://github.com/chowhanm25/real-time-disease-tracking/wiki)

## 🏆 Recognition

Contributors will be:
- **Listed** in project documentation
- **Credited** in release notes
- **Invited** to join the maintainer team (for significant contributions)

## 📄 License

By contributing, you agree that your contributions will be licensed under the project's MIT License.

---

**Thank you for contributing to the Real-Time Disease Tracking System!** 🎉

Your contributions help improve global health monitoring and make a real difference in disease outbreak detection and response.