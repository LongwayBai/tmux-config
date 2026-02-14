# tmux-config

[English](README_EN.md) | 简体中文

![demo](https://private-user-images.githubusercontent.com/254935088/549780110-0df9b9da-959b-4f05-b6a4-d04f0243ae10.png?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzEwNDMyNzQsIm5iZiI6MTc3MTA0Mjk3NCwicGF0aCI6Ii8yNTQ5MzUwODgvNTQ5NzgwMTEwLTBkZjliOWRhLTk1OWItNGYwNS1iNmE0LWQwNGYwMjQzYWUxMC5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwMjE0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDIxNFQwNDIyNTRaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT00OWExZThmMDUyNDgzODEwODczYTAzNjg3OWU0YzBiZDk1Nzc5OTc1NjQ1YTVlMmM4MmJkZTZjOGI3ODg4YzRjJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.eEs3u4Z5nQiiZ0cUVuQrQu1LjR4WfBBT_GCeDt-iRKM)

![video](https://private-user-images.githubusercontent.com/254935088/549780297-138e4c95-7b3e-4846-92c5-2d086e225fd2.gif?jwt=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3NzEwNDMyNzQsIm5iZiI6MTc3MTA0Mjk3NCwicGF0aCI6Ii8yNTQ5MzUwODgvNTQ5NzgwMjk3LTEzOGU0Yzk1LTdiM2UtNDg0Ni05MmM1LTJkMDg2ZTIyNWZkMi5naWY_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjYwMjE0JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI2MDIxNFQwNDIyNTRaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT0zMmI3OTExNjkxZjBmYThiMjliZTdiZDE0YWYyODZmNDFlOTIzZWVjNTc4YTFiOTdhNzY1YmI3YWUyN2ZiNzU0JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.B25DbGdFUQRm9cQOHJixNDQFZKzMkuoyjacSuwUd6f8)
功能丰富的 tmux 配置，包含精美的 Catppuccin 主题、智能按键绑定和实用插件。

## ✨ 特性

- 🎨 精美的 Catppuccin Frappe 主题
- ⌨️  为生产力优化的直观按键绑定
- 🖱️  启用鼠标支持
- 📋 增强的剪贴板集成，支持 OSC52
- 🔌 强大的插件（TPM、tmux-cpu、tmux-battery、tmux-floax）
- 🚀 快速响应的配置

## 📋 系统要求

- **tmux**: 版本 3.2 或更高（推荐：3.3）
- **Git**: 用于克隆仓库和安装 TPM
- **Shell**: Bash、Zsh 或兼容的 shell
- **可选**: `reattach-to-user-namespace`（macOS 剪贴板支持）

### 检查 tmux 版本

```bash
tmux -V
```

## 🚀 安装

### 快速安装

运行自动化安装脚本：

```bash
git clone https://github.com/LongwayBai/tmux-config.git
cd tmux-config
./install.sh
```

### 安装脚本的功能：

1. 检查 tmux 是否已安装
2. 如果不存在则安装 TPM (Tmux 插件管理器)
3. 备份现有的 `~/.tmux.conf` 到 `~/.tmux.conf.bak`
4. 复制配置文件到 `~/.tmux/`
5. 创建从 `~/.tmux.conf` 到 `~/.tmux/tmux.conf` 的符号链接
6. 自动安装所有 TPM 插件

### 手动安装

```bash
# 克隆仓库
git clone https://github.com/LongwayBai/tmux-config.git
cd tmux-config

# 备份现有配置
cp ~/.tmux.conf ~/.tmux.conf.bak 2>/dev/null || true

# 复制 tmux 配置
cp -a ./tmux/. ~/.tmux/

# 创建符号链接
ln -sf ~/.tmux/tmux.conf ~/.tmux.conf

# 安装 TPM
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm

# 启动 tmux 并安装插件
tmux new -s setup
# 按下: Ctrl+a 然后 Shift+I (大写 I) 来安装插件
```

## ⌨️ 快捷键绑定

### 前缀键

前缀键从 `Ctrl+b` 更改为 `Ctrl+a`，更容易访问。

### 通用操作

| 快捷键 | 说明 |
|-------|------|
| `Ctrl+a` | 前缀键 |
| `Ctrl+a c` | 创建新窗口（提示输入名称） |
| `Ctrl+a d` | 从会话分离 |
| `Ctrl+a D` | 分离其他客户端 |
| `Ctrl+a Ctrl+e` | 在编辑器中编辑 tmux.conf |
| `Ctrl+a Ctrl+r` | 重新加载配置 |
| `Ctrl+a Ctrl+s` | 切换状态栏显示 |

### 窗口管理

| 快捷键 | 说明 |
|-------|------|
| `Ctrl+a c` | 创建新窗口并提示输入名称 |
| `Ctrl+a r` | 重命名当前窗口 |
| `Ctrl+a R` | 重命名当前会话 |
| `Ctrl+a Ctrl+[` | 上一个窗口 |
| `Ctrl+a Ctrl+]` | 下一个窗口 |
| `Ctrl+a Tab` | 最近使用的窗口 (MRU) |
| `Ctrl+a X` | 关闭当前窗口 |
| `Ctrl+a Ctrl+x` | 关闭所有其他窗口 |
| `Ctrl+a L` | 从另一个会话链接窗口 |

### 面板管理

| 快捷键 | 说明 |
|-------|------|
| `Ctrl+a \|` | 水平分割面板 |
| `Ctrl+a _` | 垂直分割面板 |
| `Ctrl+a [` | 选择上一个面板 |
| `Ctrl+a ]` | 选择下一个面板 |
| `Ctrl+a Ctrl+o` | 交换面板 |
| `Ctrl+a +` | 最大化/还原当前面板 |
| `Ctrl+a x` | 关闭当前面板 |

### 复制模式 (Vi 风格)

| 快捷键 | 说明 |
|-------|------|
| `Alt+Up` | 进入复制模式 |
| `Ctrl+a p` | 粘贴缓冲区 |
| `Ctrl+a Ctrl+p` | 选择粘贴缓冲区 |
| `v` | 开始选择（在复制模式中） |
| `y` | 复制选择内容 |
| `Y` | 复制整行 |
| `D` | 复制到行尾 |
| `Enter` | 复制选择并取消 |
| `Alt+Up/Down` | 向上/下滚动 1 行 |
| `Alt+PageUp/Down` | 滚动半页 |
| `PageUp/PageDown` | 滚动整页 |

### 会话管理

| 快捷键 | 说明 |
|-------|------|
| `Ctrl+a Q` | 关闭当前会话 |
| `Ctrl+a Ctrl+u` | 将当前会话合并到另一个会话 |

## 🔌 插件

此配置通过 TPM 使用以下插件：

- **[TPM](https://github.com/tmux-plugins/tpm)**: Tmux 插件管理器
- **[tmux-cpu](https://github.com/tmux-plugins/tmux-cpu)**: 显示 CPU 和内存使用情况
- **[tmux-battery](https://github.com/tmux-plugins/tmux-battery)**: 显示电池状态
- **[tmux-floax](https://github.com/omerxx/tmux-floax)**: 浮动面板支持
- **[catppuccin](https://github.com/catppuccin/tmux)**: 精美的 Catppuccin 主题

### 管理插件

| 快捷键 | 说明 |
|-------|------|
| `Ctrl+a Shift+I` | 安装插件 |
| `Ctrl+a Shift+U` | 更新插件 |
| `Ctrl+a Alt+u` | 卸载列表中不存在的插件 |

## 🎨 主题自定义

配置使用 **Catppuccin Frappe** 风格。要更改主题，请编辑 `~/.tmux/tmux.conf`：

```bash
set -g @catppuccin_flavor "frappe"  # mocha | macchiato | frappe | latte
```

## 🔧 配置说明

### 常规设置

- **历史记录限制**: 20,000 行
- **Escape 延迟**: 0ms（无延迟）
- **鼠标支持**: 已启用
- **基础索引**: 窗口和面板从 1 开始
- **终端**: 真彩色（24-bit）支持
- **默认 Shell**: 使用系统默认 shell

### 状态栏

状态栏显示：
- **左侧**: 会话名称
- **右侧**: 应用程序、目录、CPU 使用率、主机名（SSH 时）、运行时间、电池

## 🛠️ 故障排除

### 颜色显示不正确

确保您的终端支持真彩色：

```bash
echo $TERM
# 应该是: xterm-256color, screen-256color, 或 tmux-256color
```

### macOS 剪贴板不工作

安装 reattach-to-user-namespace：

```bash
brew install reattach-to-user-namespace
```

### 插件未加载

手动安装插件：

```bash
~/.tmux/plugins/tpm/bin/install_plugins
```

### 配置未加载

重新加载配置：

```bash
tmux source ~/.tmux.conf
```

或在 tmux 内按 `Ctrl+a Ctrl+r`。

## 📝 文件结构

```
tmux-config/
├── tmux/
│   ├── tmux.conf          # 主配置文件
│   ├── tmux.remote.conf   # 远程会话配置
│   ├── yank.sh            # 剪贴板集成脚本
│   └── renew_env.sh       # 环境更新脚本
├── install.sh             # 自动化安装脚本
├── README.md              # 本文件
├── README_EN.md           # 英文文档
└── LICENSE                # 许可证文件
```

## 📜 许可证

详见 [LICENSE](LICENSE) 文件。

## 🙏 致谢

此配置受社区各种 tmux 配置的启发，并使用：
- [Catppuccin](https://github.com/catppuccin) 提供精美主题
- [TPM](https://github.com/tmux-plugins/tpm) 用于插件管理

## 🤝 贡献

欢迎提交 issue 或 pull request 来改进配置！
