# tmux-config

English | [简体中文](README.md)

A feature-rich tmux configuration with beautiful Catppuccin theme, smart key bindings, and useful plugins.

## ✨ Features

- 🎨 Beautiful Catppuccin Frappe theme
- ⌨️  Intuitive key bindings optimized for productivity
- 🖱️  Mouse support enabled
- 📋 Enhanced clipboard integration with OSC52 support
- 🔌 Powerful plugins (TPM, tmux-cpu, tmux-battery, tmux-floax)
- 🚀 Fast and responsive configuration

## 📋 Requirements

- **tmux**: Version 3.2 or higher (recommended: 3.3)
- **Git**: For cloning the repository and TPM installation
- **Shell**: Bash, Zsh, or compatible shell
- **Optional**: `reattach-to-user-namespace` for macOS clipboard support

### Check your tmux version

```bash
tmux -V
```

## 🚀 Installation

### Quick Install

Run the automated installation script:

```bash
git clone https://github.com/LongwayBai/tmux-config.git
cd tmux-config
./install.sh
```

### What the installer does:

1. Checks if tmux is installed
2. Installs TPM (Tmux Plugin Manager) if not present
3. Backs up your existing `~/.tmux.conf` to `~/.tmux.conf.bak`
4. Copies configuration files to `~/.tmux/`
5. Creates a symbolic link from `~/.tmux.conf` to `~/.tmux/tmux.conf`
6. Installs all TPM plugins automatically

### Manual Installation

```bash
# Clone the repository
git clone https://github.com/LongwayBai/tmux-config.git
cd tmux-config

# Backup existing configuration
cp ~/.tmux.conf ~/.tmux.conf.bak 2>/dev/null || true

# Copy tmux configuration
cp -a ./tmux/. ~/.tmux/

# Create symbolic link
ln -sf ~/.tmux/tmux.conf ~/.tmux.conf

# Install TPM
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm

# Start tmux and install plugins
tmux new -s setup
# Press: Ctrl+a then Shift+I (capital I) to install plugins
```

## ⌨️ Key Bindings

### Prefix Key

The prefix key is changed from `Ctrl+b` to `Ctrl+a` for easier access.

### General Operations

| Key Binding | Description |
|------------|-------------|
| `Ctrl+a` | Prefix key |
| `Ctrl+a c` | Create new window (prompts for name) |
| `Ctrl+a d` | Detach from session |
| `Ctrl+a D` | Detach other clients |
| `Ctrl+a Ctrl+e` | Edit tmux.conf in editor |
| `Ctrl+a Ctrl+r` | Reload configuration |
| `Ctrl+a Ctrl+s` | Toggle status bar |

### Window Management

| Key Binding | Description |
|------------|-------------|
| `Ctrl+a c` | Create new window with name prompt |
| `Ctrl+a r` | Rename current window |
| `Ctrl+a R` | Rename current session |
| `Ctrl+a Ctrl+[` | Previous window |
| `Ctrl+a Ctrl+]` | Next window |
| `Ctrl+a Tab` | Last used window (MRU) |
| `Ctrl+a X` | Kill current window |
| `Ctrl+a Ctrl+x` | Kill all other windows |
| `Ctrl+a L` | Link window from another session |

### Pane Management

| Key Binding | Description |
|------------|-------------|
| `Ctrl+a \|` | Split pane horizontally |
| `Ctrl+a _` | Split pane vertically |
| `Ctrl+a [` | Select previous pane |
| `Ctrl+a ]` | Select next pane |
| `Ctrl+a Ctrl+o` | Swap panes |
| `Ctrl+a +` | Zoom/unzoom current pane |
| `Ctrl+a x` | Kill current pane |

### Copy Mode (Vi-style)

| Key Binding | Description |
|------------|-------------|
| `Alt+Up` | Enter copy mode |
| `Ctrl+a p` | Paste buffer |
| `Ctrl+a Ctrl+p` | Choose paste buffer |
| `v` | Begin selection (in copy mode) |
| `y` | Copy selection |
| `Y` | Copy line |
| `D` | Copy to end of line |
| `Enter` | Copy selection and cancel |
| `Alt+Up/Down` | Scroll up/down 1 line |
| `Alt+PageUp/Down` | Scroll half page |
| `PageUp/PageDown` | Scroll full page |

### Session Management

| Key Binding | Description |
|------------|-------------|
| `Ctrl+a Q` | Kill current session |
| `Ctrl+a Ctrl+u` | Merge current session with another |

## 🔌 Plugins

This configuration uses the following plugins via TPM:

- **[TPM](https://github.com/tmux-plugins/tpm)**: Tmux Plugin Manager
- **[tmux-cpu](https://github.com/tmux-plugins/tmux-cpu)**: Display CPU and memory usage
- **[tmux-battery](https://github.com/tmux-plugins/tmux-battery)**: Display battery status
- **[tmux-floax](https://github.com/omerxx/tmux-floax)**: Floating panes support
- **[catppuccin](https://github.com/catppuccin/tmux)**: Beautiful Catppuccin theme

### Managing Plugins

| Key Binding | Description |
|------------|-------------|
| `Ctrl+a Shift+I` | Install plugins |
| `Ctrl+a Shift+U` | Update plugins |
| `Ctrl+a Alt+u` | Uninstall plugins not in list |

## 🎨 Theme Customization

The configuration uses **Catppuccin Frappe** flavor. To change the theme, edit `~/.tmux/tmux.conf`:

```bash
set -g @catppuccin_flavor "frappe"  # mocha | macchiato | frappe | latte
```

## 🔧 Configuration

### General Settings

- **History limit**: 20,000 lines
- **Escape time**: 0ms (no delay)
- **Mouse support**: Enabled
- **Base index**: Windows and panes start at 1
- **Terminal**: True color (24-bit) support
- **Default shell**: Uses your system's default shell

### Status Bar

The status bar displays:
- **Left**: Session name
- **Right**: Application, directory, CPU usage, hostname (if SSH), uptime, battery

## 🛠️ Troubleshooting

### Colors not displaying correctly

Ensure your terminal supports true color:

```bash
echo $TERM
# Should be: xterm-256color, screen-256color, or tmux-256color
```

### Clipboard not working on macOS

Install reattach-to-user-namespace:

```bash
brew install reattach-to-user-namespace
```

### Plugins not loading

Manually install plugins:

```bash
~/.tmux/plugins/tpm/bin/install_plugins
```

### Configuration not loading

Reload configuration:

```bash
tmux source ~/.tmux.conf
```

Or press `Ctrl+a Ctrl+r` inside tmux.

## 📝 Files Structure

```
tmux-config/
├── tmux/
│   ├── tmux.conf          # Main configuration file
│   ├── tmux.remote.conf   # Remote session configuration
│   ├── yank.sh            # Clipboard integration script
│   └── renew_env.sh       # Environment renewal script
├── install.sh             # Automated installation script
├── README.md              # Chinese documentation
├── README_EN.md           # English documentation
└── LICENSE                # License file
```

## 📜 License

See [LICENSE](LICENSE) file for details.

## 🙏 Credits

This configuration is inspired by various tmux configurations from the community and uses:
- [Catppuccin](https://github.com/catppuccin) for the beautiful theme
- [TPM](https://github.com/tmux-plugins/tpm) for plugin management

## 🤝 Contributing

Feel free to open issues or submit pull requests with improvements!
