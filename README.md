# Chops - Linux Edition

A Linux port of [Chops](https://github.com/Shpigford/chops) - Your AI agent skills, finally organized.

![Chops Screenshot](screenshot.png)

## Overview

Chops is a desktop application for discovering, organizing, and editing AI coding agent skills across multiple tools:

- **Claude Code** - `~/.claude/skills/`
- **Cursor** - `~/.cursor/skills/`, `~/.cursor/rules`
- **Windsurf** - `~/.codeium/windsurf/memories/`, `~/.windsurf/rules`
- **Codex** - `~/.codex/skills/`
- **Amp** - `~/.config/amp/skills/`
- **Copilot** - `~/.copilot/skills/`
- **OpenCode** - `~/.config/opencode/skills/`
- **Global Agents** - `~/.agents/skills/`

## Features

- **Multi-tool support** — Claude Code, Cursor, Codex, Windsurf, Copilot, Aider, Amp, OpenCode, and more
- **Built-in editor** — Monospaced editor with auto-save
- **Collections** — Organize skills without modifying source files
- **Real-time file watching** — Instant updates on disk changes (using inotify)
- **Full-text search** — Search across name, description, and content
- **Create new skills** — Generates correct boilerplate per tool
- **Favorites** — Mark your most-used skills for quick access

## Installation

### From Zip (Recommended)

1. Download `chops-linux-1.0.0.zip`
2. Extract it: `unzip chops-linux-1.0.0.zip`
3. Run the application:
   ```bash
   cd linux-unpacked
   ./chops-linux
   ```

### Requirements

- Linux x64
- glibc 2.28 or later (Ubuntu 18.04+, Debian 10+, Fedora 29+, etc.)

## Building from Source

### Prerequisites

- Node.js 18+
- npm or bun

### Build Steps

```bash
# Clone the repository
git clone https://github.com/Shpigford/chops.git
cd chops

# Install dependencies (Linux port)
npm install

# Build TypeScript
npm run build

# Development
npm start

# Create distribution
npm run dist:zip
```

## Project Structure

```
chops-linux/
├── src/
│   ├── main/           # Electron main process
│   │   ├── main.ts     # Application entry point
│   │   └── preload.ts  # IPC bridge for renderer
│   ├── renderer/       # UI (HTML/CSS/JS)
│   │   ├── index.html  # Main window layout
│   │   └── app.ts      # UI logic
│   ├── services/       # Backend services
│   │   ├── database.ts # SQLite operations
│   │   ├── scanner.ts  # Skill file scanner
│   │   └── parser.ts   # Frontmatter parsing
│   └── shared/         # Shared types
│       └── types.ts    # TypeScript interfaces
├── dist/               # Compiled output
└── release/            # Distribution packages
```

## Architecture

This Linux port uses:

- **Electron** - Cross-platform desktop framework
- **SQLite** (better-sqlite3) - Local database for skill metadata
- **Chokidar** - File watching (wraps inotify on Linux)
- **TypeScript** - Type-safe development

### Key Differences from macOS Version

| Feature | macOS Version | Linux Version |
|---------|--------------|---------------|
| UI Framework | SwiftUI | Electron/HTML/CSS |
| Database | SwiftData | SQLite |
| File Watching | FSEvents | inotify (via chokidar) |
| Auto-update | Sparkle | Manual (future: GitHub releases) |
| Code Editor | NSTextView | HTML textarea |

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl+S` | Save current skill |
| `Escape` | Close modal dialogs |

## Supported Skill Formats

- **SKILL.md** — Directory-based skills with frontmatter
- **AGENTS.md** — Alternative directory format
- **.md files** — Loose markdown files with optional frontmatter
- **.mdc files** — Cursor rules format



## License

MIT — see [LICENSE](LICENSE).

## Credits

- Original macOS version by [Josh Pigford](https://github.com/Shpigford)
- Linux port by [Vineesh Kumar] (https://github.com/vineeshkumarpv/)

## Contributing

Contributions are welcome! Please feel free to submit issues and pull requests.
