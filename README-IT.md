*traduzione italiana in corso*

# Git Pocket Guide

**Definizione:** Git è un software di controllo versione distribuito utilizzabile da interfaccia a riga di comando, creato da Linus Torvalds nel 2005.

**Scopo:** Tenere traccia delle revisioni dei software e delle modifiche ai file.

Il [software Git](https://git-scm.com/downloads) (come un driver) deve essere installato localmente sul computer prima di essere utilizzato, successivamente puoi cominciare a tenere traccia delle revisioni software. Le revisioni (modifiche) sono salvate in un repository locale e in uno remoto [distribuito](https://git-scm.com/book/it/v2/Distributed-Git-Distributed-Workflows). Il repository remoto può risiedere in un server proprio (come [GitLab](https://about.gitlab.com/)), o in un servizio su internet (cloud) come [github](https://github.com/). Gli sviluppatori di un team manderanno e recupereranno le revisioni a e da quel server remoto.

**Servizi Cloud:**

- [github.com](https://github.com)
  - gratis per progetti open source
  - grande community per i progetti open source
- [beanstalkapp.com](http://beanstalkapp.com/)
  - gratis per 1 utente + 1 repository
  - ottimo sistema di deploy integrato
- [bitbucket.org](https://bitbucket.org/)
  - gratis per team di sviluppatori sotto i 5 utenti
  - ottima documentazione
- [buddy.works](https://buddy.works)
  - gratis per 1 repository + utenti illimitati
  - ottimi strumenti per la collaberazione del team
  - ottimo sistema di deploy integrato

## TOC (table of contents - tavola dei contenuti)

**Usa il simbolo “$” per cercare nel documento**

- [$setup](https://github.com/heyallan/git-pocket/blob/gh-pages/README.md#setup)
- [$gibberish](https://github.com/heyallan/git-pocket/blob/gh-pages/README.md#gibberish)
- [$getting-started](https://github.com/heyallan/git-pocket/blob/gh-pages/README.md#getting-started)
- [$clone](https://github.com/heyallan/git-pocket/blob/gh-pages/README.md#clone)
- [$submodule](https://github.com/heyallan/git-pocket/blob/gh-pages/README.md#submodule)
- [$commit](https://github.com/heyallan/git-pocket/blob/gh-pages/README.md#commit)
- [$push](https://github.com/heyallan/git-pocket/blob/gh-pages/README.md#push)
- [$remote](https://github.com/heyallan/git-pocket/blob/gh-pages/README.md#remote)
- [$fetch-pull](https://github.com/heyallan/git-pocket/blob/gh-pages/README.md#fetch-pull)
- [$branch](https://github.com/heyallan/git-pocket/blob/gh-pages/README.md#branch)
- [$status](https://github.com/heyallan/git-pocket/blob/gh-pages/README.md#status)
- [$diff](https://github.com/heyallan/git-pocket/blob/gh-pages/README.md#diff)
- [$tag](https://github.com/heyallan/git-pocket/blob/gh-pages/README.md#tag)
- [$update](https://github.com/heyallan/git-pocket/blob/gh-pages/README.md#update)

## $setup

Guida al setup di Git: https://help.github.com/articles/set-up-git/

## $gibberish ([vedi wikipedia](https://it.wikipedia.org/wiki/Gibberish))

| Keyword | Descrizione |
|-------|-------------|
| `Working directory` (`Cartella di lavoro`) | File aggiornati nella directory (cartella) corrente |
| `Index` \| `Staging area` | Istantanea delle modifiche messe da parte su cui effettuare il commit |
| `SHA-1`             | identificatore univoco che rappresenta le informazioni storiche |
| `blob`              | Rappresenta un file  |
| `tree`              | Rappresenta una directory di files |
| `Commit`            | Rappresenta un tree (directory) in un certo punto del tempo  |
| `HEAD`              | Rappresenta l'ultimo commit del ramo corrente  |
| `Tag`               | Rappresenta uno specifico commit usato per marcare un punto importante nella storia del software |

Fai in modo che git ricordi le tue credenziali dalla seconda volta in poi che le inserisci in un push/pull: `$ git config credential.helper cache`


## $getting-started

| Command | Options | Description |
|------------|--------------|---------------------------------------------------------|
| `git config` | `--global user.name "Cooper Black"`    | Set global user name |
| `git config` | `--global user.email "cooper@black.com"`    | Set global user email |
| `git config` | `--list`    | Display configuration |
| `git config` | `--global --list`  | Display global configuration |
| `git init` | | Make current directory a git repository |
| `git remote` | `add origin <url>`| Set remote origin |
| `git ls-tree` | `-r <branch> --name-only`  | List files being tracked |

Reference: https://git-scm.com/docs/git-config

## $clone

| Command     | Options     | Description |
|-------------|-------------|---------------------------------------------------------|
| `git clone`   | `<giturl>`  | Clone remote repository into current directory |
| `git clone`   | `--recursive <giturl>`  | Clone remote repository with submodules |

Reference: https://git-scm.com/docs/git-clone

## $submodule

| Command     | Options     | Description |
|-------------|-------------|---------------------------------------------------------|
| `git clone`     | `--recursive <giturl>`  | Clone remote repository with submodules |
| `git submodule` | `add <giturl>`  | Add submodule |
| `git submodule` | `update --remote` | Update submodules |
| `git submodule` | `status --recursive` | List submodules |

**Remove submodule:**

```shell
$ git submodule deinit <path/to/submodule>
$ git rm <path/to/submodule>
```

Reference: https://git-scm.com/docs/git-submodule

## $commit

| Command     | Options     | Description |
|-------------|-------------|---------------------------------------------------------|
| `git add`         | `<filename>`   |  Add files to staging area  |
| `git commit`      | `-m "<title>" -m "<body>"`  |  Commit with message (includes "added" files only) |
| `git rm`          | `<filenama>`   |  Remove files from the working tree and from the index |
|                   | `-f`                |  Force deletion of files from disk |
| `git rm` | `-r --cached <filename>`  | Untrack file (without deleting) |

Reference: https://git-scm.com/docs/git-commit

**Untrack hidden files, or update list of tracked files, after adding `.gitignore`:**

```shell
# remove all
$ git rm -r --cached .

# add all again, now gitignore will take effect (try to add .gitignore from the start next time)
$ git add .
```

## $push branches (see tags for pushing tags)

| Command     | Options     | Description |
|-------------|-------------|---------------------------------------------------------|
| `git push`    | `<remotename> <branchname>`     | Push branch to remote |
| `git push`    | `<remotename> --all`            | Push all branches to remote |
| `git push`    | `--d <remotename> <branchname>` | `--delete` remote branch |

Reference: https://git-scm.com/docs/git-push

## $remote

- Remote connections are like bookmarks named after remote repos
- `git clone` automatically creates a remote connection usually called `origin`

| Command     | Options     | Description |
|-------------|-------------|---------------------------------------------------------|
| `git remote` | `-v`                         | List remote repository endpoints |
| `git branch` | `-r`                         | List remote repository branches |
| `git remote` | `add <name> <url>`           | Create namespaced connection to a remote repository |
| `git remote` | `rename <oldname> <newname>` | Rename connection |
| `git remote` | `rm <name>`                  | Remove connection |

Reference: https://git-scm.com/docs/git-remote

**Remove remote origin:**

```shell
# Remove `origin` settings from .git/config
git remote rm origin

# Remove `FETCH_HEAD` which still points to remote
git rm .git/FETCH_HEAD
```

## $fetch-pull
| Command     | Options     | Description |
|-------------|-------------|---------------------------------------------------------|
| `git fetch`     | `<remote>`     | Fetch all branches from remote (without merge) |
| `git fetch`     | `<remote> <branch>`     | Fetch specific branch |
| `git merge`     | `<remote>/<branch>`     | Merge fetched remote |
| `git pull`      | `<remote>`     | Fetch and merge in one command |

Reference: https://git-scm.com/docs/git-fetch, https://git-scm.com/docs/git-pull


## $branch

| Command     | Options     | Description |
|-------------|-------------|---------------------------------------------------------|
| `git branch`        |                   | List branches |
| `git branch`        | `<branchname>`    | Create new branch |
| `git checkout`      | `<sha-1>`         | Switch to branch, or commit |
| `git branch`        | `-m <branchname> <newname>` | Rename branch |
| `git merge`         | `<branchname>`    | Merge changes from `<branchname>` to current branch |
| `git branch`        | `-d <branchname>` | `--delete` branch |

Reference: https://git-scm.com/docs/git-branch

## $status

| Command     | Options     | Description |
|-------------|-------------|---------------------------------------------------------|
| `git status`  | `-s`        | Show the working tree status, with `--short` format |
| `git log`     | `--oneline` | Show commit logs, with `--oneline` format |
| `git ls-files`|             | Show information about files in the index and the working tree |

Reference: https://git-scm.com/docs/git-status

## $diff

| Command     | Options     | Description |
|-------------|-------------|---------------------------------------------------------|
| `git diff`  |             | Compare **`working directory`** and **`index`** |
|             | `–-cached`  | Compare **`index`** and **`latest commit`** |
|             | `HEAD`      | Compare **`latest commit`** and **`working directory`** |
|             | `--stat`    | Optional short format |
|             | `<sha-1> <sha-1>` | 2 points in time to compare |
|             | `<dir> | <file>` | Compare whole directory or limit to file |

Reference: https://git-scm.com/docs/git-diff

**Examples:**

```shell
## compare changes made to README.md between working tree (default) and latest commit (HEAD)
$ git diff --stat HEAD ./path/README.md

## compare changes made to README.md between 2 specific points in time (e.g. 2 commits)
$ git diff --stat a649900 24bdd58 ./path/README.md
```

## $tag

| Command     | Options     | Description |
|-------------|-------------|---------------------------------------------------------|
| `git tag`           |                   | List tags |
| `git tag`           | `<v1.0.0>`        | Create tag, from latest commit, lightweight |
| `git tag`           | `-a <v1.0.0> -m "<msg>"` | Create tag, with `--annotate`, from latest commit |
| `git tag`           | `-a <v1.0.0> -m "<msg>" <SHA-1>` | Create tag, with `--annotate`, from specific commit |
| `git tag`           | `-d  <v1.1.0>`    | `--delete` tag |
| `git show`          | `<v1.0.0>`        | Show tag data and message |
| `git checkout`      | `<v1.0.0>`        | Switch to specific point tag (not editable) |
| `git push`          | `<remote> <tag>`  | Push specific tag to `<remote>` (recommended) |
| `git push`          | `<remote> --tags` | Push all tags to `<remote>` (only if necessary) |

Reference: https://git-scm.com/docs/git-tag
