# Contributing to Dhvagna

First off, thank you for considering contributing to Dhvagna! It's people like you that make Dhvagna such a great tool.

## Code of Conduct

By participating in this project, you are expected to uphold our [Code of Conduct](CODE_OF_CONDUCT.md). Please take a moment to read it before proceeding.

## How Can I Contribute?

### Reporting Bugs

This section guides you through submitting a bug report for Dhvagna. Following these guidelines helps maintainers and the community understand your report, reproduce the behavior, and find related reports.

**Before Submitting A Bug Report:**

* Check the [issues](https://github.com/gnanesh-16/Dhvagna/issues) on GitHub to see if the problem has already been reported. If it has and the issue is still open, add a comment to the existing issue instead of opening a new one.
* Determine which repository the problem should be reported in.

**How Do I Submit A (Good) Bug Report?**

Bugs are tracked as [GitHub issues](https://github.com/gnanesh-16/Dhvagna/issues). When you create an issue, please provide the following information:

* **Use a clear and descriptive title** for the issue to identify the problem.
* **Describe the exact steps which reproduce the problem** in as many details as possible.
* **Provide specific examples to demonstrate the steps**. Include links to files or GitHub projects, or copy/pasteable snippets, which you use in those examples.
* **Describe the behavior you observed after following the steps** and point out what exactly is the problem with that behavior.
* **Explain which behavior you expected to see instead and why.**
* **Include screenshots and/or animated GIFs** which show you following the described steps and clearly demonstrate the problem.
* **If the problem is related to audio processing or performance**, include information about your hardware, OS, sample rate, and audio file format.
* **If the problem wasn't triggered by a specific action**, describe what you were doing before the problem happened and share more information using the guidelines below.

### Suggesting Enhancements

This section guides you through submitting an enhancement suggestion for Dhvagna, including completely new features and minor improvements to existing functionality.

**Before Submitting An Enhancement Suggestion:**

* Check if there's already a package which provides that enhancement.
* Check the [issues list](https://github.com/gnanesh-16/Dhvagna/issues) to see if the enhancement has already been suggested. If it has, add a comment to the existing issue instead of opening a new one.

**How Do I Submit A (Good) Enhancement Suggestion?**

Enhancement suggestions are tracked as GitHub issues. When creating an enhancement issue, please provide the following information:

* **Use a clear and descriptive title** for the issue to identify the suggestion.
* **Provide a step-by-step description of the suggested enhancement** in as many details as possible.
* **Provide specific examples to demonstrate the steps**. Include copy/pasteable snippets which you use in those examples.
* **Describe the current behavior** and **explain which behavior you expected to see instead** and why.
* **Include screenshots and animated GIFs** which help you demonstrate the steps or point out the part of Dhvagna which the suggestion is related to.
* **Explain why this enhancement would be useful** to most Dhvagna users.
* **List some other applications where this enhancement exists.**
* **Specify which version of Dhvagna you're using.**
* **Specify the name and version of the OS you're using.**

### Your First Code Contribution

Unsure where to begin contributing to Dhvagna? You can start by looking through these `beginner` and `help-wanted` issues:

* [Beginner issues](https://github.com/gnanesh-16/Dhvagna/labels/beginner) - issues which should only require a few lines of code, and a test or two.
* [Help wanted issues](https://github.com/gnanesh-16/Dhvagna/labels/help%20wanted) - issues which should be a bit more involved than `beginner` issues.

### Pull Requests

The process described here has several goals:

- Maintain Dhvagna's quality
- Fix problems that are important to users
- Engage the community in working toward the best possible Dhvagna
- Enable a sustainable system for Dhvagna's maintainers to review contributions

Please follow these steps to have your contribution considered by the maintainers:

1. Follow all instructions in [the template](PULL_REQUEST_TEMPLATE.md)
2. Follow the [styleguides](#styleguides)
3. After you submit your pull request, verify that all [status checks](https://help.github.com/articles/about-status-checks/) are passing

While the prerequisites above must be satisfied prior to having your pull request reviewed, the reviewer(s) may ask you to complete additional design work, tests, or other changes before your pull request can be ultimately accepted.

## Styleguides

### Git Commit Messages

* Use the present tense ("Add feature" not "Added feature")
* Use the imperative mood ("Move cursor to..." not "Moves cursor to...")
* Limit the first line to 72 characters or less
* Reference issues and pull requests liberally after the first line
* Consider starting the commit message with an applicable emoji:
    * 🎨 `:art:` when improving the format/structure of the code
    * 🐎 `:racehorse:` when improving performance
    * 🚱 `:non-potable_water:` when plugging memory leaks
    * 📝 `:memo:` when writing docs
    * 🐛 `:bug:` when fixing a bug
    * 🔥 `:fire:` when removing code or files
    * 💚 `:green_heart:` when fixing the CI build
    * ✅ `:white_check_mark:` when adding tests
    * 🔒 `:lock:` when dealing with security
    * ⬆️ `:arrow_up:` when upgrading dependencies
    * ⬇️ `:arrow_down:` when downgrading dependencies

### Python Styleguide

All Python code should adhere to [PEP 8](https://www.python.org/dev/peps/pep-0008/).

### Documentation Styleguide

* Use [Markdown](https://daringfireball.net/projects/markdown).
* Use consistent and clear naming of functions and parameters.
* Include code examples when appropriate.
* Keep documentation up to date with code changes.

## API Key Development

When working on features related to API key handling:

1. **Never commit real API keys to the repository**
2. Use environment variables for storing API keys during development
3. Test with development keys that have the prefix `dk-`
4. Implement proper error handling for invalid API keys
5. Consider implementing a mock API service for testing

## Project Structure

To maintain consistency within the project, please follow this structure when adding new files:

```
dhvagna/
├── __init__.py
├── core/
│   ├── __init__.py
│   ├── audio.py         # Audio recording and processing
│   ├── transcription.py # Transcription logic
│   └── api.py           # API key validation and usage tracking
├── utils/
│   ├── __init__.py
│   ├── prompts.py       # Default and custom prompts
│   └── formatting.py    # Output formatting utilities
└── examples/
    ├── basic_example.py
    ├── simple_example.py
    ├── prompt_customization_example.py
    └── advanced_example.py
```

## Testing

Please write tests for new code you create. We use the `pytest` framework for our tests.

Run the tests with:

```bash
pytest
```

## Development Environment Setup

1. **Fork the repository**:
   - Visit the [Dhvagna repository](https://github.com/gnanesh-16/Dhvagna) and click on the "Fork" button.

2. **Clone your fork**:
   ```bash
   git clone https://github.com/YOUR-USERNAME/Dhvagna.git
   cd Dhvagna
   ```

3. **Set up a virtual environment**:
   ```bash
   python -m venv venv
   # On Windows
   venv\Scripts\activate
   # On Unix or MacOS
   source venv/bin/activate
   ```

4. **Install development dependencies**:
   ```bash
   pip install -e ".[dev]"
   ```

5. **Set up your API key**:
   - Get a development API key from [https://github.com/gnanesh-16/Dhvagna](https://github.com/gnanesh-16/Dhvagna)
   - Set it as an environment variable:
     ```bash
     # On Windows (Command Prompt)
     set DHVGNA_API_KEY=dk-your_unique_key_here

     # On Windows (PowerShell)
     $env:DHVGNA_API_KEY="dk-your_unique_key_here"

     # On Linux/MacOS
     export DHVGNA_API_KEY="dk-your_unique_key_here"
     ```

## Release Process

The release process is handled by the project maintainers. If you're interested in helping with releases:

1. Ensure all tests pass on the main branch
2. Update version numbers in:
   - `setup.py`
   - `__init__.py`
   - Documentation
3. Update the CHANGELOG.md file
4. Create a new tag and release on GitHub
5. Publish to PyPI

## Additional Resources

* [General GitHub documentation](https://help.github.com)
* [GitHub pull request documentation](https://help.github.com/articles/about-pull-requests/)
* [Python Testing With pytest](https://docs.pytest.org/en/latest/)

## Attribution

This Contributing Guide is adapted from the open-source contribution guidelines for [Atom](https://github.com/atom/atom/blob/master/CONTRIBUTING.md).

---

Thank you for contributing to Dhvagna! Your efforts help make this project better for everyone.
