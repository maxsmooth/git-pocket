
# A quick git reference (WIP)

## Context

- **Working Directory**: current files
- **Index**: staging area before recording
- **HEAD**: last commit recorded

## Getting started

| Command     | Options     | Description |
|-------------|-------------|---------------------------------------------------------|
| `git init`  |             | Make current directory a repository |
| `git clone` | `<url>`     | Clone remote repository into current directory |

## File operations

## Commiting and pushing

| Command     | Options     | Description |
|-------------|-------------|---------------------------------------------------------|
| `git add`         | `<file> | <path>`     |  Start tracking files (includes new, modified, deleted)  |
| `git commit`      | `-m "<title>" -m "<body>"` |  Commit with message (modified, deleted, except new) |
| `git rm`          | `*path*`            |  Remove file or directory from the working tree |
|                   | `-f`                |  Force deletion of files from disk |

## Branching

| Command     | Options     | Description |
|-------------|-------------|---------------------------------------------------------|
| `git branch`        |               | List branches |
| `git branch`        | `<branchname>`  | Create new branch |
| `git checkout`      | `<object>`    | Switch to commit, branch, sha-1 |
| `git merge`         | `<branchname>`  | Merge changes from `<branchname>` to current tree |

## Tagging

| Command     | Options     | Description |
|-------------|-------------|---------------------------------------------------------|
| `git tag`           |               | List available tags |
| `git tag`           | `<v1.0.0>`        | Create tag, from latest commit, lightweight |
| `git tag`           | `-a <v1.0.0> -m "<msg>"` | Create tag, from latest commit, annotated |
| `git tag`           | `-a <v1.0.0> -m "<msg>" <SHA-1>` | Create tag, from specific commit |
| `git tag`           | `-d  <v1.1.0>` | Delete tag |
| `git show`          | `<v1.0.0>`        | Show tag data and message |
| `git checkout`      | `<v1.0.0>`        | Switch to specific point tag |


