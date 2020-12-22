<!-- markdownlint-disable MD013 MD033 MD041 -->

<!-- header-logo-start -->
<div align="center">
  <a href="https://nvuillam.github.io/mega-linter" target="blank" title="Visit Mega-Linter Web Site">
    <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/images/mega-linter-logo.png" alt="Mega-Linter" height="300px">
  </a>
</div>
<!-- header-logo-end -->

## Mega-Linter

![GitHub release](https://img.shields.io/github/v/release/nvuillam/mega-linter?sort=semver)
[![Docker Pulls](https://img.shields.io/docker/pulls/nvuillam/mega-linter)](https://hub.docker.com/r/nvuillam/mega-linter)
[![Mega-Linter](https://github.com/nvuillam/mega-linter/workflows/Mega-Linter/badge.svg?branch=master)](https://nvuillam.github.io/mega-linter)
[![codecov](https://codecov.io/gh/nvuillam/mega-linter/branch/master/graph/badge.svg)](https://codecov.io/gh/nvuillam/mega-linter)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)
<!-- [![Github All Releases](https://img.shields.io/github/downloads/nvuillam/mega-linter/total.svg)](https://github.com/users/nvuillam/packages/container/package/mega-linter) -->

<!-- welcome-phrase-start -->
**Mega-Linter** analyzes [**38 languages**](#languages), [**15 formats**](#formats), [**18 tooling formats**](#tooling-formats) , [**abusive copy-pastes**](#other) and [**spelling mistakes**](#other) in your repository sources, generate [**reports in several formats**](#reporters), and can even [**apply formatting and auto-fixes**](#apply-fixes) with **auto-generated commit or PR**, to ensure all your projects are clean, whatever IDE/toolbox are used by their developers !
<!-- welcome-phrase-end -->

<!-- online-doc-start -->
See [**Online Documentation Web Site**](https://nvuillam.github.io/mega-linter/)
<!-- online-doc-end -->

![Screenshot](https://github.com/nvuillam/mega-linter/blob/master/docs/assets/images/ConsoleReporter.jpg?raw=true>)
![Screenshot](https://github.com/nvuillam/mega-linter/blob/master/docs/assets/images/GitHubCommentReporter.jpg?raw=true>)

<!-- table-of-contents-start -->
## Table of Contents

- [Mega-Linter](#mega-linter)
  - [Why Mega-Linter ?](#why_mega-linter)
  - [Quick start](#quick-start)
  - [Demo](#demo)
  - [Supported Linters](#supported-linters)
    - [Languages](#languages)
    - [Formats](#formats)
    - [Tooling formats](#tooling-formats)
    - [Other](#other)
  - [Installation](#installation)
    - [GitHub Action](#github-action)
    - [Azure](#azure)
    - [Jenkins](#jenkins)
    - [GitLab](#gitlab)
    - [Run locally](#run-mega-linter-locally)
  - [Configuration](#configuration)
    - [Activation and deactivation](#activation-and-deactivation)
    - [Apply fixes](#apply-fixes)
    - [Shared variables](#shared-variables)
    - [Linter specific variables](#linter-specific-variables)
    - [Filter linted files](#filter-linted-files)
    - [Template rules files](#template-rules-files)
  - [Reporters](#reporters)
  - [Flavors](#flavors)
  - [Add Mega-Linter badge in your repository README](#badge)
  - [How to contribute](#how-to-contribute)
  - [License](#license)
  - [Mega-Linter vs Super-Linter](#mega-linter-vs-super-linter)
<!-- table-of-contents-end -->

## Why Mega-Linter

Projects need to contain clean code, in order to **avoid technical debt**, who makes **evolutive maintenance harder and time consuming**.

By using [**code formatters and code linters**](#supported-linters), you ensure that your code base is **easier to read** and **respects best practices**, from the kick-off to each step of the project lifecycle

Not all developers have the good habit to use linters in their IDEs, making code reviews harder and longer to process

By using **Mega-Linter**, you ensure that:

- At **each pull request** it will **automatically analyze all updated code in all languages**
- **Reading error logs**, **developers learn best practices** of the language they are using
- [**Mega-Linter documentation**](https://nvuillam.github.io/mega-linter/) provides the **list of IDE plugins integrating each linter**, so developers know which linter and plugins to install
- Mega-Linter is **ready our of the box** after a [**quick setup**](#quick-start)
- **Formatting and fixes** can be automatically [**applied on the git branch**](#apply-fixes) or [**provided in reports**](https://github.com/nvuillam/mega-linter/tree/master/docs/reporters/UpdatedSourcesReporter.md)
- This tool is **100% open-source** and **free for all uses** (personal, professional, public and private repositories)
- Mega-Linter can run on [**any CI tool**](#installation) and be **run locally**: **no need to authorize an external application**, and **your code base never leaves your tooling ecosystem**

<!-- quick-start-section-start -->
## Quick Start

- Save [mega-linter.yml](https://raw.githubusercontent.com/nvuillam/mega-linter/master/TEMPLATES/mega-linter.yml) in a folder `.github/workflows` of your repository
  - If you do not want to **apply formatters and auto-fixers** in a new commit/PR, comment [**APPLY_FIXES** block variables](#apply-fixes)
  - If you do not want to check copy-pastes and spell, uncomment `# DISABLE: COPYPASTE,SPELL` in `mega-linter.yml`
- Commit, push, and create a pull request
- Watch !

**Notes**:

- This repo is a hard-fork of GitHub Super-Linter, rewritten in python to add [lots of additional features](#mega-linter-vs-super-linter)
- If you are a Super-Linter user, you can transparently **switch to Mega-Linter and keep the same configuration** (just replace `github/super-linter@v3` by `nvuillam/mega-linter@v4` in your GT Action YML file, [like on this PR](https://github.com/nvuillam/npm-groovy-lint/pull/109))
- If you want to use some advanced additional features like **applying fixes during CI**, please take 5 minutes to define [mega-linter.yml](https://raw.githubusercontent.com/nvuillam/mega-linter/master/TEMPLATES/mega-linter.yml) :)
<!-- quick-start-section-end -->

<!-- demo-section-start -->
## Demo

![Demo Gif](https://github.com/nvuillam/mega-linter/blob/master/docs/assets/images/demo_with_comments.gif?raw=true)
<!-- demo-section-end -->

<!-- supported-linters-section-start -->
## Supported Linters

All linters are integrated in the [Mega-Linter docker image](https://hub.docker.com/r/nvuillam/mega-linter), which is frequently upgraded with their latest versions

<!-- languages-section-start-->
<!-- linters-table-start -->
### Languages

| <!-- --> | Language | Linter | Configuration key | Fix |
| :---: | ----------------- | -------------- | ------------ | ------- |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/bash.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**BASH**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/bash.md#readme) | [bash-exec](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/bash_bash_exec.md#readme)| [BASH_EXEC](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/bash_bash_exec.md#readme)|  |
| <!-- --> <!-- linter-icon --> |  | [shellcheck](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/bash_shellcheck.md#readme)| [BASH_SHELLCHECK](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/bash_shellcheck.md#readme)|  |
| <!-- --> <!-- linter-icon --> |  | [shfmt](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/bash_shfmt.md#readme)| [BASH_SHFMT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/bash_shfmt.md#readme)| :heavy_check_mark: |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/c.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**C**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/c.md#readme) | [cpplint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/c_cpplint.md#readme)| [C_CPPLINT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/c_cpplint.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/clojure.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**CLOJURE**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/clojure.md#readme) | [clj-kondo](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/clojure_clj_kondo.md#readme)| [CLOJURE_CLJ_KONDO](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/clojure_clj_kondo.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/coffee.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**COFFEE**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/coffee.md#readme) | [coffeelint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/coffee_coffeelint.md#readme)| [COFFEE_COFFEELINT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/coffee_coffeelint.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/cpp.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**C++** (CPP)](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/cpp.md#readme) | [cpplint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/cpp_cpplint.md#readme)| [CPP_CPPLINT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/cpp_cpplint.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/csharp.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**C#** (CSHARP)](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/csharp.md#readme) | [dotnet-format](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/csharp_dotnet_format.md#readme)| [CSHARP_DOTNET_FORMAT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/csharp_dotnet_format.md#readme)| :heavy_check_mark: |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/dart.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**DART**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/dart.md#readme) | [dartanalyzer](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/dart_dartanalyzer.md#readme)| [DART_DARTANALYZER](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/dart_dartanalyzer.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/go.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**GO**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/go.md#readme) | [golangci-lint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/go_golangci_lint.md#readme)| [GO_GOLANGCI_LINT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/go_golangci_lint.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/groovy.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**GROOVY**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/groovy.md#readme) | [npm-groovy-lint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/groovy_npm_groovy_lint.md#readme)| [GROOVY_NPM_GROOVY_LINT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/groovy_npm_groovy_lint.md#readme)| :heavy_check_mark: |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/java.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**JAVA**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/java.md#readme) | [checkstyle](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/java_checkstyle.md#readme)| [JAVA_CHECKSTYLE](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/java_checkstyle.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/javascript.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**JAVASCRIPT**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/javascript.md#readme) | [eslint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/javascript_eslint.md#readme)| [JAVASCRIPT_ES](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/javascript_eslint.md#readme)| :heavy_check_mark: |
| <!-- --> <!-- linter-icon --> |  | [standard](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/javascript_standard.md#readme)| [JAVASCRIPT_STANDARD](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/javascript_standard.md#readme)| :heavy_check_mark: |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/jsx.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**JSX**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/jsx.md#readme) | [eslint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/jsx_eslint.md#readme)| [JSX_ESLINT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/jsx_eslint.md#readme)| :heavy_check_mark: |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/kotlin.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**KOTLIN**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/kotlin.md#readme) | [ktlint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/kotlin_ktlint.md#readme)| [KOTLIN_KTLINT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/kotlin_ktlint.md#readme)| :heavy_check_mark: |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/lua.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**LUA**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/lua.md#readme) | [luacheck](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/lua_luacheck.md#readme)| [LUA_LUACHECK](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/lua_luacheck.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/perl.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**PERL**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/perl.md#readme) | [perlcritic](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/perl_perlcritic.md#readme)| [PERL_PERLCRITIC](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/perl_perlcritic.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/php.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**PHP**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/php.md#readme) | [php](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/php_php.md#readme)| [PHP_BUILTIN](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/php_php.md#readme)|  |
| <!-- --> <!-- linter-icon --> |  | [phpcs](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/php_phpcs.md#readme)| [PHP_PHPCS](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/php_phpcs.md#readme)|  |
| <!-- --> <!-- linter-icon --> |  | [phpstan](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/php_phpstan.md#readme)| [PHP_PHPSTAN](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/php_phpstan.md#readme)|  |
| <!-- --> <!-- linter-icon --> |  | [psalm](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/php_psalm.md#readme)| [PHP_PSALM](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/php_psalm.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/powershell.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**POWERSHELL**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/powershell.md#readme) | [powershell](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/powershell_powershell.md#readme)| [POWERSHELL_POWERSHELL](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/powershell_powershell.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/python.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**PYTHON**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/python.md#readme) | [pylint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/python_pylint.md#readme)| [PYTHON_PYLINT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/python_pylint.md#readme)|  |
| <!-- --> <!-- linter-icon --> |  | [black](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/python_black.md#readme)| [PYTHON_BLACK](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/python_black.md#readme)| :heavy_check_mark: |
| <!-- --> <!-- linter-icon --> |  | [flake8](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/python_flake8.md#readme)| [PYTHON_FLAKE8](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/python_flake8.md#readme)|  |
| <!-- --> <!-- linter-icon --> |  | [isort](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/python_isort.md#readme)| [PYTHON_ISORT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/python_isort.md#readme)| :heavy_check_mark: |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/r.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**R**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/r.md#readme) | [lintr](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/r_lintr.md#readme)| [R_LINTR](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/r_lintr.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/raku.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**RAKU**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/raku.md#readme) | [raku](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/raku_raku.md#readme)| [RAKU_RAKU](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/raku_raku.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/ruby.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**RUBY**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/ruby.md#readme) | [rubocop](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/ruby_rubocop.md#readme)| [RUBY_RUBOCOP](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/ruby_rubocop.md#readme)| :heavy_check_mark: |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/rust.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**RUST**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/rust.md#readme) | [clippy](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/rust_clippy.md#readme)| [RUST_CLIPPY](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/rust_clippy.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/salesforce.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**SALESFORCE**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/salesforce.md#readme) | [sfdx-scanner](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/salesforce_sfdx_scanner.md#readme)| [SALESFORCE_SFDX_SCANNER](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/salesforce_sfdx_scanner.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/scala.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**SCALA**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/scala.md#readme) | [scalafix](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/scala_scalafix.md#readme)| [SCALA_SCALAFIX](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/scala_scalafix.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/sql.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**SQL**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/sql.md#readme) | [sql-lint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/sql_sql_lint.md#readme)| [SQL_SQL_LINT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/sql_sql_lint.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/tsx.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**TSX**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/tsx.md#readme) | [eslint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/tsx_eslint.md#readme)| [TSX_ESLINT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/tsx_eslint.md#readme)| :heavy_check_mark: |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/typescript.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**TYPESCRIPT**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/typescript.md#readme) | [eslint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/typescript_eslint.md#readme)| [TYPESCRIPT_ES](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/typescript_eslint.md#readme)| :heavy_check_mark: |
| <!-- --> <!-- linter-icon --> |  | [standard](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/typescript_standard.md#readme)| [TYPESCRIPT_STANDARD](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/typescript_standard.md#readme)| :heavy_check_mark: |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/vbdotnet.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**Visual Basic .NET** (VBDOTNET)](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/vbdotnet.md#readme) | [dotnet-format](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/vbdotnet_dotnet_format.md#readme)| [VBDOTNET_DOTNET_FORMAT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/vbdotnet_dotnet_format.md#readme)| :heavy_check_mark: |

### Formats

| <!-- --> | Format | Linter | Configuration key | Fix |
| :---: | ----------------- | -------------- | ------------ | ------- |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/css.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**CSS**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/css.md#readme) | [stylelint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/css_stylelint.md#readme)| [CSS_STYLELINT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/css_stylelint.md#readme)| :heavy_check_mark: |
| <!-- --> <!-- linter-icon --> |  | [scss-lint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/css_scss_lint.md#readme)| [CSS_SCSS_LINT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/css_scss_lint.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/env.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**ENV**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/env.md#readme) | [dotenv-linter](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/env_dotenv_linter.md#readme)| [ENV_DOTENV_LINTER](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/env_dotenv_linter.md#readme)| :heavy_check_mark: |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/graphql.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**GRAPHQL**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/graphql.md#readme) | [graphql-schema-linter](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/graphql_graphql_schema_linter.md#readme)| [GRAPHQL_GRAPHQL_SCHEMA_LINTER](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/graphql_graphql_schema_linter.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/html.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**HTML**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/html.md#readme) | [htmlhint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/html_htmlhint.md#readme)| [HTML_HTMLHINT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/html_htmlhint.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/json.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**JSON**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/json.md#readme) | [jsonlint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/json_jsonlint.md#readme)| [JSON_JSONLINT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/json_jsonlint.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/latex.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**LATEX**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/latex.md#readme) | [chktex](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/latex_chktex.md#readme)| [LATEX_CHKTEX](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/latex_chktex.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/markdown.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**MARKDOWN**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/markdown.md#readme) | [markdownlint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/markdown_markdownlint.md#readme)| [MARKDOWN_MARKDOWNLINT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/markdown_markdownlint.md#readme)| :heavy_check_mark: |
| <!-- --> <!-- linter-icon --> |  | [markdown-link-check](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/markdown_markdown_link_check.md#readme)| [MARKDOWN_MARKDOWN_LINK_CHECK](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/markdown_markdown_link_check.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/protobuf.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**PROTOBUF**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/protobuf.md#readme) | [protolint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/protobuf_protolint.md#readme)| [PROTOBUF_PROTOLINT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/protobuf_protolint.md#readme)| :heavy_check_mark: |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/rst.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**RST**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/rst.md#readme) | [rst-lint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/rst_rst_lint.md#readme)| [RST_RST_LINT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/rst_rst_lint.md#readme)|  |
| <!-- --> <!-- linter-icon --> |  | [rstcheck](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/rst_rstcheck.md#readme)| [RST_RSTCHECK](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/rst_rstcheck.md#readme)|  |
| <!-- --> <!-- linter-icon --> |  | [rstfmt](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/rst_rstfmt.md#readme)| [RST_RSTFMT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/rst_rstfmt.md#readme)| :heavy_check_mark: |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/xml.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**XML**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/xml.md#readme) | [xmllint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/xml_xmllint.md#readme)| [XML_XMLLINT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/xml_xmllint.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/yaml.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**YAML**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/yaml.md#readme) | [yamllint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/yaml_yamllint.md#readme)| [YAML_YAMLLINT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/yaml_yamllint.md#readme)|  |

### Tooling formats

| <!-- --> | Tooling format | Linter | Configuration key | Fix |
| :---: | ----------------- | -------------- | ------------ | ------- |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/ansible.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**ANSIBLE**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/ansible.md#readme) | [ansible-lint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/ansible_ansible_lint.md#readme)| [ANSIBLE_ANSIBLE_LINT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/ansible_ansible_lint.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/arm.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**ARM**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/arm.md#readme) | [arm-ttk](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/arm_arm_ttk.md#readme)| [ARM_ARM_TTK](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/arm_arm_ttk.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/cloudformation.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**CLOUDFORMATION**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/cloudformation.md#readme) | [cfn-lint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/cloudformation_cfn_lint.md#readme)| [CLOUDFORMATION_CFN_LINT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/cloudformation_cfn_lint.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/dockerfile.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**DOCKERFILE**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/dockerfile.md#readme) | [dockerfilelint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/dockerfile_dockerfilelint.md#readme)| [DOCKERFILE_DOCKERFILELINT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/dockerfile_dockerfilelint.md#readme)|  |
| <!-- --> <!-- linter-icon --> |  | [hadolint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/dockerfile_hadolint.md#readme)| [DOCKERFILE_HADOLINT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/dockerfile_hadolint.md#readme)|  |
| <!-- --> <!-- linter-icon --> |  | [docker-label-inspector](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/dockerfile_docker_label_inspector.md#readme)| [DOCKERFILE_DLI](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/dockerfile_docker_label_inspector.md#readme)|  |
| <!-- --> <!-- linter-icon --> |  | [docker-label-inspector-validate](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/dockerfile_docker_label_inspector_validate.md#readme)| [DOCKERFILE_DLI_VALIDATE](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/dockerfile_docker_label_inspector_validate.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/editorconfig.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**EDITORCONFIG**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/editorconfig.md#readme) | [editorconfig-checker](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/editorconfig_editorconfig_checker.md#readme)| [EDITORCONFIG_EDITORCONFIG_CHECKER](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/editorconfig_editorconfig_checker.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/gherkin.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**GHERKIN**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/gherkin.md#readme) | [gherkin-lint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/gherkin_gherkin_lint.md#readme)| [GHERKIN_GHERKIN_LINT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/gherkin_gherkin_lint.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/kubernetes.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**KUBERNETES**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/kubernetes.md#readme) | [kubeval](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/kubernetes_kubeval.md#readme)| [KUBERNETES_KUBEVAL](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/kubernetes_kubeval.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/openapi.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**OPENAPI**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/openapi.md#readme) | [spectral](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/openapi_spectral.md#readme)| [OPENAPI_SPECTRAL](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/openapi_spectral.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/puppet.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**PUPPET**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/puppet.md#readme) | [puppet-lint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/puppet_puppet_lint.md#readme)| [PUPPET_PUPPET_LINT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/puppet_puppet_lint.md#readme)| :heavy_check_mark: |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/snakemake.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**SNAKEMAKE**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/snakemake.md#readme) | [snakemake](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/snakemake_snakemake.md#readme)| [SNAKEMAKE_LINT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/snakemake_snakemake.md#readme)|  |
| <!-- --> <!-- linter-icon --> |  | [snakefmt](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/snakemake_snakefmt.md#readme)| [SNAKEMAKE_SNAKEFMT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/snakemake_snakefmt.md#readme)| :heavy_check_mark: |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/tekton.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**TEKTON**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/tekton.md#readme) | [tekton-lint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/tekton_tekton_lint.md#readme)| [TEKTON_TEKTON_LINT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/tekton_tekton_lint.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/terraform.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**TERRAFORM**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/terraform.md#readme) | [tflint](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/terraform_tflint.md#readme)| [TERRAFORM_TFLINT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/terraform_tflint.md#readme)|  |
| <!-- --> <!-- linter-icon --> |  | [terrascan](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/terraform_terrascan.md#readme)| [TERRAFORM_TERRASCAN](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/terraform_terrascan.md#readme)|  |
| <!-- --> <!-- linter-icon --> |  | [terragrunt](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/terraform_terragrunt.md#readme)| [TERRAFORM_TERRAGRUNT](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/terraform_terragrunt.md#readme)|  |

### Other

| <!-- --> | Code quality checker | Linter | Configuration key | Fix |
| :---: | ----------------- | -------------- | ------------ | ------- |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/copypaste.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**COPYPASTE**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/copypaste.md#readme) | [jscpd](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/copypaste_jscpd.md#readme)| [COPYPASTE_JSCPD](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/copypaste_jscpd.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/git.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**GIT**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/git.md#readme) | [git_diff](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/git_git_diff.md#readme)| [GIT_GIT_DIFF](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/git_git_diff.md#readme)|  |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/spell.ico" alt="" height="32px" class="megalinter-icon"></a> <!-- linter-icon --> | [**SPELL**](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/spell.md#readme) | [cspell](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/spell_cspell.md#readme)| [SPELL_CSPELL](https://github.com/nvuillam/mega-linter/tree/master/docs/descriptors/spell_cspell.md#readme)|  |

<!-- linters-table-end -->
<!-- supported-linters-section-end -->

<!-- installation-section-start -->
## Installation

The following instructions examples are using to latest Mega-Linter stable version (**V4** , always corresponding to the [latest release](https://github.com/nvuillam/mega-linter/releases)

- GitHub Action: nvuillam/mega-linter:v4
- Docker image: nvuillam/mega-linter@v4

You can also use **insiders** version (beta release, corresponding to the content of master branch)

- GitHub Action: nvuillam/mega-linter:insiders
- Docker image: nvuillam/mega-linter@latest

### GitHub Action

1. Create a new file in your repository called `.github/workflows/mega-linter.yml`
2. Copy the [example workflow from below](https://raw.githubusercontent.com/nvuillam/mega-linter/master/TEMPLATES/mega-linter.yml) into that new file, no extra configuration required
3. Commit that file to a new branch
4. Open up a pull request and observe the action working
5. Enjoy your more _stable_, and _cleaner_ code base

**NOTES:**

- If you pass the _Environment_ variable `GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}` in your workflow, then the **GitHub Mega-Linter** will mark the status of each individual linter run in the Checks section of a pull request. Without this you will only see the overall status of the full run. There is no need to set the **GitHub** Secret as it is automatically set by GitHub, it only needs to be passed to the action.
- You can also **use it outside of GitHub Actions** (CircleCI, Azure Pipelines, Jenkins, GitLab, or even locally with a docker run)

In your repository you should have a `.github/workflows` folder with **GitHub** Action similar to below:

- `.github/workflows/mega-linter.yml`

This file should have the following code:

```yml
---
# Mega-Linter GitHub Action configuration file
# More info at https://nvuillam.github.io/mega-linter
name: Mega-Linter

on:
  # Trigger mega-linter at every push. Action will also be visible from Pull Requests to master
  push: # Comment this line to trigger action only on pull-requests (not recommended if you don't pay for GH Actions)
  pull_request:
    branches: [master, main]

env: # Comment env block if you do not want to apply fixes
  # Apply linter fixes configuration
  APPLY_FIXES: all # When active, APPLY_FIXES must also be defined as environment variable (in github/workflows/mega-linter.yml or other CI tool)
  APPLY_FIXES_EVENT: pull_request # Decide which event triggers application of fixes in a commit or a PR (pull_request, push, all)
  APPLY_FIXES_MODE: commit # If APPLY_FIXES is used, defines if the fixes are directly committed (commit) or posted in a PR (pull_request)

jobs:
  # Cancel duplicate jobs: https://github.com/fkirc/skip-duplicate-actions#option-3-cancellation-only
  cancel_duplicates:
    name: Cancel duplicate jobs
    runs-on: ubuntu-latest
    steps:
      - uses: fkirc/skip-duplicate-actions@master
        with:
          github_token: ${{ secrets.PAT || secrets.GITHUB_TOKEN }}

  build:
    name: Mega-Linter
    runs-on: ubuntu-latest
    steps:
      # Git Checkout
      - name: Checkout Code
        uses: actions/checkout@v2
        with:
          token: ${{ secrets.PAT || secrets.GITHUB_TOKEN }}
          fetch-depth: 0

      # Mega-Linter
      - name: Mega-Linter
        id: ml
        # You can override Mega-Linter flavor used to have faster performances
        # More info at https://nvuillam.github.io/mega-linter/flavors/
        uses: nvuillam/mega-linter@v4
        env:
          # All available variables are described in documentation
          # https://nvuillam.github.io/mega-linter/configuration/
          VALIDATE_ALL_CODEBASE: ${{ github.event_name == 'push' && github.ref == 'refs/heads/master' }} # Validates all source when push on master, else just the git diff with master. Override with true if you always want to lint all sources
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          # ADD YOUR CUSTOM ENV VARIABLES HERE OR DEFINE THEM IN A FILE .mega-linter.yml AT THE ROOT OF YOUR REPOSITORY
          # DISABLE: COPYPASTE,SPELL # Uncomment to disable copy-paste and spell checks

      # Upload Mega-Linter artifacts
      - name: Archive production artifacts
        if: ${{ success() }} || ${{ failure() }}
        uses: actions/upload-artifact@v2
        with:
          name: Mega-Linter reports
          path: |
            report
            mega-linter.log

      # Create pull request if applicable (for now works only on PR from same repository, not from forks)
      - name: Create Pull Request with applied fixes
        id: cpr
        if: steps.ml.outputs.has_updated_sources == 1 && (env.APPLY_FIXES_EVENT == 'all' || env.APPLY_FIXES_EVENT == github.event_name) && env.APPLY_FIXES_MODE == 'pull_request' && github.event.pull_request.head.repo.full_name == github.repository
        uses: peter-evans/create-pull-request@v3
        with:
          token: ${{ secrets.PAT || secrets.GITHUB_TOKEN }}
          commit-message: "[Mega-Linter] Apply linters automatic fixes"
          title: "[Mega-Linter] Apply linters automatic fixes"
          labels: bot
      - name: Create PR output
        if: steps.ml.outputs.has_updated_sources == 1 && (env.APPLY_FIXES_EVENT == 'all' || env.APPLY_FIXES_EVENT == github.event_name) && env.APPLY_FIXES_MODE == 'pull_request' && github.event.pull_request.head.repo.full_name == github.repository
        run: |
          echo "Pull Request Number - ${{ steps.cpr.outputs.pull-request-number }}"
          echo "Pull Request URL - ${{ steps.cpr.outputs.pull-request-url }}"

      # Push new commit if applicable (for now works only on PR from same repository, not from forks)
      - name: Prepare commit
        if: steps.ml.outputs.has_updated_sources == 1 && (env.APPLY_FIXES_EVENT == 'all' || env.APPLY_FIXES_EVENT == github.event_name) && env.APPLY_FIXES_MODE == 'commit' && github.ref != 'refs/heads/master' && github.event.pull_request.head.repo.full_name == github.repository
        run: sudo chown -Rc $UID .git/
      - name: Commit and push applied linter fixes
        if: steps.ml.outputs.has_updated_sources == 1 && (env.APPLY_FIXES_EVENT == 'all' || env.APPLY_FIXES_EVENT == github.event_name) && env.APPLY_FIXES_MODE == 'commit' && github.ref != 'refs/heads/master' && github.event.pull_request.head.repo.full_name == github.repository
        uses: stefanzweifel/git-auto-commit-action@v4
        with:
          branch: ${{ github.event.pull_request.head.ref || github.head_ref || github.ref }}
          commit_message: "[Mega-Linter] Apply linters fixes"
```

### Azure

Use the following Azure workflow template

You may activate [File.io reporter](https://nvuillam.github.io/mega-linter/reporters/FileIoReporter/) or [E-mail reporter](https://nvuillam.github.io/mega-linter/reporters/EmailReporter/) to access detailed logs and fixed source

```yaml
  - job: megalinter
    displayName: Mega-Linter
    pool:
      vmImage: ubuntu-latest
    steps:
    - script: |
        docker pull nvuillam/mega-linter:v4
        docker run -v $(System.DefaultWorkingDirectory):/tmp/lint nvuillam/mega-linter
      displayName: 'Code Scan using  Mega-Linter'
```

### Jenkins

Add the following stage in your Jenkinsfile

You may activate [File.io reporter](https://nvuillam.github.io/mega-linter/reporters/FileIoReporter/) or [E-mail reporter](https://nvuillam.github.io/mega-linter/reporters/EmailReporter/) to access detailed logs and fixed source

```groovy
// Lint with Mega-Linter: https://nvuillam.github.io/mega-linter/
stage('Mega-Linter') {
    agent {
        docker {
            image 'nvuillam/mega-linter:v4'
            args "-e VALIDATE_ALL_CODEBASE=true -v ${WORKSPACE}:/tmp/lint --entrypoint=''"
            reuseNode true
        }
    }
    steps {
        sh '/entrypoint.sh'
    }
}
```

### GitLab

Example of configuration using GitLab CI

You may activate [File.io reporter](https://nvuillam.github.io/mega-linter/reporters/FileIoReporter/) or [E-mail reporter](https://nvuillam.github.io/mega-linter/reporters/EmailReporter/) to access detailed logs and fixed source

```yaml
megalinter:
  stage: linting
  image: nvuillam/mega-linter:v4
  script: [ "true" ]
  variables:
    DEFAULT_WORKSPACE: $CI_BUILDS_DIR
    ANSIBLE_DIRECTORY: $CI_PROJECT_PATH
    LINTER_RULES_PATH: $CI_PROJECT_PATH/.github/linters
```

### Run Mega-Linter locally

You can use [mega-linter-runner](https://nvuillam.github.io/mega-linter/mega-linter-runner/) to locally run Mega-Linter with the same configuration defined in [.mega-linter.yml](#configuration) file

See [mega-linter-runner installation instructions](https://nvuillam.github.io/mega-linter/mega-linter-runner/#installation)
<!-- installation-section-end -->

<!-- configuration-section-start -->
## Configuration

Mega-Linter configuration variables can be defined with **environment variables** or in a **.mega-linter.yml** file at the root of the repository.
You can see an example config file in this repo: [**.mega-linter.yml**](https://github.com/nvuillam/mega-linter/blob/master/.mega-linter.yml)

### Activation and deactivation

Mega-Linter have all linters enabled by default, but allows to enable only some, or disable only some

- If `ENABLE` is not set, all descriptors are activated by default. If set, all linters of listed descriptors will be activated by default
- If `ENABLE_LINTERS` is set, only listed linters will be processed
- If `DISABLE` is set, the linters in the listed descriptors will be skipped
- If `DISABLE_LINTERS` is set, the listed linters will be skipped

Examples:

- Run all javascript and groovy linters except STANDARD javascript linter

```yaml
ENABLE: JAVASCRIPT,GROOVY
DISABLE_LINTERS: JAVSCRIPT_STANDARD
```

- Run all linters except PHP linters (PHP_BUILTIN, PHP_PCPCS, PHP_STAN, PHP_PSALM)

```yaml
DISABLE: PHP
```

- Run all linters except PHP_STAN and PHP_PSALM linters

```yaml
DISABLE_LINTERS: PHP_STAN,PHP_PSALM
```

### Apply fixes

Mega-linter is able to apply fixes provided by linters. To use this capability, you need 3 **env variables** defined at top level

- **APPLY_FIXES**: `all` to apply fixes of all linters, or a list of linter keys (ex: `JAVASCRIPT_ES`,`MARKDOWN_MARKDOWNLINT`)
- **APPLY_FIXES_EVENT**: `all`, `push`, `pull_request`, `none` _(use none in case of use of [Updated sources reporter](https://github.com/nvuillam/mega-linter/tree/master/docs/reporters/UpdatedSourcesReporter.md))_
- **APPLY_FIXES_MODE**: `commit` to create a new commit and push it on the same branch, or `pull_request` to create a new PR targeting the branch.

Notes:

- You can use [**Updated sources reporter**](https://github.com/nvuillam/mega-linter/tree/master/docs/reporters/UpdatedSourcesReporter.md) if you do not want fixes to be automatically applied on git branch, but **download them in a zipped file** and manually **extract them in your project**
- If used, **APPLY_FIXES_EVENT** and **APPLY_FIXES_MODE** can not be defined in `.mega-linter.yml`config file, they must be set as environment variables
- If you use **APPLY_FIXES**, add the following line in your `.gitignore file`

```shell
report/
```

- You may see **github permission errors**, or workflows not run on the new commit. To solve these issues:
  - [Create Personal Access Token](https://docs.github.com/en/free-pro-team@latest/github/authenticating-to-github/creating-a-personal-access-token#creating-a-token), then copy the PAT value
  - [Define secret variable](https://docs.github.com/en/free-pro-team@latest/actions/reference/encrypted-secrets#creating-encrypted-secrets-for-a-repository) named **PAT** on your repository, and paste the PAT value

### Shared variables

| **ENV VAR**                         | **Default Value**            | **Notes**                                                                                                                                                                        |
| ----------------------------------- | ---------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ADDITIONAL_EXCLUDED_DIRECTORIES** | \[\]                         | List of additional excluded directory basenames. They are excluded at any nested level.                                                                                          |
| **DEFAULT_BRANCH**                  | `master`                     | The name of the repository default branch. Warning: In new github repositories, master branch is named `main`, so you need to override this value with `main`                    |
| **DEFAULT_WORKSPACE**               | `/tmp/lint`                  | The location containing files to lint if you are running locally.                                                                                                                |
| **DISABLE_ERRORS**                  | `false`                      | Flag to have the linter complete with exit code 0 even if errors were detected.                                                                                                  |
| **EXCLUDED_DIRECTORIES**            | \[...many values...\]        | List of excluded directory basenames. They are excluded at any nested level.                                                                                                     |
| **FILTER_REGEX_EXCLUDE**            | `none`                       | Regular expression defining which files will be excluded from linting  (ex: `.*src/test.*`)                                                                                      |
| **FILTER_REGEX_INCLUDE**            | `all`                        | Regular expression defining which files will be processed by linters (ex: `.*src/.*`)                                                                                            |
| **FLAVOR_SUGGESTIONS**              | `true`                       | Provides suggestions about different Mega-Linter flavors to use to improve runtime performances                                                                                  |
| **GITHUB_WORKSPACE**                | ``                           | Base directory for `REPORT_OUTPUT_FOLDER`, for user-defined linter rules location, for location of linted files if `DEFAULT_WORKSPACE` is not set                                |
| **LINTER_RULES_PATH**               | `.github/linters`            | Directory for all linter configuration rules.<br/> Can be a local folder or a remote URL (ex: `https://raw.githubusercontent.com/some_org/some_repo/mega-linter-rules` )         |
| **LOG_FILE**                        | `mega-linter.log`            | The file name for outputting logs. All output is sent to the log file regardless of `LOG_LEVEL`.                                                                                 |
| **LOG_LEVEL**                       | `INFO`                       | How much output the script will generate to the console. One of `INFO`, `DEBUG`, `WARNING` or `ERROR`.                                                                           |
| **OUTPUT_FOLDER**                   | `report`                     | The location where the output reporting will be generated to.                                                                                                                    |
| **PARALLEL**                        | `true`                       | Process linters in parallel to improve overall Mega-Linter performance. If true, linters of same language or formats are grouped in the same parallel process to avoid lock issues if fixing the same files |
| **PRINT_ALPACA**                    | `true`                       | Enable printing alpaca image to console                                                                                                                                          |
| **REPORT_OUTPUT_FOLDER**            | `${GITHUB_WORKSPACE}/report` | Directory for generating report files                                                                                                                                            |
| **SHOW_ELAPSED_TIME**               | `false`                      | Displays elapsed time in reports                                                                                                                                                 |
| **VALIDATE_ALL_CODEBASE**           | `true`                       | Will parse the entire repository and find all files to validate across all types. **NOTE:** When set to `false`, only **new** or **edited** files will be parsed for validation. |

### Filter linted files

If you need to lint only a folder or exclude some files from linting, you can use optional environment parameters `FILTER_REGEX_INCLUDE` and `FILTER_REGEX_EXCLUDE`
You can apply filters to a single linter by defining variable `<LINTER_KEY>_FILTER_REGEX_INCLUDE` and `<LINTER_KEY>_FILTER_REGEX_EXCLUDE`

Examples:

- Lint only src folder: `FILTER_REGEX_INCLUDE: (src/)`
- Do not lint files inside test and example folders: `FILTER_REGEX_EXCLUDE: (test/|examples/)`
- Do not lint javascript files inside test folder: `FILTER_REGEX_EXCLUDE: (test/.*\.js)`

### Linter specific variables

See linters specific variables in their [Mega-Linter documentation](#languages)

### Template rules files

You can use the **Mega-Linter** _with_ or _without_ your own personal rules sets. This allows for greater flexibility for each individual code base. The Template rules all try to follow the standards we believe should be enabled at the basic level.

- Copy **any** or **all** template rules files from `TEMPLATES/` into your repository in the location: `.github/linters/` of your repository
  - If your repository does not have rules files, they will fall back to defaults in [this repository's `TEMPLATE` folder](https://github.com/nvuillam/mega-linter/tree/master/TEMPLATES), or to linter defaults
<!-- configuration-section-end -->

<!-- reporters-section-start -->
## Reporters

Mega-Linter can generate various reports that you can activate / deactivate and customize

| Reporter |  Description | Default |
| -------- |  ----------- | ------- |
| [Text files](https://github.com/nvuillam/mega-linter/tree/master/docs/reporters/TextReporter.md) |  One log file by linter + suggestions for fixes that can not be automated | Active |
| [Pull Request comments](https://github.com/nvuillam/mega-linter/tree/master/docs/reporters/GitHubCommentReporter.md) | Mega-Linter posts a comment on the PR with a summary of lint results, and links to detailed logs | Active if GitHub Action |
| [Updated sources](https://github.com/nvuillam/mega-linter/tree/master/docs/reporters/UpdatedSourcesReporter.md) | Zip containing all formatted and auto-fixed sources so you can extract them in your repository | Active |
| [GitHub Status](https://github.com/nvuillam/mega-linter/tree/master/docs/reporters/GitHubStatusReporter.md) | One GitHub status by linter on the PR, with links to detailed logs | Active if GitHub Action |
| [File.io](https://github.com/nvuillam/mega-linter/tree/master/docs/reporters/FileIoReporter.md) | Send reports on file.io so you can access them with a simple hyperlink provided at the end of console log | Inactive |
| [Email](https://github.com/nvuillam/mega-linter/tree/master/docs/reporters/EmailReporter.md) | Receive all reports on your e-mail, if you can not use artifacts | Active |
| [TAP files](https://github.com/nvuillam/mega-linter/tree/master/docs/reporters/TapReporter.md) | One log file by linter following [Test Anything Protocol](https://testanything.org/) format | Active |
| [Console](https://github.com/nvuillam/mega-linter/tree/master/docs/reporters/ConsoleReporter.md) | Execution logs visible in console | Active |
<!-- reporters-section-end -->

<!-- flavors-section-start -->
## Flavors

_This capability is in **Beta version**_

To improve run performances, we generate **Flavored Mega-Linter images** containing only the list of linters related to a project type

- When using default Mega-Linter, if a Mega-Linter Flavor would cover all your project requirements, a message is added in the logs
- If your project uses a Mega-Linter Flavor not covering linter requirements, an error message will be thrown with instructions about how to solve the issue

<!-- flavors-table-start -->
| <!-- --> | Flavor | Description | Embedded linters | Info |
| :------: | :----- | :---------- | :--------------: | ---: |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/images/mega-linter-square.png" alt="" height="32px" class="megalinter-icon"></a> | [all](https://nvuillam.github.io/mega-linter/supported-linters/) | Default Mega-Linter Flavor | 74 | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/nvuillam/mega-linter/v4) ![Docker Pulls](https://img.shields.io/docker/pulls/nvuillam/mega-linter) |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/dart.ico" alt="" height="32px" class="megalinter-icon"></a> | [dart](https://github.com/nvuillam/mega-linter/tree/master/docs/flavors/dart.md#readme) | Mega-Linter optimized for DART based projects | 32 | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/nvuillam/mega-linter-dart/v4) ![Docker Pulls](https://img.shields.io/docker/pulls/nvuillam/mega-linter-dart) |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/dotnet.ico" alt="" height="32px" class="megalinter-icon"></a> | [dotnet](https://github.com/nvuillam/mega-linter/tree/master/docs/flavors/dotnet.md#readme) | Mega-Linter optimized for C, C++, C# or VB based projects | 37 | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/nvuillam/mega-linter-dotnet/v4) ![Docker Pulls](https://img.shields.io/docker/pulls/nvuillam/mega-linter-dotnet) |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/go.ico" alt="" height="32px" class="megalinter-icon"></a> | [go](https://github.com/nvuillam/mega-linter/tree/master/docs/flavors/go.md#readme) | Mega-Linter optimized for GO based projects | 32 | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/nvuillam/mega-linter-go/v4) ![Docker Pulls](https://img.shields.io/docker/pulls/nvuillam/mega-linter-go) |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/java.ico" alt="" height="32px" class="megalinter-icon"></a> | [java](https://github.com/nvuillam/mega-linter/tree/master/docs/flavors/java.md#readme) | Mega-Linter optimized for JAVA based projects | 32 | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/nvuillam/mega-linter-java/v4) ![Docker Pulls](https://img.shields.io/docker/pulls/nvuillam/mega-linter-java) |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/javascript.ico" alt="" height="32px" class="megalinter-icon"></a> | [javascript](https://github.com/nvuillam/mega-linter/tree/master/docs/flavors/javascript.md#readme) | Mega-Linter optimized for JAVASCRIPT or TYPESCRIPT based projects | 38 | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/nvuillam/mega-linter-javascript/v4) ![Docker Pulls](https://img.shields.io/docker/pulls/nvuillam/mega-linter-javascript) |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/php.ico" alt="" height="32px" class="megalinter-icon"></a> | [php](https://github.com/nvuillam/mega-linter/tree/master/docs/flavors/php.md#readme) | Mega-Linter optimized for PHP based projects | 35 | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/nvuillam/mega-linter-php/v4) ![Docker Pulls](https://img.shields.io/docker/pulls/nvuillam/mega-linter-php) |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/python.ico" alt="" height="32px" class="megalinter-icon"></a> | [python](https://github.com/nvuillam/mega-linter/tree/master/docs/flavors/python.md#readme) | Mega-Linter optimized for PYTHON based projects | 38 | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/nvuillam/mega-linter-python/v4) ![Docker Pulls](https://img.shields.io/docker/pulls/nvuillam/mega-linter-python) |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/ruby.ico" alt="" height="32px" class="megalinter-icon"></a> | [ruby](https://github.com/nvuillam/mega-linter/tree/master/docs/flavors/ruby.md#readme) | Mega-Linter optimized for RUBY based projects | 32 | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/nvuillam/mega-linter-ruby/v4) ![Docker Pulls](https://img.shields.io/docker/pulls/nvuillam/mega-linter-ruby) |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/rust.ico" alt="" height="32px" class="megalinter-icon"></a> | [rust](https://github.com/nvuillam/mega-linter/tree/master/docs/flavors/rust.md#readme) | Mega-Linter optimized for RUST based projects | 32 | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/nvuillam/mega-linter-rust/v4) ![Docker Pulls](https://img.shields.io/docker/pulls/nvuillam/mega-linter-rust) |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/scala.ico" alt="" height="32px" class="megalinter-icon"></a> | [scala](https://github.com/nvuillam/mega-linter/tree/master/docs/flavors/scala.md#readme) | Mega-Linter optimized for SCALA based projects | 32 | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/nvuillam/mega-linter-scala/v4) ![Docker Pulls](https://img.shields.io/docker/pulls/nvuillam/mega-linter-scala) |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/terraform.ico" alt="" height="32px" class="megalinter-icon"></a> | [terraform](https://github.com/nvuillam/mega-linter/tree/master/docs/flavors/terraform.md#readme) | Mega-Linter optimized for TERRAFORM based projects | 34 | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/nvuillam/mega-linter-terraform/v4) ![Docker Pulls](https://img.shields.io/docker/pulls/nvuillam/mega-linter-terraform) |
<!-- flavors-table-end -->

<!-- flavors-section-end -->

<!-- badge-section-start -->
## Badge

You can show Mega-Linter status with a badge in your repository README

[![Mega-Linter](https://github.com/nvuillam/mega-linter/workflows/Mega-Linter/badge.svg?branch=master)](https://nvuillam.github.io/mega-linter)

### Markdown

- Format

```markdown
[![Mega-Linter](https://github.com/<OWNER>/<REPOSITORY>/workflows/Mega-Linter/badge.svg?branch=master)](https://nvuillam.github.io/mega-linter)
```

- Example

```markdown
[![Mega-Linter](https://github.com/nvuillam/npm-groovy-lint/workflows/Mega-Linter/badge.svg?branch=master)](https://nvuillam.github.io/mega-linter)
```

### reStructuredText

- Format

```markdown
.. |Mega-Linter yes| image:: https://github.com/<OWNER>/<REPOSITORY>/workflows/Mega-Linter/badge.svg?branch=master
   :target: https://nvuillam.github.io/mega-linter
```

- Example

```markdown
.. |Mega-Linter yes| image:: https://github.com/nvuillam/npm-groovy-lint/workflows/Mega-Linter/badge.svg?branch=master
   :target: https://nvuillam.github.io/mega-linter
```

_Note:_ IF you did not use `Mega-Linter` as GitHub Action name, please read [GitHub Actions Badges documentation](https://docs.github.com/en/actions/configuring-and-managing-workflows/configuring-a-workflow#adding-a-workflow-status-badge-to-your-repository)
<!-- badge-section-end -->

<!-- how-to-contribute-section-start -->
## How to contribute

Contributions to Mega-Linter are very welcome, please follow [Contributing Guide](https://github.com/nvuillam/mega-linter/blob/master/.github/CONTRIBUTING.md)

You can also [report problems and request new features](https://github.com/nvuillam/mega-linter/issues), or just [:star: star the repository](https://github.com/nvuillam/mega-linter/stargazers) and [share it on twitter](http://twitter.com/intent/tweet/?text=Mega-Linter:%2070%20linters%20aggregator%20easy%20to%20use%20for%20all%20your%20projects&url=http://nvuillam.github.io/mega-linter&via=nvuillam)
<!-- how-to-contribute-section-end -->

---
<!-- license-section-start -->
## License

- [MIT License](https://github.com/nvuillam/mega-linter/blob/master/LICENSE)
<!-- license-section-end -->

<!-- mega-linter-vs-super-linter-section-start -->
## Mega-Linter vs Super-Linter

The hard-fork of Super-Linter to be rewritten in Python is not just a language switch: use of python flexibility and libraries allowed to define lots of additional functions

### More languages and formats linted

- **C**, **C++**, **Copy-Paste detection**, **GraphQL**, **Puppet**, **reStructuredText**, **Rust**, **Scala**, **Spell checker**, **Visual Basic .NET**

### Performances

- [Mega-Linter Flavors](#flavors) allow to use **smaller docker images**, so the pull time is reduced
- Thanks to python multiprocessing capabilities, **linters are run in parallel**, which is way faster than Super-Linter bash script who runs all linters in sequence

### Automatically apply formatting and fixes

Mega-Linter can [**automatically apply fixes performed by linters**](#apply-fixes), and **push them to the same branch**, or **create a Pull Request** that you can validate

This is pretty handy, especially for linter errors related to formatting (in that case, you don't have any manual update to perform)

### Run locally

Mega-Linter can be run locally thanks to [mega-linter-runner](https://nvuillam.github.io/mega-linter/mega-linter-runner/)

### More reporters

- [Text files](https://github.com/nvuillam/mega-linter/tree/master/docs/reporters/TextReporter.md)
- [Pull Request comments](https://github.com/nvuillam/mega-linter/tree/master/docs/reporters/GitHubCommentReporter.md)
- [Updated sources](https://github.com/nvuillam/mega-linter/tree/master/docs/reporters/UpdatedSourcesReporter.md)
- [Email](https://github.com/nvuillam/mega-linter/tree/master/docs/reporters/EmailReporter.md)
- [File.io](https://github.com/nvuillam/mega-linter/tree/master/docs/reporters/FileIoReporter.md)

### Enhanced Configuration

- Configure **include and exclude regexes** for a **single language or linter**: ex: `JAVASCRIPT_FILTER_REGEX_INCLUDE (src)`
- Configure **additional CLI arguments** for a linter: ex: `JAVASCRIPT_ES_ARGUMENTS "--debug --env-info"`
- Configure **non blocking errors** for a **single language or linter**: ex: `JAVASCRIPT_DISABLE_ERRORS`
- **Simplify languages and linters variables**
  - ENABLE = list of languages and formats to apply lint on codebase (default: all)
  - ENABLE_LINTERS = list of linters to apply lint on codebase (default: all)
  - DISABLE = list of languages and formats to skip (default: none)
  - DISABLE_LINTERS = list of linters to skip (default: none)
  - Variables VALIDATE_XXX are still taken in account (but should not be used in association with ENABLE and DISABLE variables)

### Enhanced Documentation

- [**HTML documentation**](https://nvuillam.github.io/mega-linter/)
- **One page per linter documentation** :
  - **All variables** that can be used with this linter
  - List of **file extensions, names and filters** applied by the linter
  - Link to **Mega-Linter default linter configuration**
  - Link to linter Web-Site
  - Link to official page explaining **how to customize the linter rules**
  - Link to official page explaining **how to disable rules from source comments**
  - **Examples** of linter command line calls behind the hood
  - **Help** command text
  - Installation commands
- README
  - Separate languages, formats and tooling formats in the linters table
  - Add logos for each descriptor

### Enhanced logging and reports

- Show linter version and applied filters for each linter processed
- Reports stored as artefacts on GitHub Action run
  - General log
  - One report file by linter

### Simplify architecture and evolutive maintenance

- Refactoring runtime in Python, for easier handling than bash thanks to [classes](https://github.com/nvuillam/mega-linter/tree/master/megalinter) and python modules
- Everything related to each linter [in a single descriptor YML file](https://github.com/nvuillam/mega-linter/tree/master/megalinter/descriptors)
  - easier evolutive maintenance
  - less conflicts to manage between PRs.
  - Few special cases require a [python linter class](https://github.com/nvuillam/mega-linter/tree/master/megalinter/descriptors))
- [Default behaviours for all linters](https://github.com/nvuillam/mega-linter/blob/master/megalinter/Linter.py), with possibility to override part of them for special cases
- Hierarchical architecture: Apply fixes and new behaviours to all linters with a single code update
- **Documentation as code**
  - Generate linters tables (ordered by type: language, format & tooling format) and include it in README. [(see result)](https://nvuillam.github.io/mega-linter/supported-linters/)
  - Generate one markdown file per Linter, containing all configuration variables, infos and examples [(See examples)](https://nvuillam.github.io/mega-linter/descriptors/javascript_eslint/)
- **Automatic generation of Dockerfile** using YML descriptors, always using the linter latest version
  - Dockerfile commands (FROM, ARG, ENV, COPY, RUN )
  - APK packages (linux)
  - NPM packages (node)
  - PIP packages (python)
  - GEM packages (ruby)
  - Phive packages (PHP)
- Have a centralized exclude list (node_modules,.rbenv, etc...)

### Improve robustness & stability

- [Test classes](https://github.com/nvuillam/mega-linter/blob/master/megalinter/tests/test_megalinter) for each capability
- [Test classes for each linter](https://github.com/nvuillam/mega-linter/tree/master/megalinter/tests/test_megalinter/linters): Automatic generation of test classes using [.automation/build.py](https://github.com/nvuillam/mega-linter/blob/master/.automation/build.py)
- Setup **code coverage** [![codecov](https://codecov.io/gh/nvuillam/mega-linter/branch/master/graph/badge.svg)](https://codecov.io/gh/nvuillam/mega-linter)
- **Development CD / CI**
  - Validate multi-status on PR inside each PR (posted from step "Run against all code base")
  - Run test classes and code coverage with pytest during validation GitHub Action
  - Validate descriptor YML files with json schema during build
  - Automated job to upgrade linters to their latest stable version
<!-- mega-linter-vs-super-linter-section-end -->
