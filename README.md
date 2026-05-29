# Omamac

Omamac is a keyboard-centric setup for macOS designed for developers working with the terminal. It's inspired by [Omarchy](https://omarchy.org/), and shares the same [Omadots](https://github.com/omacom-io/omadots) for the shell.

It's built on AeroSpace for real i3/Hyprland-style tiling and workspace management. It also sets up all the basic developer tooling needed for a Terminal-driven workflow centered around Tmux.

## Install

```bash
curl -fsSL https://omamac.org/install | bash
```

Note: This will overwrite any existing configurations for `.zshrc`, Neovim, and the like. It's intended for a fresh installation.

## What it sets up

- **Window Management**: AeroSpace (tiling, workspaces)
- **Terminal**: Alacritty, Tmux
- **Shell**: Starship prompt, fzf, eza, zoxide
- **Editors**: nvim, opencode, claude-code
- **Dev tools**: mise, Docker, lazygit, lazydocker
- **Git**: Helpful aliases and config

## Hotkeys

### Window Management (AeroSpace)

The modifier is `Alt` (⌥), like a tiling WM's `$mod`. Full config in `~/.config/aerospace/aerospace.toml`.

| Hotkey | Action |
|--------|--------|
| `Alt + Enter` | Launch terminal (Alacritty) |
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

### Terminal (Tmux)

You launch tmux with `t` in a new terminal (`Ctrl + Cmd + Return`).

**Prefix key:** `Ctrl + Space` (secondary: `Ctrl + b`)

**Pane Management:**

| Hotkey | Action |
|--------|--------|
| `Ctrl + Cmd + PageUp` | Split horizontally |
| `Ctrl + Cmd + PageDown` | Split vertically |
| `Ctrl + Cmd + Home` | Split horizontally |
| `Ctrl + Cmd + End` | Kill pane |
| `Ctrl + Cmd + ←` | Focus left pane |
| `Ctrl + Cmd + →` | Focus right pane |
| `Ctrl + Cmd + ↑` | Focus up pane |
| `Ctrl + Cmd + ↓` | Focus down pane |
| `Ctrl + Cmd + Shift + ←` | Resize left |
| `Ctrl + Cmd + Shift + ↓` | Resize down |
| `Ctrl + Cmd + Shift + ↑` | Resize up |
| `Ctrl + Cmd + Shift + →` | Resize right |

**Window Management:**

| Hotkey | Action |
|--------|--------|
| `Ctrl + Shift + Home` | New window |
| `Ctrl + Shift + End` | Kill window |
| `Ctrl + Shift + PageUp` | Next window |
| `Ctrl + Shift + PageDown` | Previous window |
| `Ctrl + Space x` | Kill window |
| `Ctrl + Space r` | Rename window |

**Session Management:**

| Hotkey | Action |
|--------|--------|
| `Ctrl + Cmd + Shift + Home` | New session |
| `Ctrl + Cmd + Shift + End` | Kill session |
| `Ctrl + Cmd + Shift + PageUp` | Previous session |
| `Ctrl + Cmd + Shift + PageDown` | Next session |
| `Ctrl + Space R` | Rename session |
| `Ctrl + Space X` | Kill session |

**Copy Mode (Vi):**

| Hotkey | Action |
|--------|--------|
| `v` | Begin selection |
| `y` | Copy selection |

**Other:**

| Hotkey | Action |
|--------|--------|
| `Ctrl + Space q` | Reload config |

