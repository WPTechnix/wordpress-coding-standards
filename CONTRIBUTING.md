# Contributing to WPTechnixWordPress Coding Standards

Thank you for your interest in contributing to the WPTechnix WordPress Coding Standards! This document provides guidelines and instructions for contributing to the project.

## Code of Conduct

By participating in this project, you agree to maintain a respectful and inclusive environment for all contributors. We expect everyone to follow our Code of Conduct.

## How to Contribute

### Reporting Issues

If you find a bug, have a suggestion for a new rule, or want to discuss an existing one:

1.  Check if the issue already exists in the [GitHub Issues](https://github.com/wptechnix/wordpress-coding-standards/issues).
2.  If not, create a new issue with a clear title and a detailed description.
3.  Include relevant details such as:
    *   PHP version (must be 8.0+).
    *   PHP_CodeSniffer and WordPress Coding Standards versions.
    *   Example code that demonstrates the issue.
    *   The expected behavior vs. the actual behavior.

### Submitting Pull Requests

1.  Fork the repository.
2.  Create a new branch from `main` for your feature or fix:
    ```bash
    git checkout -b feat/your-feature-name
    ```
3.  Make your changes and commit them using the [Conventional Commits](https://www.conventionalcommits.org/) format:
    ```bash
    git commit -m "feat: add rule for WP_Query best practices"
    ```
4.  Push your branch to your forked repository:
    ```bash
    git push origin feat/your-feature-name
    ```
5.  Open a Pull Request against the `main` branch of the original repository.

## Commit Message Guidelines

This project uses [Conventional Commits](https://www.conventionalcommits.org/) for automated versioning and changelog generation. All commit messages must adhere to this specification.

### Commit Message Format

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Types

*   `feat`: A new feature (e.g., adding a new sniff) - triggers a **minor** version bump.
*   `fix`: A bug fix (e.g., correcting a rule's behavior) - triggers a **patch** version bump.
*   `docs`: Documentation changes only.
*   `style`: Code style changes (formatting, etc.).
*   `refactor`: Code refactoring without changing external behavior.
*   `perf`: A code change that improves performance.
*   `test`: Adding or updating tests.
*   `build`: Changes to the build system or external dependencies.
*   `ci`: Changes to CI configuration files and scripts.
*   `chore`: Other changes that don't modify source or test files.
*   `revert`: Reverting a previous commit.

### Breaking Changes

To indicate a breaking change, add `BREAKING CHANGE:` in the commit footer or add a `!` after the type. This will trigger a **major** version bump.

```
feat!: remove deprecated WordPress rule

BREAKING CHANGE: The `WordPress.WP.DeprecatedFunctions` rule has been removed in favor of a more comprehensive solution.
```

## Development Setup

### Prerequisites

*   PHP 8.0 or higher
*   Composer 2.x
*   Node.js 18.0 or higher
*   npm 9.0 or higher

### Setup Steps

1.  Clone the repository:
    ```bash
    git clone https://github.com/wptechnix/wordpress-coding-standards.git
    cd wordpress-coding-standards
    ```

2.  Install Composer dependencies:
    ```bash
    composer install
    ```

3.  Install Node.js dependencies (for commit message validation):
    ```bash
    npm install
    ```

    This automatically sets up [Husky](https://typicode.github.io/husky/) git hooks to validate your commit messages locally before you commit.

## Testing Your Changes

Before submitting a pull request, it is crucial to test your changes locally to ensure they work as expected.

1.  Create a temporary PHP file on your local machine. This file is for your testing purposes and **should not be included in your pull request**.
2.  In this file, add various code samples that your changes should affect. Include examples of code that should trigger an error and code that should pass inspection.
3.  From the root of the project, run PHP_CodeSniffer against your local test file:
    ```bash
    ./vendor/bin/phpcs --standard=WPTechnixWordPress /path/to/your/local/test-file.php
    ```
4.  Verify that the output from PHP_CodeSniffer matches your expectations.

## Modifying Rules

When adding, removing, or modifying rules in `WPTechnixWordPress/ruleset.xml`:

1.  Provide a clear reason for the change in your commit message and pull request.
2.  Ensure the rule does not conflict with existing rules in the base `WPTechnix` standard or other WordPress rules.
3.  Test the changes with real-world WordPress code examples.
4.  Update the `README.md` or other documentation if the changes are significant.

## Release Process

Releases are **fully automated** using [release-please](https://github.com/googleapis/release-please).

### How It Works

1.  When pull requests with conventional commit messages are merged into the `main` branch, the `release-please` action creates or updates a "Release PR."
2.  This special PR contains an updated `CHANGELOG.md` and the next version number based on the types of commits merged (`fix`, `feat`, `feat!`, etc.).
3.  When the Release PR is merged, the following happens automatically:
    *   A new Git tag (e.g., `v1.2.0`) is created.
    *   A new GitHub Release is published with the generated changelog.
    *   Packagist detects the new tag and publishes the new version to the package repository.

**Important:** Do not manually edit the `CHANGELOG.md` or the version number. The automated process handles this entirely.

## License

By contributing to this project, you agree that your contributions will be licensed under its MIT License.