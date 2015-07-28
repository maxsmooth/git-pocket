
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
| `git tag`           | `v1.0.0`        | Tag latest commit lightweight |
| `git tag`           | `v1.0.0 -a -m "*message*"` | Tag latest commit with annotation |
| `git show`          | `v1.0.0`        | Show tag data and message |


