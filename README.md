<div align="center">

<img src="https://getslatewave.com/brand/icon.png" alt="" height="64" align="middle">
<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://getslatewave.com/brand/wordmark-light.png">
  <img alt="Slatewave" src="https://getslatewave.com/brand/wordmark.png" height="64" align="middle">
</picture>

# Slatewave (Starship)

A Slatewave prompt for [Starship](https://starship.rs) — slate foundation, teal signature. Part of the [Slatewave family](#slatewave-family) — one palette across editors, terminals, prompts, notes, and more.

> _Slate below, teal above._

</div>

---

## Layout

Two lines, three zones — mirrors the oh-my-posh companion so switching between the two is seamless:

```
╭─  ~ /  path    main ≡   2    1                          3.2s   83%    42%    3:04 PM
╰─❯
```

- **Left**: OS → path → git → language runtimes (python, node, go, rust, java, cmake, docker)
- **Right**: execution time → battery → memory → clock
- **Second line**: `╰─❯`, teal when the last command succeeded, rose when it exited non-zero

---

## Requirements

- **Starship** ≥ 1.16 (custom `[palettes.*]` tables, `$fill`, and `add_newline`) — [install guide](https://starship.rs/guide/#step-1-install-starship)
- A **Nerd Font** for the powerline glyphs (``, ``) and segment icons. Tested with MesloLGS NF and Hack Nerd Font. Configure your terminal accordingly.

---

## Installation

### Clone + point Starship at it

```sh
git clone https://github.com/kevinlangleyjr/starship-slatewave.git \
  ~/.config/starship-slatewave
```

Then point Starship at the config via the `STARSHIP_CONFIG` env var in your shell init:

**zsh** (`~/.zshrc`):
```sh
export STARSHIP_CONFIG=~/.config/starship-slatewave/slatewave.toml
eval "$(starship init zsh)"
```

**bash** (`~/.bashrc`):
```sh
export STARSHIP_CONFIG=~/.config/starship-slatewave/slatewave.toml
eval "$(starship init bash)"
```

**fish** (`~/.config/fish/config.fish`):
```fish
set -gx STARSHIP_CONFIG ~/.config/starship-slatewave/slatewave.toml
starship init fish | source
```

Reload (`exec zsh`) — the prompt applies immediately.

### Or: install as the default Starship config

Starship reads `~/.config/starship.toml` if `STARSHIP_CONFIG` is unset. Drop the theme file there to make it the default:

```sh
curl -fsSL https://raw.githubusercontent.com/kevinlangleyjr/starship-slatewave/main/slatewave.toml \
  -o ~/.config/starship.toml
```

### Or: import the palette into an existing config

The palette block is self-contained. To keep your current prompt layout but adopt the Slatewave colors, copy the `[palettes.slatewave]` table out of [`slatewave.toml`](./slatewave.toml) into your existing `~/.config/starship.toml` and add:

```toml
palette = 'slatewave'
```

at the top. Then reference palette colors by name in your own module styles — e.g. `style = 'fg:teal_300'`.

---

## Palette

Slatewave shares its palette with the companion themes. Every color resolves to a semantic name you can reference in overrides.

### Backgrounds

| | Hex | Palette | Used by |
|---|---|---|---|
| ![#0f172a](https://placehold.co/20x20/0f172a/0f172a.png) | `#0f172a` | `bg_inset` | reserved (editor inset) |
| ![#1e293b](https://placehold.co/20x20/1e293b/1e293b.png) | `#1e293b` | `bg_elevated` | reserved (editor elevated) |
| ![#21252b](https://placehold.co/20x20/21252b/21252b.png) | `#21252b` | `bg_raised` | reserved (editor chrome) |
| ![#282c34](https://placehold.co/20x20/282c34/282c34.png) | `#282c34` | `bg_base` | reserved (editor bg) |
| ![#2c313a](https://placehold.co/20x20/2c313a/2c313a.png) | `#2c313a` | `chrome_dark` | path, clock, alternate lang bg |
| ![#3e4451](https://placehold.co/20x20/3e4451/3e4451.png) | `#3e4451` | `chrome_light` | OS, memory, languages |

### Foregrounds

| | Hex | Palette | Used by |
|---|---|---|---|
| ![#64748b](https://placehold.co/20x20/64748b/64748b.png) | `#64748b` | `fg_faint` | reserved (disabled text) |
| ![#94a3b8](https://placehold.co/20x20/94a3b8/94a3b8.png) | `#94a3b8` | `fg_muted` | memory fg |
| ![#cbd5e1](https://placehold.co/20x20/cbd5e1/cbd5e1.png) | `#cbd5e1` | `fg_subtle` | execution time |
| ![#e2e8f0](https://placehold.co/20x20/e2e8f0/e2e8f0.png) | `#e2e8f0` | `fg_default` | OS, hostname |
| ![#f1f5f9](https://placehold.co/20x20/f1f5f9/f1f5f9.png) | `#f1f5f9` | `fg_bright` | reserved (bright text) |

### Accent

| | Hex | Palette | Used by |
|---|---|---|---|
| ![#5eead4](https://placehold.co/20x20/5eead4/5eead4.png) | `#5eead4` | `teal_300` | frame, path fg, language fg, clock fg, success caret |
| ![#99f6e4](https://placehold.co/20x20/99f6e4/99f6e4.png) | `#99f6e4` | `teal_200` | vimcmd caret |
| ![#0f766e](https://placehold.co/20x20/0f766e/0f766e.png) | `#0f766e` | `teal_600` | cmake bg |
| ![#0e7490](https://placehold.co/20x20/0e7490/0e7490.png) | `#0e7490` | `teal_700` | battery charging bg |
| ![#ecfeff](https://placehold.co/20x20/ecfeff/ecfeff.png) | `#ecfeff` | `cyan_fg` | cmake / battery fg |

### State colors

| | Hex | Palette | Meaning |
|---|---|---|---|
| ![#38bdf8](https://placehold.co/20x20/38bdf8/38bdf8.png) | `#38bdf8` | `sky_400` | git branch bg |
| ![#fb7185](https://placehold.co/20x20/fb7185/fb7185.png) | `#fb7185` | `rose_400` | root user, read-only dir |
| ![#ef5350](https://placehold.co/20x20/ef5350/ef5350.png) | `#ef5350` | `red_bright` | exit ≠ 0 caret |
| ![#b388ff](https://placehold.co/20x20/b388ff/b388ff.png) | `#b388ff` | `purple` | reserved (storage / decorators) |
| ![#fbbf24](https://placehold.co/20x20/fbbf24/fbbf24.png) | `#fbbf24` | `amber_400` | git rebase/merge state |
| ![#b45309](https://placehold.co/20x20/b45309/b45309.png) | `#b45309` | `amber_700` | battery discharging bg |
| ![#ff4500](https://placehold.co/20x20/ff4500/ff4500.png) | `#ff4500` | `orange` | reserved (git diverged) |
| ![#193549](https://placehold.co/20x20/193549/193549.png) | `#193549` | `git_ink` | fg on sky git segment |

---

## Segments in detail

| Segment | Shows | Foreground | Background |
|---|---|---|---|
| OS | platform icon | `fg_default` | `chrome_light` |
| Username | `user` (when different from default, or root) | `fg_default` / `rose_400` | `chrome_light` |
| Hostname | `host` (SSH sessions only) | `fg_default` | `chrome_light` |
| Directory | 3-dir truncated path with home icon | `teal_300` | `chrome_dark` |
| Git branch | `` branch | `git_ink` | `sky_400` |
| Git status | `stash`, `ahead/behind`, `modified`, `staged`, `untracked`, etc. | `git_ink` | `sky_400` |
| Git state | `REBASE`, `MERGE`, `BISECT`, … during multi-step ops | `amber_400` | `sky_400` |
| Python | version + `(virtualenv)` if active | `teal_300` | `chrome_light` |
| Node / Go / Rust / Java | version | `teal_300` | `chrome_light` |
| CMake | version when `CMakeLists.txt` present | `cyan_fg` | `teal_600` |
| Docker context | active non-default context | `teal_300` | `chrome_light` |
| Execution time | duration of last command (`min_time: 500ms`) | `fg_subtle` | _(transparent)_ |
| Battery | icon + percentage, hides at 100% on AC | `cyan_fg` | `teal_700` charging / `amber_700` discharging |
| Memory | RAM % | `fg_muted` | `chrome_light` |
| Clock | 12-hour local time | `teal_300` | `chrome_dark` |
| Character | prompt caret | `teal_300` success / `red_bright` error / `teal_200` vim cmd | _(transparent)_ |

---

## Customize

The theme file is a plain Starship config — every module is a top-level TOML table. To override without forking, edit [`slatewave.toml`](./slatewave.toml) in place, or point `STARSHIP_CONFIG` at your own file that imports only the palette.

Common edits:

- **24-hour clock**: `time_format = '%H:%M'` in `[time]`
- **Hide battery when full**: delete the `threshold = 100` block so the module falls through to nothing
- **Always show hostname**: set `ssh_only = false` in `[hostname]`
- **Longer paths**: bump `truncation_length` in `[directory]`
- **Swap powerline glyphs**: replace `` / `` with `▶` / `◀` or any Nerd Font alternative throughout the `format` strings
- **Disable a runtime segment**: add `disabled = true` to its table (e.g. `[java] disabled = true`)

Starship re-reads the config on every prompt, so edits apply without reloading the shell.

---

## Slatewave family

One palette. Every tool.

- **Editors** — [VSCode](https://github.com/kevinlangleyjr/vscode-slatewave) · [Neovim](https://github.com/kevinlangleyjr/neovim-slatewave) · [Helix](https://github.com/kevinlangleyjr/helix-slatewave) · [Zed](https://github.com/kevinlangleyjr/zed-slatewave) · [Sublime Text](https://github.com/kevinlangleyjr/sublime-text-slatewave) · [JetBrains](https://github.com/kevinlangleyjr/jetbrains-slatewave)
- **Terminals** — [Alacritty](https://github.com/kevinlangleyjr/alacritty-slatewave) · [Ghostty](https://github.com/kevinlangleyjr/ghostty-slatewave) · [iTerm2](https://github.com/kevinlangleyjr/iterm2-slatewave) · [WezTerm](https://github.com/kevinlangleyjr/wezterm-slatewave) · [Windows Terminal](https://github.com/kevinlangleyjr/windows-terminal-slatewave) · [Kitty](https://github.com/kevinlangleyjr/kitty-slatewave)
- **Prompts** — [Oh My Posh](https://github.com/kevinlangleyjr/slatewave-omp)
- **Multiplexer** — [tmux](https://github.com/kevinlangleyjr/tmux-slatewave)
- **CLI** — [LSD](https://github.com/kevinlangleyjr/lsd-slatewave)
- **Notes** — [Obsidian](https://github.com/kevinlangleyjr/obsidian-slatewave) · [Logseq](https://github.com/kevinlangleyjr/logseq-slatewave) · [MarkEdit](https://github.com/kevinlangleyjr/markedit-slatewave) · [Anytype](https://github.com/kevinlangleyjr/anytype-slatewave)
- **Launchers** — [Alfred](https://github.com/kevinlangleyjr/alfred-slatewave) · [Raycast](https://github.com/kevinlangleyjr/raycast-slatewave)
- **Chat** — [Slack](https://github.com/kevinlangleyjr/slack-slatewave)

See [getslatewave.com](https://getslatewave.com) for the full family.
---

## Contributing

Issues and PRs welcome. For palette changes, include a before/after screenshot of the prompt in both a clean and dirty git repo, with and without language runtimes detected, so the visual tradeoff is obvious.

---

## License

WTFPL — Do What The Fuck You Want To Public License. See [LICENSE](LICENSE).
