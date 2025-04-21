# Git notes

Git is a distributed version control system.
At first, it is developed to manage the changesets in the Linux source code.

## States in Git

There are three states in Git: Modified, Staged and Committed

- Modified means that you have changed the file but have not committed it to your database yet.
- Staged means that you have marked a modified file in its current version to go into your next commit snapshot.
- Committed means that the data is safely stored in your local database.

This leads us to the three main sections of a Git project: the working tree, the staging area, and the Git directory.

The working tree is a single checkout of one version of the project. These files are pulled out of the compressed database in the Git directory and placed on disk for you to use or modify.

The staging area is a file, generally contained in your Git directory, that stores information about what will go into your next commit. Its technical name in Git parlance is the "index", but the phrase "staging area" works just as well.

The Git directory is where Git stores the metadata and object database for your project. This is the most important part of Git, and it is what is copied when you clone a repository from another computer.

## Config

Git comes with a tool called `git config` that lets you get and set configuration variables.
These variables can be stored in three different places:

1. `[path]/etc/gitconfig` file: Contains values applied to every user on the system and all their repositories. If you pass the option `--system` to `git config`, it reads and writes from this file specifically.
2. `~/.gitconfig` or `~/.config/git/config` file: Values specific personally to you, the user. You can make Git read and write to this file specifically by passing the `--global` option.
3. `config` file in the Git directory (that is, `.git/config`) of whatever repository you're currently using: Specific to that single repository. You can force Git to read from and write to this file with the `--local` option, but that is in fact the default.

Each level overrides values in the previous level, so values in `.git/config` trump those in `[path]/etc/gitconfig`.

### Your identity

The first thing you should do when you install Git is to set your user name and email address. This is important because every Git commit uses this information, and it's immutably baked into the commits you start creating:

```sh
git config --global user.name "John Doe"
git config --global user.email johndoe@example.com
```

### Your editor

Now that your identity is set up, you can configure the default text editor that will be used when Git needs you to type in a message. If not configured, Git uses your system's default editor.

If you want to use a different text editor, such as Emacs, you can do the following:

```sh
git config --global core.editor emacs
```

### Your default branch name

By default Git will create a branch called **master** when you create a new repository with `git init`. From Git version 2.28 onwards, you can set a different name for the initial branch.

To set `main` as the default branch name do:

```sh
git config --global init.defaultBranch main
```

### Checking your settings

If you want to check your configuration settings, you can use the `git config --list` command to list all the settings Git can find at that point:

```sh
$ git config --list
user.name=John Doe
user.email=johndoe@example.com
color.status=auto
color.branch=auto
color.interactive=auto
color.diff=auto
...
```

You can view where they are coming from using:

```sh
git config --list --show-origin
```

You can also check what Git thinks a specific key's value is by typing `git config <key>`:

```sh
$ git config user.name
John Doe
```

## Getting help

If you ever need help while using Git, there are three equivalent ways to get the comprehensive manual page (manpage) help for any of the Git commands:

```sh
git help <verb>
git <verb> --help
man git-<verb>
```

In addition, if you don't need the full-blown manpage help, but just need a quick refresher on the available options for a Git command, you can ask for the more concise "help" output with the `-h` option, as in:

```sh
$ git add -h
usage: git add [<options>] [--] <pathspec>...

    -n, --dry-run               dry run
    -v, --verbose               be verbose

    -i, --interactive           interactive picking
    -p, --patch                 select hunks interactively
    -e, --edit                  edit current diff and apply
    -f, --force                 allow adding otherwise ignored files
    -u, --update                update tracked files
    --renormalize               renormalize EOL of tracked files (implies -u)
    -N, --intent-to-add         record only the fact that the path will be added later
    -A, --all                   add changes from all tracked and untracked files
    --ignore-removal            ignore paths removed in the working tree (same as --no-all)
    --refresh                   don't add, only refresh the index
    --ignore-errors             just skip files which cannot be added because of errors
    --ignore-missing            check if - even missing - files are ignored in dry run
    --sparse                    allow updating entries outside of the sparse-checkout cone
    --chmod (+|-)x              override the executable bit of the listed files
    --pathspec-from-file <file> read pathspec from file
    --pathspec-file-nul         with --pathspec-from-file, pathspec elements are separated with NUL character
```
