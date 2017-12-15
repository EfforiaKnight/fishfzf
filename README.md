# Fzf

[![Slack Room][slack-badge]][slack-link]

**fzf** provides efficient keybindings for the [fzf](https://github.com/junegunn/fzf) utility. Heavily adapted from @hauleth's PR.

## Install

With [fisherman]

```
fisher fzf
```

## Notes

* Required fish version: `>=2.4.0`
* Compatible fzf versions: `>0.11.3`

## Additional tools
* [tmux] - terminal multiplexer
* [rougify] - colored peview
* [locate] - searching a pre-constructed database file. Before locate can be used, the database will need to be created. To do this, execute updatedb as root.

## FZF binary
This plugin will fail if the `fzf` binary is not detected in your `PATH`.

The recommended means of installing `fzf` is through your respective package managers. However, if you do wish to install the latest version, simply run:

```
__fzf_install
```

If you later wish to uninstall the binary, run:

```
__fzf_uninstall
```

Note that the binary is only installed for the current user.

## Usage

| Legacy      | New Keybindings   | Remarks                                                       |
| -------     | ----------------- | ------------------------------------------------------------- |
| Ctrl-t      | Ctrl-f            | Find a file.                                                  |
| Ctrl-r      | Ctrl-r            | Similar to ^                                                  |
| Ctrl-x      | Alt-x             | Does the reverse isearch, and immediately executes command.   |
| Alt-c       | Alt-o             | cd into sub-directories (recursively searched).               |
| Alt-Shift-c | Alt-Shift-o       | cd into sub-directories, including hidden ones.               |
| Ctrl-o      | Ctrl-o            | Find file/directory using locate.                             |

Legacy keybindings are kept by default, but these have conflict with keybindings in fish 2.4.0. If you want to use the new keybindings, enter the following into your terminal:

```
set -U FZF_LEGACY_KEYBINDINGS 0
```

NOTE: On OS X, Alt-c (Option-c) types ç by default. In iTerm2, you can send the right escape sequence with Esc-c. If you configure the option key to act as +Esc (iTerm2 Preferences > Profiles > Default > Keys > Left option (⌥) acts as: > +Esc), then alt-c will work for fzf as documented.


## Commands
| Variable                       | Remarks                                               | Example                                                       |
| ------------------------------ | ----------------------------------------------------- | ------------------------------------------------------------- |
| `FZF_FIND_FILE_COMMAND`        | Modify the command used to generate the list of files | `set -U FZF_FIND_FILE_COMMAND rg --files --smart-case --no-ignore --hidden --follow --no-messages --glob '!.git/*'` |
| `FZF_CD_COMMAND`               | Similar to ^                                          | Similar to ^                                                  |
| `FZF_CD_WITH_HIDDEN_COMMAND`   | Similar to ^                                          | Similar to ^                                                  |
| `FZF_FIND_AND_EXECUTE_COMMAND` | Similar to ^                                          | Similar to ^                                                  |
| `FZF_REVERSE_ISEARCH_COMMAND`  | Similar to ^                                          | Similar to ^                                                  |
| `FZF_LOCATE_COMMAND`           | Similar to ^                                          | `set -U FZF_LOCATE_COMMAND locate /`                                                 |

## Variables
| Variable                    | Remarks                                                        | Example                                               |
| --------------------------- | -------------------------------------------------------------- | ----------------------------------------------------  |
| `FZF_DEFAULT_OPTS`          | Default options passed to every fzf command                    | `set -U FZF_DEFAULT_OPTS "--height 40"`               |
| `FZF_FIND_FILE_OPTS`        | Pass in additional arguments to the fzf command for find file  | `set -U FZF_FIND_FILE_OPTS "--preview 'rougify {} 2>/dev/null' --preview-window right:60%:hidden --bind 'ctrl-e:execute(tmux split-window -fh nvim {})' --bind 'ctrl-o:execute(open {})' --bind 'alt-n:preview-down' --bind 'alt-p:preview-up' --bind '?:toggle-preview' --history='$HOME/.cache/FZF_history'"` |
| `FZF_CD_OPTS`               | Similar to ^                                                   | Similar to ^                                          |
| `FZF_CD_WITH_HIDDEN_OPTS`   | Similar to ^                                                   | Similar to ^                                          |
| `FZF_FIND_AND_EXECUTE_OPTS` | Similar to ^                                                   | Similar to ^                                          |
| `FZF_REVERSE_ISEARCH_OPTS`  | Similar to ^                                                   | Similar to ^                                          |
| `FZF_LOCATE_OPTS`           | Similar to ^                                                   | Similar to ^                                          |
| `FZF_TMUX`                  | Runs a tmux-friendly version of fzf instead.                   | `set -U FZF_TMUX 1`                                   |

[tmux]:https://tmux.github.io/
[rougify]:http://rouge.jneen.net/
[locate]:https://anonscm.debian.org/cgit/collab-maint/mlocate.git
[slack-link]: https://fisherman-wharf.herokuapp.com
[slack-badge]: https://fisherman-wharf.herokuapp.com/badge.svg
[fisherman]: https://github.com/fisherman/fisherman