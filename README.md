# Termio

**Desktop terminal & SSH workspace manager**

Termio organizes your local shells and SSH connections into workspaces with split-pane layouts, per-connection file storage, a built-in command composer, and an AI copilot — all in a single, fast native app.

---

## Download

**[Get the latest release](https://github.com/termio-dev/termio/releases)**

| Platform | Format |
|----------|--------|
| macOS | `.dmg` |
| Linux | `.AppImage` |
| Windows | `.exe` |

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
```bash
chmod +x Termio.AppImage
./Termio.AppImage
```

> Credential storage requires `libsecret-tools` (pre-installed on most GNOME/KDE desktops).
> Install if missing: `sudo apt install libsecret-tools` or `sudo dnf install libsecret`.

### Windows
1. Download `.exe` from [Releases](https://github.com/termio-dev/termio/releases)
2. Run the installer

---

## License

See [LICENSE](LICENSE) for details.
