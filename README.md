<div align="center">

<img src="store-assets/logos/HeroImage-1920x1080.png" alt="myClipClip Banner" width="760" />

# myClipClip

**An Alfred-inspired Windows clipboard manager, smart snippet expander, and multi-provider AI search assistant — built natively with .NET 8, Edge WebView2, and React.**

![Windows](https://img.shields.io/badge/Windows-10%20%7C%2011%20(x64)-0078D6?style=flat-square&logo=windows)
![.NET 8](https://img.shields.io/badge/.NET-8.0-512BD4?style=flat-square&logo=dotnet)
![React](https://img.shields.io/badge/React-19-61DAFB?style=flat-square&logo=react&logoColor=black)
![Idle RAM](https://img.shields.io/badge/Idle%20RAM-~12.6%20MB-10B981?style=flat-square)
![Installer](https://img.shields.io/badge/Installer-1.26%20MB-6366F1?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-slate?style=flat-square)

</div>

---

## Why myClipClip?

Most modern desktop clipboard utilities bundle an entire Chromium browser (Electron), consuming **300–500 MB of RAM** and **100+ MB on disk** just to sit in your system tray.

**myClipClip** pairs a native **C# (.NET 8) Win32 host** with Windows' built-in **Edge WebView2 Runtime** and a **60-second idle auto-unload watchdog** — giving you a crisp Alfred-style UI and streaming Markdown AI window at a fraction of the footprint:

| Metric | myClipClip v2.0 |
| :--- | :--- |
| **App Folder Size** | **3.97 MB** (`myClipClip.exe` is **3.20 MB**) |
| **Windows Setup Installer (NSIS)** | **1.26 MB** |
| **Idle Memory in System Tray** | **~12.6 MB Working Set / ~11.2 MB Private** (1 process) |
| **Idle Clipboard CPU Usage** | **0%** (event-driven Win32 `WM_CLIPBOARDUPDATE`) |
| **Data & Privacy** | **100% Local SQLite** + **Windows DPAPI** encrypted API keys |

---

## Screenshots

| Clipboard History (`Shift+Win+C`) | Smart Snippets & Placeholders (`Shift+Win+X`) |
| :---: | :---: |
| ![Clipboard History](store-assets/screenshots/01-clipboard-history-1920x1080.png) | ![Snippets View](store-assets/screenshots/02-snippets-expander-1920x1080.png) |

| Separate AI Search Markdown Window | Settings & AI Providers |
| :---: | :---: |
| ![AI Search Markdown](store-assets/screenshots/03-ai-markdown-search-1920x1080.png) | ![Settings](store-assets/screenshots/04-settings-providers-1920x1080.png) |

---

## Features

### Clipboard History (`Shift+Win+C`)
- **Multi-format capture**: Plain text, screenshots/images (stored cleanly on disk with previews & dimensions), and copied file paths (`CF_HDROP`).
- **Configurable retention**: Defaults to **10 days** (choose `1d`, `7d`, `10d`, `30d`, `90d`, `Forever`, or custom). Automatic background pruning.
- **Smart organization**: SHA-256 deduplication, pinning (exempt from retention cleanup), instant multi-token search, and source app tagging.
- **Instant auto-paste**: Press `Enter` to restore focus to your previous Windows app and paste automatically via Win32 `SendInput`.

### Smart Snippets & Global Auto-Expansion (`Shift+Win+X`)
- **Collections & tags**: Organize reusable templates or promote any clipboard history item to a snippet in one click.
- **Dynamic placeholders**: Resolved automatically when pasted or expanded:
  - `{date}` (`YYYY-MM-DD`), `{time}` (`HH:mm`), `{time_full}` (`HH:mm:ss`), `{datetime}`, `{isodate}`, `{day}`, `{year}`, `{month}`, `{clipboard}`.
- **Global auto-expansion**: Assign optional trigger keywords (e.g., `!standup`, `!sig`) — typing them in any Windows app replaces them in place (toggleable anytime from the system tray).
- **Backup**: One-click JSON **Import** (merge/replace) and **Export**.

### AI Search — Separate Markdown Result Window (`Tab` or `Shift+Win+A`)
- **Analyze copied text or images**: Send any clipboard item (`Tab`) or your current clipboard (`Shift+Win+A`) to an independent, resizable Markdown AI window.
- **6 Built-in AI Providers (BYOK)** — switch provider and model on the fly:
  | Provider | Protocol | Example Models |
  | :--- | :--- | :--- |
  | **OpenRouter** | OpenAI-compatible SSE | `google/gemini-2.5-flash`, `anthropic/claude-sonnet-4`, `deepseek/deepseek-chat-v3-0324`, `openai/gpt-4o-mini` |
  | **Google Gemini** | Native Gemini SSE | `gemini-2.5-flash`, `gemini-2.5-pro`, `gemini-2.0-flash` |
  | **DeepSeek** | OpenAI-compatible SSE | `deepseek-chat`, `deepseek-reasoner` |
  | **Anthropic Claude** | Native Messages SSE | `claude-sonnet-4-20250514`, `claude-3-5-haiku-latest` |
  | **OpenAI** | OpenAI-compatible SSE | `gpt-4o-mini`, `gpt-4o`, `o3-mini` |
  | **Custom OpenAI-Compatible** | OpenAI-compatible SSE | Any local or remote model (Ollama, LM Studio, Groq, Together, etc.) |
- **Quick Presets & Multi-Turn Chat**: Built-in customizable presets (*Explain*, *Summarize*, *Fix Grammar*, *Translate*, *Code Review*, *Key Takeaways*) plus follow-up questions in the same thread.
- **Rich GFM Markdown**: Live streaming with **Stop** button, tables, syntax-highlighted code blocks with per-block **Copy**, plus **Copy MD**, **Copy Plain**, and **Save as Snippet**.

### Privacy & Security
- **Local-first**: All history and snippets live locally in `%APPDATA%\myClipClip\clipclip.db` (SQLite WAL mode). Zero analytics or telemetry.
- **Encrypted API keys**: All AI keys are encrypted at rest with **Windows DPAPI** (`ProtectedData`).
- See [PRIVACY.md](PRIVACY.md) for the full privacy policy.

---

## Keyboard Shortcuts

| Shortcut | Action |
| :--- | :--- |
| `Shift+Win+C` | Toggle Clipboard History *(configurable in Settings)* |
| `Shift+Win+X` | Toggle Snippets View *(configurable in Settings)* |
| `Shift+Win+A` | Open AI Search on current clipboard *(configurable in Settings)* |
| `Enter` | Auto-paste selected item/snippet into previous app |
| `Shift+Enter` | Copy selected item/snippet without auto-pasting |
| `Tab` | Send selected history item to AI Search |
| `Ctrl+P` | Pin / unpin selected history item |
| `Alt+1` – `Alt+9` | Quick-paste top 9 history items |
| `Ctrl+1` / `Ctrl+2` | Switch between History and Snippets tabs |
| `Ctrl+,` | Open Settings |
| `Esc` | Dismiss launcher |

---

## Architecture

```text
myClipClip/
├── src/
│   ├── shared/                 # Shared TypeScript types, placeholders, AI provider catalog
│   └── renderer/               # React 19 + Tailwind CSS v4 UI + WebView2 JSON-RPC bridge
├── native/
│   ├── MyClipClip/             # Native C# (.NET 8) WinForms + Edge WebView2 host
│   │   ├── Services/           # SQLite (WAL), Win32 hooks/hotkeys/paste, DPAPI + SSE AI client
│   │   └── UI/                 # WebHostForm & WindowManager (60s idle auto-unload)
│   └── MyClipClip.Tests/       # .NET 8 xUnit tests (SQLite, DPAPI, SSE streaming, placeholders)
├── installer/                  # Commercial-free NSIS 3 Windows Setup script
├── packaging/msix/             # Microsoft Store MSIX manifest, tile assets & build script
├── e2e/                        # Playwright CDP end-to-end tests driving native myClipClip.exe
├── docs/                       # GitHub Pages privacy policy (privacy.html)
└── store-assets/               # Microsoft Store 1920x1080 screenshots, logos & listing copy
```

---

## Development & Building from Source

### Prerequisites (Windows 10/11 x64)
- [Node.js 20+](https://nodejs.org/)
- [.NET 8 SDK](https://dotnet.microsoft.com/en-us/download/dotnet/8.0)
- Microsoft Edge WebView2 Runtime *(preinstalled on Windows 11)*
- Optional for packaging: [NSIS 3](https://nsis.sourceforge.io/) (`winget install NSIS.NSIS`)

### Commands

```powershell
# 1. Install frontend & test dependencies
npm install

# 2. Build frontend + native Release binary into dist/myClipClip/
npm run build:win

# 3. Build and launch immediately
npm run dev

# 4. Run TypeScript type-check + Vitest + .NET 8 xUnit unit tests
npm run typecheck
npm test

# 5. Run Playwright CDP end-to-end tests against the real native myClipClip.exe
npm run test:e2e

# 6. Build Windows Setup installer (dist/myClipClip-Setup-2.0.0.exe, ~1.26 MB)
npm run build:installer

# 7. Build Microsoft Store MSIX package (auto-restores makeappx.exe via NuGet)
npm run build:msix          # Unsigned self-contained MSIX for Partner Center upload
npm run build:msix:test     # Self-signed MSIX for local sideload testing
```

---

## License

MIT — built by **Kijo Kim**.
