# tmux-config

English | [简体中文](README.md)

Tmux configuration for daily development and remote sessions, with a Catppuccin Frappe theme, `Ctrl+a` prefix, TPM-managed plugins, and enhanced clipboard integration.

> Companion documentation: installation, onboarding, and keymap reference are published at <https://longwaybai.github.io/docs/tmux/>.

![tmux preview](https://longwaybai.github.io/assets/images/cover-effect-a3e41d734805fcbb90bfebec1d8764fe.png)

![tmux workflow demo](https://longwaybai.github.io/assets/images/minimal-closed-loop-e694ba4e16466fc16951986b5720be23.gif)

## ✨ Features

- Catppuccin Frappe theme with an enhanced status bar
- Prefix key changed from `Ctrl+b` to `Ctrl+a`
- Mouse support, Vi-style copy mode, and OSC52 clipboard integration
- TPM-managed plugins: `tmux-cpu`, `tmux-battery`, `tmux-floax`, and `catppuccin/tmux`
- Remote-session config and helper scripts for local and SSH-based workflows

## 📚 Companion Documentation

This repository is the configuration source for the published tmux documentation set:

- [Tmux Guide](https://longwaybai.github.io/docs/tmux/)
- [Installation and Initial Setup](https://longwaybai.github.io/docs/tmux/installation)
- [Keymap Reference](https://longwaybai.github.io/docs/tmux/keymaps)

The README focuses on repository usage and configuration details. For conceptual explanations, onboarding flow, and walkthrough-style examples, use the companion documentation above.

## 📋 Requirements

- **tmux**: 3.2 or later, 3.3+ recommended
- **Git**: required for cloning the repository and TPM installation
- **Shell**: Bash, Zsh, or a compatible shell
- **Optional**: `reattach-to-user-namespace` for improved macOS clipboard behavior

```bash
tmux -V
```

## 🚀 Installation

### Quick Install

```bash
git clone https://github.com/LongwayBai/tmux-config.git
cd tmux-config
./install.sh
```

`install.sh` performs the following steps:

1. Verifies that `tmux` is installed.
2. Installs TPM when it is missing from the default location.
3. Backs up an existing `~/.tmux.conf` to `~/.tmux.conf.bak`.
4. Copies the repository `tmux/` directory into `~/.tmux/`.
5. Creates the `~/.tmux.conf -> ~/.tmux/tmux.conf` symlink.
6. Starts a temporary `__noop` session to run TPM plugin installation, then removes that session.

### Manual Install

```bash
git clone https://github.com/LongwayBai/tmux-config.git
cd tmux-config

cp ~/.tmux.conf ~/.tmux.conf.bak 2>/dev/null || true
cp -a ./tmux/. ~/.tmux/
ln -sf ~/.tmux/tmux.conf ~/.tmux.conf
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

After entering tmux, run `Ctrl+a Shift+I` to install plugins.

## ⚡ Minimal First Steps

If you are new to tmux, start with this minimum loop:

```bash
tmux new -s demo
tmux ls
tmux attach -t demo
tmux kill-session -t demo
```

- Detach from the current session: `Ctrl+a d`
- Reload the configuration: `Ctrl+a Ctrl+r`
- If plugins are missing, try first: `Ctrl+a Shift+I`

## ⌨️ Common Key Bindings

The unified prefix key is `Ctrl+a`.

### Sessions and Windows

| Key Binding | Description |
| --- | --- |
| `Ctrl+a c` | Create a new window |
| `Ctrl+a d` | Detach from the current session |
| `Ctrl+a r` | Rename the current window |
| `Ctrl+a R` | Rename the current session |
| `Ctrl+a Ctrl+r` | Reload the configuration |
| `Ctrl+a Ctrl+[` | Previous window |
| `Ctrl+a Ctrl+]` | Next window |

### Panes

| Key Binding | Description |
| --- | --- |
| `Ctrl+a \|` | Split left/right |
| `Ctrl+a _` | Split top/bottom |
| `Ctrl+a [` | Select the previous pane |
| `Ctrl+a ]` | Select the next pane |
| `Ctrl+a +` | Zoom / unzoom the current pane |
| `Ctrl+a x` | Kill the current pane |

### Copy Mode and Plugins

| Key Binding | Description |
| --- | --- |
| `Alt+Up` | Enter copy mode |
| `Ctrl+a p` | Paste buffer |
| `Ctrl+a Ctrl+p` | Choose a buffer and paste |
| `Ctrl+a Shift+I` | Install plugins |
| `Ctrl+a Shift+U` | Update plugins |
| `Ctrl+a Alt+u` | Remove plugins no longer listed |

Vi-style copy-mode keys such as `v`, `y`, `Y`, and `D` are available only inside copy mode.

## 🔌 Plugins and Theme

Plugins are managed through [TPM](https://github.com/tmux-plugins/tpm):

- [tmux-plugins/tmux-cpu](https://github.com/tmux-plugins/tmux-cpu)
- [tmux-plugins/tmux-battery](https://github.com/tmux-plugins/tmux-battery)
- [omerxx/tmux-floax](https://github.com/omerxx/tmux-floax)
- [catppuccin/tmux](https://github.com/catppuccin/tmux)

The default theme flavor is **Catppuccin Frappe**. To change it:

```bash
set -g @catppuccin_flavor "frappe"  # mocha | macchiato | frappe | latte
```

Additional plugin-related settings already enabled in this repository include:

- `@floax-text-color 'white'`
- `@floax-change-path 'false'`

## 🧩 Repository Layout

```text
tmux-config/
├── tmux/
│   ├── tmux.conf
│   ├── tmux.remote.conf
│   ├── yank.sh
│   └── renew_env.sh
├── install.sh
├── README.md
├── README_EN.md
└── LICENSE
```

### Key Files

- `tmux/tmux.conf`: main configuration for theme, key bindings, status bar, and plugins
- `tmux/tmux.remote.conf`: remote-session configuration for SSH-oriented workflows
- `tmux/yank.sh`: clipboard helper supporting `pbcopy`, `xsel`, and OSC52 fallback
- `tmux/renew_env.sh`: helper script for refreshing pane environment variables

## 🛠️ Troubleshooting

### Colors are incorrect

```bash
echo $TERM
```

Recommended values are `xterm-256color`, `screen-256color`, or `tmux-256color`.

### Clipboard is not working on macOS

```bash
brew install reattach-to-user-namespace
```

### Plugins are not loading

```bash
~/.tmux/plugins/tpm/bin/install_plugins
```

### Changes do not take effect

```bash
tmux source ~/.tmux.conf
```

You can also run `Ctrl+a Ctrl+r` inside tmux.

## 🤝 Contributing

Issues and pull requests are welcome. If you add user-facing behavior, please keep the companion docs site and the README links in sync.

## 📜 License

See [LICENSE](LICENSE).
