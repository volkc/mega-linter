<!-- markdownlint-disable MD033 MD041 -->
<!-- Generated by .automation/build.py, please do not update manually -->
# git_diff

Git diff checks for git conflicts markers in files

## git_diff documentation

- Version in Mega-Linter: **2.26.2**
- Visit [Official Web Site](https://git-scm.com){target=_blank}

[![git - GitHub](https://gh-card.dev/repos/git/git.svg?fullname=)](https://github.com/git/git){target=_blank}

## Configuration in Mega-Linter

- Enable git_diff by adding `GIT_GIT_DIFF` in [ENABLE_LINTERS variable](/configuration/#activation-and-deactivation)
- Disable git_diff by adding `GIT_GIT_DIFF` in [DISABLE_LINTERS variable](/configuration/#activation-and-deactivation)

| Variable | Description | Default value |
| ----------------- | -------------- | -------------- |
| GIT_GIT_DIFF_ARGUMENTS | User custom arguments to add in linter CLI call<br/>Ex: `-s --foo "bar"` |  |
| GIT_GIT_DIFF_FILTER_REGEX_INCLUDE | Custom regex including filter<br/>Ex: `(src|lib)` | Include every file |
| GIT_GIT_DIFF_FILTER_REGEX_EXCLUDE | Custom regex excluding filter<br/>Ex: `(test|examples)` | Exclude no file |
| GIT_GIT_DIFF_FILE_EXTENSIONS | Allowed file extensions. `"*"` matches any extension, `""` matches empty extension. Empty list excludes all files<br/>Ex: `[".py", ""]` | Exclude every file |
| GIT_GIT_DIFF_FILE_NAMES_REGEX | File name regex filters. Regular expression list for filtering files by their base names using regex full match. Empty list includes all files<br/>Ex: `["Dockerfile(-.+)?", "Jenkinsfile"]` | Include every file |
| GIT_GIT_DIFF_DISABLE_ERRORS | Run linter but disable crash if errors found | `false` |

## Mega-Linter Flavours

This linter is available in the following flavours

| <!-- --> | Flavor | Description | Embedded linters | Info |
| :------: | :----- | :---------- | :--------------: | ---: |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/images/mega-linter-square.png" alt="" height="32px" class="megalinter-icon"></a> | [all](https://nvuillam.github.io/mega-linter/supported-linters/) | Default Mega-Linter Flavor | 74 | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/nvuillam/mega-linter/v4) ![Docker Pulls](https://img.shields.io/docker/pulls/nvuillam/mega-linter) |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/dart.ico" alt="" height="32px" class="megalinter-icon"></a> | [dart](https://nvuillam.github.io/mega-linter/flavors/dart/) | Mega-Linter optimized for DART based projects | 32 | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/nvuillam/mega-linter-dart/v4) ![Docker Pulls](https://img.shields.io/docker/pulls/nvuillam/mega-linter-dart) |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/dotnet.ico" alt="" height="32px" class="megalinter-icon"></a> | [dotnet](https://nvuillam.github.io/mega-linter/flavors/dotnet/) | Mega-Linter optimized for C, C++, C# or VB based projects | 37 | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/nvuillam/mega-linter-dotnet/v4) ![Docker Pulls](https://img.shields.io/docker/pulls/nvuillam/mega-linter-dotnet) |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/go.ico" alt="" height="32px" class="megalinter-icon"></a> | [go](https://nvuillam.github.io/mega-linter/flavors/go/) | Mega-Linter optimized for GO based projects | 32 | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/nvuillam/mega-linter-go/v4) ![Docker Pulls](https://img.shields.io/docker/pulls/nvuillam/mega-linter-go) |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/java.ico" alt="" height="32px" class="megalinter-icon"></a> | [java](https://nvuillam.github.io/mega-linter/flavors/java/) | Mega-Linter optimized for JAVA based projects | 32 | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/nvuillam/mega-linter-java/v4) ![Docker Pulls](https://img.shields.io/docker/pulls/nvuillam/mega-linter-java) |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/javascript.ico" alt="" height="32px" class="megalinter-icon"></a> | [javascript](https://nvuillam.github.io/mega-linter/flavors/javascript/) | Mega-Linter optimized for JAVASCRIPT or TYPESCRIPT based projects | 38 | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/nvuillam/mega-linter-javascript/v4) ![Docker Pulls](https://img.shields.io/docker/pulls/nvuillam/mega-linter-javascript) |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/php.ico" alt="" height="32px" class="megalinter-icon"></a> | [php](https://nvuillam.github.io/mega-linter/flavors/php/) | Mega-Linter optimized for PHP based projects | 35 | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/nvuillam/mega-linter-php/v4) ![Docker Pulls](https://img.shields.io/docker/pulls/nvuillam/mega-linter-php) |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/python.ico" alt="" height="32px" class="megalinter-icon"></a> | [python](https://nvuillam.github.io/mega-linter/flavors/python/) | Mega-Linter optimized for PYTHON based projects | 38 | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/nvuillam/mega-linter-python/v4) ![Docker Pulls](https://img.shields.io/docker/pulls/nvuillam/mega-linter-python) |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/ruby.ico" alt="" height="32px" class="megalinter-icon"></a> | [ruby](https://nvuillam.github.io/mega-linter/flavors/ruby/) | Mega-Linter optimized for RUBY based projects | 32 | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/nvuillam/mega-linter-ruby/v4) ![Docker Pulls](https://img.shields.io/docker/pulls/nvuillam/mega-linter-ruby) |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/rust.ico" alt="" height="32px" class="megalinter-icon"></a> | [rust](https://nvuillam.github.io/mega-linter/flavors/rust/) | Mega-Linter optimized for RUST based projects | 32 | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/nvuillam/mega-linter-rust/v4) ![Docker Pulls](https://img.shields.io/docker/pulls/nvuillam/mega-linter-rust) |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/scala.ico" alt="" height="32px" class="megalinter-icon"></a> | [scala](https://nvuillam.github.io/mega-linter/flavors/scala/) | Mega-Linter optimized for SCALA based projects | 32 | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/nvuillam/mega-linter-scala/v4) ![Docker Pulls](https://img.shields.io/docker/pulls/nvuillam/mega-linter-scala) |
| <img src="https://github.com/nvuillam/mega-linter/raw/master/docs/assets/icons/terraform.ico" alt="" height="32px" class="megalinter-icon"></a> | [terraform](https://nvuillam.github.io/mega-linter/flavors/terraform/) | Mega-Linter optimized for TERRAFORM based projects | 34 | ![Docker Image Size (tag)](https://img.shields.io/docker/image-size/nvuillam/mega-linter-terraform/v4) ![Docker Pulls](https://img.shields.io/docker/pulls/nvuillam/mega-linter-terraform) |

## Behind the scenes

### How are identified applicable files

<!-- markdownlint-disable -->
<!-- /* cSpell:disable */ -->

### Example calls

```shell
git diff --check
```


### Help content

```shell
usage: git [--version] [--help] [-C <path>] [-c <name>=<value>]
           [--exec-path[=<path>]] [--html-path] [--man-path] [--info-path]
           [-p | --paginate | -P | --no-pager] [--no-replace-objects] [--bare]
           [--git-dir=<path>] [--work-tree=<path>] [--namespace=<name>]
           <command> [<args>]

These are common Git commands used in various situations:

start a working area (see also: git help tutorial)
   clone             Clone a repository into a new directory
   init              Create an empty Git repository or reinitialize an existing one

work on the current change (see also: git help everyday)
   add               Add file contents to the index
   mv                Move or rename a file, a directory, or a symlink
   restore           Restore working tree files
   rm                Remove files from the working tree and from the index
   sparse-checkout   Initialize and modify the sparse-checkout

examine the history and state (see also: git help revisions)
   bisect            Use binary search to find the commit that introduced a bug
   diff              Show changes between commits, commit and working tree, etc
   grep              Print lines matching a pattern
   log               Show commit logs
   show              Show various types of objects
   status            Show the working tree status

grow, mark and tweak your common history
   branch            List, create, or delete branches
   commit            Record changes to the repository
   merge             Join two or more development histories together
   rebase            Reapply commits on top of another base tip
   reset             Reset current HEAD to the specified state
   switch            Switch branches
   tag               Create, list, delete or verify a tag object signed with GPG

collaborate (see also: git help workflows)
   fetch             Download objects and refs from another repository
   pull              Fetch from and integrate with another repository or a local branch
   push              Update remote refs along with associated objects

'git help -a' and 'git help -g' list available subcommands and some
concept guides. See 'git help <command>' or 'git help <concept>'
to read about a specific subcommand or concept.
See 'git help git' for an overview of the system.
```

### Installation on mega-linter Docker image


### Example success log

```shell
Results of git_diff linter (version 2.26.2)
See documentation on https://nvuillam.github.io/mega-linter/descriptors/git_git_diff/
-----------------------------------------------

[SUCCESS] .automation/test/git_diff/good
    

```
