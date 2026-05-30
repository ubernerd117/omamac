# Omamac

A lean, tiling-first macOS dev setup — a debloated fork of [omamac](https://github.com/omacom-io/omamac). It's keyboard-centric and built for developers who live in the terminal, inspired by [Omarchy](https://omarchy.org/) and sharing the same [Omadots](https://github.com/omacom-io/omadots) for the shell and Neovim.

The window-management stack is replaced with [AeroSpace](https://github.com/nikitabobko/AeroSpace) for real i3/Hyprland-style tiling and workspaces, and the GUI app bloat is stripped down to dev-only essentials. It sets up the basic developer tooling needed for a Terminal-driven workflow centered around Tmux.

## Install

```bash
curl -fsSL https://raw.githubusercontent.com/ubernerd117/omamac/main/install.sh | bash
```

Note: This will overwrite any existing configurations for `.zshrc`, Neovim, and the like. It's intended for a fresh installation.

## What it sets up

- **Window Management**: AeroSpace (tiling, workspaces)
- **Terminal**: Alacritty, Tmux
- **Shell**: Starship prompt, fzf, eza, zoxide
- **Editors**: nvim, opencode, claude-code
- **Dev tools**: Docker, lazygit, lazydocker, gh (GitHub CLI), jq
- **Git**: Helpful aliases and config

## Hotkeys

### Window Management (AeroSpace)

The modifier is `Alt` (⌥), like a tiling WM's `$mod`. Full config in `~/.config/aerospace/aerospace.toml`.

| Hotkey | Action |
|--------|--------|
| `Alt + Enter` | Launch terminal (Alacritty) |
| `Alt + Shift + B` | Launch browser (Zen)  |
| `Alt + H / J / K / L` | Focus left / down / up / right |
| `Alt + Shift + H / J / K / L` | Move window left / down / up / right |
| `Alt + -` / `Alt + =` | Shrink / grow focused window |
| `Alt + /` | Tiles layout (horizontal/vertical) |
| `Alt + ,` | Accordion layout |
| `Alt + F` | Fullscreen focused window |
| `Alt + Shift + Space` | Toggle floating / tiling |
| `Alt + [1-9]` | Switch to workspace |
| `Alt + Shift + [1-9]` | Move window to workspace |
| `Alt + Tab` | Back-and-forth to previous workspace |
| `Alt + Shift + Tab` | Move workspace to next monitor |
| `Alt + Shift + ;` | Enter service mode (reload/reset) |

In **service mode**: `Esc` reloads config, `R` resets the layout, `F` toggles floating, `Backspace` closes all windows but the current one.

**Multi-monitor:** workspaces are pinned to specific screens via `[workspace-to-monitor-force-assignment]` — `1`–`5` on the built-in display (`main`), `6`–`9` on the external (`secondary`). This keeps each workspace on a predictable screen and stops AeroSpace from parking a stray, unbound workspace (e.g. `11`) on a monitor. With only one display connected, every workspace falls back to it automatically.

### Terminal (Tmux)

Alacritty launches straight into tmux (it runs `tmux new-session -A -s main`, attaching to the running session or creating one), so a new terminal (`Alt + Enter`) drops you into tmux automatically. The tmux config is not in this repo — it's installed via [Omadots](https://github.com/omacom-io/omadots); the bindings below mirror [`config/tmux/tmux.conf`](https://github.com/omacom-io/omadots/blob/master/config/tmux/tmux.conf) upstream (installed to `~/.config/tmux/tmux.conf`).

`Alt` is the Option key — Alacritty is configured with `option_as_alt = "Both"`. Below, `<prefix>` means press the prefix key first, then release and press the next key.

**Prefix key:** `Ctrl + Space` (secondary: `Ctrl + b`)

> **Heads up — AeroSpace grabs some Alt keys first.** AeroSpace binds `Alt + Enter` (launch terminal) and `Alt + 1`–`9` (switch workspace) globally, so tmux never sees them. Use the `<prefix>`-based alternatives (e.g. `<prefix> h` to split, `<prefix> w` to pick a window) when those collide.

**Pane Management:**

| Hotkey | Action |
|--------|--------|
| `Alt + Enter` | Split pane below *(grabbed by AeroSpace — use `<prefix> h`)* |
| `Alt + Shift + Enter` | Split pane to the right |
| `<prefix> h` | Split pane below |
| `<prefix> v` | Split pane to the right |
| `Alt + Escape` / `<prefix> x` | Kill pane |
| `Ctrl + Alt + ←/↓/↑/→` | Focus pane left / down / up / right |
| `Ctrl + Alt + Shift + ←/↓/↑/→` | Resize pane left / down / up / right |

**Window Management:**

| Hotkey | Action |
|--------|--------|
| `<prefix> c` | New window |
| `<prefix> k` | Kill window |
| `<prefix> r` | Rename window |
| `Alt + ←` / `Alt + →` | Previous / next window |
| `Alt + Shift + ←` / `Alt + Shift + →` | Move window left / right |
| `Alt + 1`–`9` | Select window 1–9 *(grabbed by AeroSpace)* |

**Session Management:**

| Hotkey | Action |
|--------|--------|
| `<prefix> C` | New session |
| `<prefix> K` | Kill session |
| `<prefix> R` | Rename session |
| `<prefix> P` / `<prefix> N` | Previous / next session |
| `Alt + ↑` / `Alt + ↓` | Previous / next session |

**Copy Mode (Vi):**

| Hotkey | Action |
|--------|--------|
| `v` | Begin selection |
| `y` | Copy selection |

**Other:**

| Hotkey | Action |
|--------|--------|
| `<prefix> q` | Reload config |
| `<prefix> ?` | Show all keybindings (popup) |

