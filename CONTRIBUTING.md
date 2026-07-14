# Contributing to AminoSeqIndex

Thank you for your interest in contributing to AminoSeqIndex.

## How to Contribute

### Reporting Bugs

1. Check [existing issues](https://github.com/gopizux/AminoSeqIndex/issues) to avoid duplicates.
2. Open a new issue using the **Bug Report** template.
3. Include: browser name/version, steps to reproduce, expected vs actual behavior, and a screenshot if applicable.

### Suggesting Features

1. Open a new issue using the **Feature Request** template.
2. Describe the use case and how the feature would improve the tool.

### Submitting Changes

1. Fork the repository.
2. Create a branch from `main`: `git checkout -b feature/your-feature-name`
3. Make your changes in the `src/` directory (if refactored) or edit `index.html` directly.
4. Test across browsers: Chrome, Firefox, Safari, Edge.
5. Ensure no new external dependencies are introduced without discussion.
6. Submit a pull request with a clear description of changes.

### Code Style

- **HTML**: Use semantic elements where possible.
- **CSS**: Follow existing naming conventions (BEM-like: `.category-nonpolar`, `.sequence-grid`).
- **JavaScript**: Use vanilla ES6+ features. No frameworks or build tools.
- Keep the single-file architecture unless a change genuinely requires splitting.

### Testing

Before submitting, verify:
- [ ] Sequence input accepts all 20 standard amino acid codes (ACDEFGHIKLMNPQRSTVWY)
- [ ] Invalid characters trigger the error message
- [ ] All four output formats render correctly
- [ ] DOCX export produces a valid Word document
- [ ] Positional indexing aligns for sequences of length 1, 50, 500, and 10,000+

### Community Guidelines

- Be respectful and constructive.
- Focus on the tool's mission: making protein sequence analysis accessible.
- Ask questions if anything is unclear.

## Contact

- **Issues**: Use GitHub Issues (preferred)
- **Email**: gopizux@gmail.com
