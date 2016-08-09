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

| Comando | Opzioni | Descrizione |
|------------|--------------|---------------------------------------------------------|
| `git config` | `--global user.name "Cooper Black"`    | Imposta lo user name globale |
| `git config` | `--global user.email "cooper@black.com"`    | Imposta la user email globale |
| `git config` | `--list`    | Mostra la configurazione |
| `git config` | `--global --list`  | Mostra la configuration globale |
| `git init` | | Imposta la directory corrente come un repository git |
| `git remote` | `add origin <url>`| Imposta il remote origin (la sorgente remota) |
| `git ls-tree` | `-r <branch> --name-only`  | Elenca i file monitorati |

Riferimenti: https://git-scm.com/docs/git-config

## $clone

| Comando | Opzioni | Descrizione |
|-------------|-------------|---------------------------------------------------------|
| `git clone`   | `<giturl>`  | Clona un repository remoto nella directory corrente |
| `git clone`   | `--recursive <giturl>`  | Clona un repository remoto con i sotto moduli (submodule) |

Riferimenti: https://git-scm.com/docs/git-clone

## $submodule

| Comando | Opzioni | Descrizione |
|-------------|-------------|---------------------------------------------------------|
| `git clone`     | `--recursive <giturl>`  | Clona un repository remoto con i sotto moduli |
| `git submodule` | `add <giturl>`  | Aggiunge un sotto modulo |
| `git submodule` | `update --remote` | Aggiorna un sotto modulo |
| `git submodule` | `status --recursive` | Mostra i sotto moduli |

**Eliminare un sottomodulo:**

```shell
$ git submodule deinit <path/to/submodule>
$ git rm <path/to/submodule>
```

Riferimenti: https://git-scm.com/docs/git-submodule

## $commit

| Comando | Opzioni | Descrizione |
|-------------|-------------|---------------------------------------------------------|
| `git add`         | `<filename>`   |  Aggiunge i files allo stage  |
| `git commit`      | `-m "<title>" -m "<body>"`  |  Effettua un commit con messaggio (solo per i file aggiunti allo stage) |
| `git rm`          | `<filename>`   |  Elimina i files dall'albero di lavoro e dall'indice |
|                   | `-f`                |  Forza la cancellazione dei files dal disco |
| `git rm` | `-r --cached <filename>`  | Effettua l'"untrack" del file (senza cancellarlo) (il file rimane su disco ma non sarà più tracciato da git) |

Riferimenti: https://git-scm.com/docs/git-commit

**Effettua l'untrack dei file nascosti, o aggiorna la lista dei files tracciati, dopo l'aggiunta di `.gitignore`:**

```shell
# rimuovi tutto
$ git rm -r --cached .

# aggiunti di nuovo tutto, adesso gitignore avrà effetto (prova ad aggiungere .gitignore dall'inizio la prossima volta)
$ git add .
```

## $push branches (vedi tag per il pushing dei tags)

| Comando     | Opzioni     | Descrizione |
|-------------|-------------|---------------------------------------------------------|
| `git push`    | `<remotename> <branchname>`     | Effettua il Push di un ramo al server remoto |
| `git push`    | `<remotename> --all`            | Effettua il Push di tutti i rami al server remoto |
| `git push`    | `--d <remotename> <branchname>` | `--delete` cancella un ramo dal server remoto |

Referimenti: https://git-scm.com/docs/git-push

## $remote

- Le connessioni remote sono come i segnalibri che prendono il nome di repository remoti
- `git clone` crea automaticamente una connessione remota chiamata solitamente `origin`

| Comando     | Opzioni     | Descrizione |
|-------------|-------------|---------------------------------------------------------|
| `git remote` | `-v`                         | Mostra le repository remote |
| `git branch` | `-r`                         | Mostra i rami nelle repository remote |
| `git remote` | `add <name> <url>`           | Crea una connessione con nome ad una repository remota |
| `git remote` | `rename <oldname> <newname>` | Rinomina la connessione |
| `git remote` | `rm <name>`                  | Rimuovi la connessione |

Riferimenti: https://git-scm.com/docs/git-remote

**Rimuovi l'origin remoto:**

```shell
# Rimuovi `origin` da .git/config
git remote rm origin

# Rimuovi `FETCH_HEAD` che punta ancora al remoto
git rm .git/FETCH_HEAD
```

## $fetch-pull
| Comando     | Opzioni     | Descrizione |
|-------------|-------------|---------------------------------------------------------|
| `git fetch`     | `<remote>`     | Effettua il Fetch di tutti i rami dal remoto (senza fare merge) |
| `git fetch`     | `<remote> <branch>`     | Effettua il Fetch di uno specifico ramo |
| `git merge`     | `<remote>/<branch>`     | Effettua il Merge del Fetche remoto già effettuato |
| `git pull`      | `<remote>`     | effettua il Fetch e il Merge in un unico comando |

Riferimenti: https://git-scm.com/docs/git-fetch, https://git-scm.com/docs/git-pull


## $branch

| Comando     | Opzioni     | Descrizione |
|-------------|-------------|---------------------------------------------------------|
| `git branch`        |                   | Mostra i rami |
| `git branch`        | `<branchname>`    | Crea un nuovo ramo |
| `git checkout`      | `<sha-1>`         | Effettua lo switch al ramo o al commit |
| `git branch`        | `-m <branchname> <newname>` | Rinomina il ramo |
| `git merge`         | `<branchname>`    | Effettua il Merge delle modifica da `<branchname>` al ramo corrente |
| `git branch`        | `-d <branchname>` | `--delete` (cancella) ramo |

Riferimenti: https://git-scm.com/docs/git-branch

## $status

| Comando     | Opzioni     | Descrizione |
|-------------|-------------|---------------------------------------------------------|
| `git status`  | `-s`        | Mostra lo stato di lavoro corrente, in formato `--short` (corto) |
| `git log`     | `--oneline` | Mostra i log dei commit, in formato `--oneline` (singola linea) |
| `git ls-files`|             | Mostra le informazioni dei file nell'indice e nell'albero di lavoro |

Riferimenti: https://git-scm.com/docs/git-status

## $diff

| Comando     | Opzioni     | Descrizione |
|-------------|-------------|---------------------------------------------------------|
| `git diff`  |             | Confronta **`working directory`** e **`index`** |
|             | `–-cached`  | Confronta **`index`** e **`latest commit`** (ultimo commit) |
|             | `HEAD`      | Confronta **`latest commit`** e **`working directory`** |
|             | `--stat`    | formato corto opzionale |
|             | `<sha-1> <sha-1>` | 2 punti nel temp da confrontare |
|             | `<dir> | <file>` | Confronta un'intera directory o limitati ad un file |

Riferimenti: https://git-scm.com/docs/git-diff

**Esempi:**

```shell
## confronta le modifiche fatte a README.md tra l'albero di lavoro (default) e l'ultimo commit (HEAD)
$ git diff --stat HEAD ./path/README.md

## confronta le modifiche fatte a README.md tra 2 specifici punti nel tempo (es. 2 commit)
$ git diff --stat a649900 24bdd58 ./path/README.md
```

## $tag

| Comando     | Opzioni     | Descrizione |
|-------------|-------------|---------------------------------------------------------|
| `git tag`           |                   | Mostra i tags |
| `git tag`           | `<v1.0.0>`        | Crea un tag, dall'ultimo commit, velocemente |
| `git tag`           | `-a <v1.0.0> -m "<msg>"` | Crea un tag, con `--annotate`, dall'ultimo commit |
| `git tag`           | `-a <v1.0.0> -m "<msg>" <SHA-1>` | Crea un tag, con `--annotate`, da uno specifico commit |
| `git tag`           | `-d  <v1.1.0>`    | `--delete` (canella) tag |
| `git show`          | `<v1.0.0>`        | Mostra i dati del tag e i messaggi |
| `git checkout`      | `<v1.0.0>`        | Effettua uno switch ad uno specifico tag (non editabile) |
| `git push`          | `<remote> <tag>`  | Effettua il Push di uno specifico tag a `<remote>` (raccommandato) |
| `git push`          | `<remote> --tags` | Effettua il Push di tutti i tags a `<remote>` (solo se necessario) |

Riferimenti: https://git-scm.com/docs/git-tag
