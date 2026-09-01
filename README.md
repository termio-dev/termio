# Termio

**Desktop terminal & SSH workspace manager**

Termio organizes your local shells and SSH connections into workspaces with split-pane layouts, per-connection file storage, a built-in command composer, and an AI copilot — all in a single, fast native app.

---

## Download

| Platform | Format | Download | Best for |
|----------|--------|----------|----------|
| macOS | `.dmg` | **[Termio-macos-universal.dmg](https://github.com/termio-dev/termio/releases/latest/download/Termio-macos-universal.dmg)** | Apple silicon and Intel — universal binary |
| Windows | `.exe` | **[Termio-windows-x64-setup.exe](https://github.com/termio-dev/termio/releases/latest/download/Termio-windows-x64-setup.exe)** | Standard installer |
| Linux | `.AppImage` | **[Termio-linux-x86_64.AppImage](https://github.com/termio-dev/termio/releases/latest/download/Termio-linux-x86_64.AppImage)** | Any distro, no install — just `chmod +x` and run |
| Linux | `.deb` | **[Termio-linux-x86_64.deb](https://github.com/termio-dev/termio/releases/latest/download/Termio-linux-x86_64.deb)** | Debian, Ubuntu, Mint, Pop!_OS |
| Linux | `.rpm` | **[Termio-linux-x86_64.rpm](https://github.com/termio-dev/termio/releases/latest/download/Termio-linux-x86_64.rpm)** | Fedora, RHEL, openSUSE |

All builds are `x86_64`; macOS is a universal binary. Windows is also available from the Microsoft Store (MSIX). Checksums, signatures, and older versions live on the [releases page](https://github.com/termio-dev/termio/releases).

---

## Features

### Terminal & connections
- **Local shells and SSH** in one unified interface
- **Split-pane layouts** — horizontal and vertical splits within each tab
- **Tabs** — multiple session groups, each with its own layout
- **Connection tree** — organize connections into folders, reorder via drag-and-drop, pin favorites
- **Startup commands** — auto-run commands when a session connects

### Workspace system
- **Workspaces** group connections, files, and layouts into portable project contexts
- **Per-connection files** — store scripts, configs, and notes directly inside each connection
- **Script detection** — `.sh`, `.py`, `.js`, `.ts`, `.rb`, `.pl` files get a one-click run button
- **File editor** — CodeMirror for files with extensions, plain textarea for the rest
- **AI memory** — per-connection context file that persists across AI sessions

### Command composer
- Multi-line command editor with syntax highlighting
- Stage commands before running — review and edit safely
- Execute into the active terminal pane

### AI Copilot
- Sidebar AI assistant with streaming responses
- Runs terminal commands, edits files, and stages commands via tool use
- Context-aware — sees your active terminal output, connection info, and files
- Destructive command detection (rm, mkfs, git force, etc.) with confirmation
- Works with any OpenAI-compatible API endpoint
- Separate model setting for background memory summarization

### Security
- **SSH credentials stored in the native OS credential store** — never in project files
  - macOS: Keychain
  - Linux: Secret Service (GNOME Keyring / KDE Wallet)
  - Windows: Windows Credential Manager
- Credentials are copied, moved, and deleted alongside their connections

### UI
- Unified dark and light themes across terminal, editor, and app chrome
- Command palette (`Cmd+K` / `Ctrl+K`) for quick navigation
- Configurable keyboard shortcuts
- Resizable sidebar, file panel, and AI panel

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Desktop runtime | Tauri v2 (Rust backend) |
| Frontend | React 19, TypeScript, Zustand, Vite |
| Terminal | xterm.js |
| Editor | CodeMirror 6 |
| Local PTY | `portable-pty` |
| SSH | `ssh2` (Rust, single-threaded session with OS pipe I/O) |
| AI | OpenAI-compatible streaming client, CopilotKit |

---

## Installation

### macOS
1. Download `.dmg` from [Releases](https://github.com/termio-dev/termio/releases)
2. Drag **Termio** to Applications
3. Open the app

### Linux

**AppImage**
```bash
chmod +x Termio-linux-x86_64.AppImage
./Termio-linux-x86_64.AppImage
```

**Debian / Ubuntu**
```bash
sudo apt install ./Termio-linux-x86_64.deb
```

**Fedora / RHEL / openSUSE**
```bash
sudo dnf install ./Termio-linux-x86_64.rpm
```

> Credential storage requires `libsecret-tools` (pre-installed on most GNOME/KDE desktops).
> Install if missing: `sudo apt install libsecret-tools` or `sudo dnf install libsecret`.

### Windows
1. Download `.exe` from [Releases](https://github.com/termio-dev/termio/releases)
2. Run the installer

---

## Changelog

### 1.2.3 — 1 September 2026

**Fixed**
- SSH handshake failures now name the real cause instead of reporting "Unable to exchange encryption keys" for every mismatch
- Windows: connections can be added to folders again
- Linux: blank window on Ubuntu 26.04
- Linux: freeze when returning focus to the window, most noticeable with multiple monitors
- Workspaces whose folder was deleted are removed from the list instead of failing on every attempt

**Added**
- Collapsible sidebar — status bar button or `Cmd+B` (`Ctrl+Shift+B` on Windows and Linux). Remembers its state and width
- `.deb` and `.rpm` packages alongside the AppImage
- Optional system SSH client per connection, for servers requiring algorithms the built-in client cannot negotiate, or when you need `~/.ssh/config`, `ProxyJump`, certificates or agent forwarding

**Changed**
- Dependencies updated, including the SSH and terminal stacks
- Package-manager installs no longer offer in-app updates

### 1.2.2 — 8 May 2026
- Fixed system tools failing in terminals launched from the Linux AppImage
- Light theme refinements

### 1.2.1 — 20 April 2026
- Microsoft Store packaging (MSIX) for Windows

### 1.2.0 — 6 April 2026
- WSL and PowerShell session backends on Windows, selectable per connection

### 1.1.0 — 4 April 2026
- Files open in your own editor, selectable in settings
- Faster tab switching

---

## License

See [LICENSE](LICENSE) for details.
