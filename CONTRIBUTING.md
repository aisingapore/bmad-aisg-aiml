# Contributing to BMAD AI/ML Engineering Expansion Pack

Thank you for your interest in contributing to the BMAD AI/ML Engineering Expansion Pack! This guide will help you understand how to contribute effectively to this project.

## 🚀 Quick Start

1. Fork the repository
2. Create a feature branch from `main`
3. Make your changes
4. Test your changes
5. Submit a pull request

## 📋 Contribution Process

### For External Contributors

All external contributions must be submitted via **pull requests only**. Direct commits to the repository are restricted to core team members.

1. **Fork** the repository to your GitHub account
2. **Clone** your fork locally
3. **Create a branch** for your feature/fix: `git checkout -b feature/your-feature-name`
4. **Make your changes** following our coding standards
5. **Test your changes** thoroughly
6. **Commit** with clear, descriptive messages
7. **Push** to your fork
8. **Submit a pull request** to the `main` branch

### Pull Request Requirements

- [ ] Clear, descriptive title and description
- [ ] Reference any related issues
- [ ] Include tests for new functionality
- [ ] Documentation updates if applicable
- [ ] Follows project coding standards
- [ ] Passes all existing tests
- [ ] Approved by at least one core team member

## 🛠️ Development Setup

### Prerequisites

- Python >= 3.8
- Git
- Text editor or IDE

### Local Setup

```bash
# Clone your fork
git clone https://github.com/yourusername/bmad-aisg-aiml.git
cd bmad-aisg-aiml

# Create a virtual environment (recommended)
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies (if any are added in the future)
pip install -r requirements.txt  # When available
```

## 📝 Coding Standards

### File Structure

- Follow the existing directory structure
- Use descriptive file names
- Keep files focused and cohesive

### YAML Files

- Use 2-space indentation
- Include comments for complex configurations
- Validate YAML syntax before submitting

### Markdown Files

- Use consistent heading levels
- Include table of contents for long documents
- Follow existing formatting patterns
- Ensure all links work

### Commit Messages

Follow conventional commit format:
```
type(scope): description

Examples:
- feat(agents): add new ML security specialist agent
- fix(workflows): correct AISG MVP timeline
- docs(readme): update installation instructions
- refactor(templates): consolidate duplicate templates
```

## 🧪 Testing

### Before Submitting

- [ ] Validate all YAML files
- [ ] Check all markdown links
- [ ] Test any workflow changes
- [ ] Ensure documentation is up-to-date

### Testing Commands

```bash
# Validate YAML files (example)
python -c "import yaml; yaml.safe_load(open('config.yaml'))"

# Check markdown links (if tools are available)
# markdown-link-check README.md
```

## 📚 Types of Contributions

We welcome various types of contributions:

### 🔧 Code Contributions
- New agents or agent improvements
- Workflow enhancements
- Template additions or improvements
- Bug fixes

### 📖 Documentation
- README improvements
- New guides or tutorials
- Code comments and documentation
- Translation (future)

### 🐛 Bug Reports
Use GitHub Issues with:
- Clear description of the problem
- Steps to reproduce
- Expected vs actual behavior
- Environment details

### 💡 Feature Requests
Use GitHub Issues with:
- Clear use case description
- Proposed solution (if any)
- Alternative solutions considered
- Additional context

## 🏛️ Governance

### Core Team

The core team consists of maintainers with write access:
- **Najib Ninaba** ([@najibninaba](https://github.com/najibninaba))
- **Siavash Sakhavi** ([@ssakhavi](https://github.com/ssakhavi))

### Review Process

- All PRs require approval from at least one core team member
- Core team members may request changes or additional information
- Large changes may require discussion in issues before implementation
- Core team has final decision on feature inclusion

### Becoming a Core Team Member

Core team membership is by invitation based on:
- Consistent high-quality contributions
- Understanding of BMAD methodology and project goals
- Active participation in project discussions
- Demonstrated commitment to project maintenance

## 📋 AI Singapore Context

This project is specifically designed for AI Singapore (AISG) programs. When contributing:

- Understand AISG program structures (MVP, POC, SIP, LADP)
- Consider Singapore regulatory context (PDPA, IMDA, MAS)
- Respect the cultural diversity represented in our agents
- Align with AISG's mission and values

## 🤝 Code of Conduct

- Be respectful and inclusive
- Focus on constructive feedback
- Help create a welcoming environment
- Follow professional communication standards

## ❓ Questions?

- **General Questions**: Open a GitHub Discussion
- **Bug Reports**: Create a GitHub Issue
- **Feature Requests**: Create a GitHub Issue
- **Security Issues**: Contact core team directly

## 📜 License

By contributing, you agree that your contributions will be licensed under the same MIT License that covers the project.

---

## Quick Reference

### Branch Naming
- `feature/description` - New features
- `fix/description` - Bug fixes
- `docs/description` - Documentation updates
- `refactor/description` - Code refactoring

### PR Template Checklist
- [ ] Descriptive title and description
- [ ] Tests added/updated
- [ ] Documentation updated
- [ ] YAML validation passed
- [ ] Related issues referenced
- [ ] Ready for review

Thank you for contributing to BMAD AI/ML Engineering Expansion Pack! 🚀