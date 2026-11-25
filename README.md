<div align="center">

# unix-conf

**Personal Unix configuration files (dotfiles) for Bash, Readline and Vim (2016).**

[![Shell: Bash](https://img.shields.io/badge/shell-Bash-4EAA25)](.bashrc)
[![Editor: Vim](https://img.shields.io/badge/editor-Vim-019733)](.vimrc)
[![Year: 2016](https://img.shields.io/badge/year-2016-informational)](#history)
[![License: MIT](https://img.shields.io/badge/license-MIT-green)](LICENSE)

</div>

## Table of contents

- [About](#about)
- [The files](#the-files)
- [How the repository is organised](#how-the-repository-is-organised)
- [History](#history)
- [License](#license)

## About

This repository keeps the configuration files of a Unix home directory under version control: shell, command-line
editing and editor settings. The author's own comments, mainly in `.vimrc`, are in French.

## The files

### [`.bashrc`](.bashrc): Bash

- **Base**: the start of the file follows the default `.bashrc` of Debian and Ubuntu (colour prompt, which is
  [forced on](.bashrc#L5), window size check, `lesspipe`, colour `ls`, bash completion).
- **History**: duplicates and commands starting with a space are [not recorded](.bashrc#L11), the history file is
  appended to rather than overwritten, and each command is written to it at once (`history -a`).
- **Aliases** ([from line 92](.bashrc#L92)): `vi` runs `vim`, shortcuts for `apt-get install` / `remove`, coloured
  `grep`, a family of `ls` variants (sort by extension, size or date, hidden files, recursive), `s` for `cd ..`, `psg`
  to search running processes, `topten` for the ten largest entries of the current folder.
- **Functions** ([from line 122](.bashrc#L122)): `ff` finds files by name, `fe` finds files and runs a command on
  each, `fstr` searches a string in files and highlights it, `cmd` lists the most used commands (ignoring `sudo`),
  `logview` reads a log in colour with `ccze`, `tarx` extracts an archive, `cleantmp` deletes editor backup files.
- **Environment** (end of the file): Git completion script, then `PATH` and variables for Maven 3.3.9,
  a JDK 1.8 (macOS path), Hadoop 2.7.2, Scala 2.11.7, Pig 0.15.0, `gsutil` and Terraform.

### [`.inputrc`](.inputrc): Readline

- The up and down arrows search the history for commands that start with what is already typed.
- `page-completions off` removes the `--More--` prompt on long completion lists.

### [`.vimrc`](.vimrc): Vim

- **Editing comfort**: `,` as leader key, line numbers, spaces instead of tabs, 4-column indentation,
  case-insensitive search unless the pattern has capitals, incremental search, syntax highlighting with a dark
  background, mouse support, a custom status line, 500 lines of history.
- **Key mappings**: system clipboard copy, cut and paste ([line 4](.vimrc#L4)), `F5` toggles paste mode
  ([line 86](.vimrc#L86)), `F6` / `F7` / `F8` toggle line numbers, mouse and search highlighting, `Tab` / `Shift-Tab`
  indent ([line 106](.vimrc#L106)), `Ctrl-j` / `Ctrl-k` move the current line, `Alt-Up` / `Alt-Down` switch tabs,
  `Shift`+arrows select text ([line 151](.vimrc#L151)), `Ctrl-Z` undoes.
- **Web development helpers**: a template inserted in new `.html` files ([line 1](.vimrc#L1)), abbreviations for
  CSS, PHP and eZ Publish templates with a `____` placeholder that `Ctrl-W` jumps to ([line 43](.vimrc#L43)), a
  function that turns accented letters into HTML entities, a mapping that clears the eZ Publish caches.
- **Lookups from visual mode** ([line 100](.vimrc#L100)): the word under the cursor opened in Firefox on Wikipedia,
  the eZ Publish documentation or the PHP manual, or searched with `rgrep` / `find`.
- **Shortcuts to personal files**: notes, a project stylesheet, the `.vimrc` itself (open and reload), and command
  abbreviations that copy the current file to a remote web server with `scp`.

## How the repository is organised

The repository is meant to be the home directory itself. Its [`.gitignore`](.gitignore) ignores everything (`*`)
and then lists the few files to track, so the rest of the home directory stays out of Git:

```
~/
├── .gitignore    ignore all, except the files below
├── .bashrc
├── .inputrc
├── .vimrc
├── README.md     (added with git add -f, as the .gitignore ignores it)
└── LICENSE
```

Some settings point to files that are not in the repository, such as `~/.git-completion.bash`, the Vim HTML
template in `~/.vim/templates/`, and the `~/tmp` and `~/bak` folders used by Vim.

## History

All files were added in a single commit in March 2016.

## License

Released under the [MIT License](LICENSE). © 2016 Erwan Rouzel.

The start of [`.bashrc`](.bashrc) comes from the default `.bashrc` shipped with Debian and Ubuntu, which keeps its
own origin.
