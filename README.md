
# A quick git reference (WIP)

## Git workflow

- **Working Directory**: current files
- **Index**: staging area before recording
- **HEAD**: last commit recorded

## Getting started

| Command     | Options     | Description |
|-------------|-------------|---------------------------------------------------------|
| git clone       | *url*       | Clone a remote repository to current directory |
| git init        |             | Make current directory a repository |

## File operations

| Command     | Options     | Description |
|-------------|-------------|---------------------------------------------------------|
| git add         | *path*           |  Add files to index, e.g current dir (includes new, modified, deleted)  |
| git rm          | *path*           |  Remove file or directory from the working tree |
|                 | -f               |  Force deletion of files from disk |
| git commit      | -m "*message*"   |  Commit all (modified and deleted, except new) files with message |

## Branching

| Command     | Options     | Description |
|-------------|-------------|---------------------------------------------------------|
| git branch        |               | List branches |
| git branch        | *branchname*  | Create new branch |
| git checkout      | *branchname*  | Switch to branch |
| git merge         | *branchname*  | Merge changes from *branchname* to current tree |

## Tagging

| Command     | Options     | Description |
|-------------|-------------|---------------------------------------------------------|
| `git tag`           |               | List available tags |
| `git tag`           | `v1.0.0`        | Create tag, from latest commit, lightweight |
| `git tag`           | `-a v1.0.0 -m "<msg>"` | Create tag, from latest commit, annotated |
| `git tag`           | `-a <tagname> -m "<msg>" <SHA-1>` | Create tag, from specific commit |
| `git tag`           | `-d  v1.1.0` | Delete tag |
| `git show`          | `v1.0.0`        | Show tag data and message |
| `git checkout`      | `v1.0.0`        | Show tag data and message |


