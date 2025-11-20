<h1 align="center">WPTechnixWordPress Coding Standards</h1>

<p align="center">
    <strong>WordPress-specific coding standards building upon WPTechnix base standards for modern, secure, and performant code.</strong>
</p>

<p align="center">
    <a href="https://github.com/wptechnix/wordpress-coding-standards"><img src="https://img.shields.io/badge/source-wptechnix/wordpress--coding--standards-blue.svg?style=flat-square" alt="Source Code"></a>
    <a href="https://packagist.org/packages/wptechnix/wordpress-coding-standards"><img src="https://img.shields.io/packagist/v/wptechnix/wordpress-coding-standards.svg?style=flat-square&label=release" alt="Download Package"></a>
    <a href="https://php.net"><img src="https://img.shields.io/packagist/php-v/wptechnix/wordpress-coding-standards.svg?style=flat-square&colorB=%238892BF" alt="PHP Programming Language"></a>
    <a href="https://github.com/wptechnix/wordpress-coding-standards/blob/master/LICENSE"><img src="https://img.shields.io/packagist/l/wptechnix/wordpress-coding-standards.svg?style=flat-square&colorB=darkcyan" alt="Read License"></a>
</p>

## About

This is a coding standard for [PHP_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer) designed specifically for WordPress development. It extends the base [WPTechnix Coding Standards](https://github.com/WPTechnix/coding-standards), which already enforces strict types, immutability, and PSR-12 compliance, and incorporates rules from the official [WordPress Coding Standards](https://github.com/WordPress/WordPress-Coding-Standards).

This ruleset is designed to help you write modern, secure, and high-quality WordPress code, with a focus on:

**WordPress Best Practices:**
-   Enforces the use of WordPress functions and APIs over native PHP.
-   Checks for proper use of text domains for internationalization (i18n).
-   Discourages the use of deprecated WordPress functions, classes, and parameters.
-   Verifies correct prefixing and naming conventions for classes and functions.
-   Ensures proper enqueueing of scripts and styles.

**Security:**
-   Requires nonce verification for form and URL processing.
-   Enforces proper data validation and sanitization of all inputs.
-   Mandates output escaping to prevent XSS vulnerabilities.
-   Flags the use of insecure and discouraged PHP and WordPress functions.

**Database:**
-   Discourages direct database queries, promoting the use of WordPress database APIs.
-   Enforces the use of prepared statements to prevent SQL injection attacks.
-   Identifies potentially slow and inefficient database queries.

**Code Quality & Analysis:**
-   Flags the use of development functions (`var_dump`, `error_log`, etc.).
-   Prevents modification of global variables.
-   Enforces strict type checking (e.g., in `in_array`).

## Installation

Install this package as a development dependency using [Composer](https://getcomposer.org).

```bash
composer require --dev wptechnix/wordpress-coding-standards
```

### Optional: Automatic Installation with Dealerdirect

For automatic registration with PHP_CodeSniffer, you can optionally install [dealerdirect/phpcodesniffer-composer-installer](https://github.com/Dealerdirect/phpcodesniffer-composer-installer):

```bash
composer require --dev dealerdirect/phpcodesniffer-composer-installer
```

This plugin will:

-   Automatically register the standard with PHP_CodeSniffer upon Composer install.
-   Eliminate the need for manual path configuration.
-   Make the standard immediately available for use in your `phpcs.xml` configuration.

**Note:** This is optional. If you prefer manual configuration or have a custom PHP_CodeSniffer setup, you can skip this step and configure the path manually in your `phpcs.xml` file.

## Usage

To use this coding standard, add `<rule ref="WPTechnixWordPress"/>` to your `phpcs.xml` configuration.

Here is an example `phpcs.xml.dist` file that you can place in the root of your repository:

```xml
<?xml version="1.0"?>
<ruleset xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
        xsi:noNamespaceSchemaLocation="vendor/squizlabs/php_codesniffer/phpcs.xsd">

    <arg name="extensions" value="php"/>
    <arg name="colors"/>
    <arg value="sp"/>

    <file>./src</file>
    <file>./tests</file>

    <rule ref="WPTechnixWordPress"/>

</ruleset>
```

Then, run PHP_CodeSniffer:

```bash
./vendor/bin/phpcs
```

To automatically fix violations:

```bash
./vendor/bin/phpcbf
```

## Contributing

Contributions are welcome! To contribute, please familiarize yourself with the project's `CONTRIBUTING.md`.

## Copyright and License

The `wptechnix/wordpress-coding-standards` library is copyright © [WPTechnix](https://wptechnix.com) and licensed for use under the terms of the MIT License (MIT). Please see [LICENSE](LICENSE) for more information.