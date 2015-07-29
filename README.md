
# A quick Git reference (WIP)

## Git context

| Stage | Description |
|-------|-------------|
| Working directory | Actual files and changes on current directory |
| Index            \| Staging area | Snapshot of files and changes set aside to be commited |
| HEAD              | Latest commit recorded in current branch  |
| blog              |   |
| SHA-1             |   |

## Getting started

| Command     | Options     | Description |
|-------------|-------------|---------------------------------------------------------|
| `git init`  |             | Make current directory a git repository |
| `git clone` | `<giturl>`  | Clone remote repository into current directory |
| `git checkout`| `<object>`| Switch to commit, branch, or SHA-1 |
| `git status`| `-s`        | Show the working tree status, optional `--short` format |
| `git log`   | `--oneline` | Show commit logs, optional `--oneline` |
| `git ls-files`|           | Show information about files in the index and the working tree |

## Diff

| Command     | Options     | Description |
|-------------|-------------|---------------------------------------------------------|
| `git diff`  |             | Compare **`working directory`** and **`index`** |
|             | `–-cached`  | Compare **`index`** and **`latest commit`** |
|             | `HEAD`      | Compare **`latest commit`** and **`working directory`** |
|             | `--stat`    | Optional short format |
|             | `<commit> <commit> | <branch> <branch>` | 2 points in time to compare |
|             | `<path> | <file>` | Make output relative to `<path>` or limit to `<file>` |

#### Diff examples:

```shell
## compare changes made to README.md between working tree (implied default) and latest commit (HEAD)
$ git diff HEAD --stat ./path/README.md

## compare changes made to README.md between 2 points in time (e.g. 2 commits)
$ git diff --stat a649900 24bdd58 ./path/README.md
```

## Commiting and pushing

| Command     | Options     | Description |
|-------------|-------------|---------------------------------------------------------|
| `git add`         | `<file> | <path>`   |  Add files to staging area  |
| `git commit`      | `-m "<title>" -m "<body>"`  |  Commit with message (includes "added" files only) |
| `git rm`          | `<file> | <path>`   |  Remove files from the working tree and from the index |
|                   | `-f`                |  Force deletion of files from disk |

## Branching

| Command     | Options     | Description |
|-------------|-------------|---------------------------------------------------------|
| `git branch`        |                   | List branches |
| `git branch`        | `<branchname>`    | Create new branch |
| `git merge`         | `<branchname>`    | Merge changes from `<branchname>` to current tree |
| `git branch`        | `-d <branchname>` | `--delete` branch |

## Tagging

| Command     | Options     | Description |
|-------------|-------------|---------------------------------------------------------|
| `git tag`           |                   | List available tags |
| `git tag`           | `<v1.0.0>`        | Create tag, from latest commit, lightweight |
| `git tag`           | `-a <v1.0.0> -m "<msg>"` | Create tag, from latest commit, annotated |
| `git tag`           | `-a <v1.0.0> -m "<msg>" <SHA-1>` | Create tag, from specific commit |
| `git tag`           | `-d  <v1.1.0>`    | Delete tag |
| `git show`          | `<v1.0.0>`        | Show tag data and message |
| `git checkout`      | `<v1.0.0>`        | Switch to specific point tag (not editable) |


