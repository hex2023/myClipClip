# Microsoft Partner Center — Ready-to-Paste Store Listing Copy

Use the exact fields below when filling out **Partner Center → Submission → Properties / Store listings / Submission options**.

---

## Properties
- **Category**: Productivity
- **Subcategory**: Utilities & tools
- **Privacy Policy URL**: Host `docs/privacy.html` (e.g. via GitHub Pages: `https://<your-github-username>.github.io/<repo-name>/privacy.html`) or paste `PRIVACY.md` into a public Notion/website page.

---

## Store Listing — Short Description (max 270 chars)
> Fast, lightweight Alfred-inspired Windows clipboard manager with configurable history, smart snippet auto-expansion, global hotkeys (Shift+Win+C / Shift+Win+X), and a separate streaming Markdown AI Search window supporting OpenRouter, Gemini, DeepSeek, Claude, OpenAI & Ollama.

## Store Listing — Full Description
> **myClipClip** brings Alfred-style clipboard speed and multi-provider AI intelligence to Windows — engineered natively in .NET 8 + Edge WebView2 for ultra-low memory usage (~12 MB idle in the system tray).
>
> **Clipboard History (Shift+Win+C)**
> • Automatically captures copied text, screenshots/images, and file paths via event-driven Windows notifications (zero idle polling).
> • Configurable retention period (10 days default — choose 1, 7, 10, 30, 90 days, Forever, or custom).
> • Smart deduplication, pinning (exempt from auto-pruning), instant fuzzy search, source app tagging, and one-keystroke auto-paste directly back into your active app.
>
> **Smart Snippets & Global Auto-Expansion (Shift+Win+X)**
> • Save reusable templates organized by collections and tags, or promote any clipboard item into a snippet in one click.
> • Dynamic placeholders resolved on paste: {date}, {time}, {datetime}, {isodate}, {day}, and {clipboard}.
> • Global auto-expansion keywords: assign a short trigger (like !standup) and type it in any Windows app to expand automatically.
> • Full JSON import & export backup.
>
> **Separate AI Search Markdown Window (Tab or Shift+Win+A)**
> • Send any clipboard text or image straight to AI without leaving your workflow.
> • Switch providers and models on the fly: OpenRouter, Google Gemini, DeepSeek, Anthropic Claude, OpenAI, and Custom OpenAI-Compatible endpoints (Ollama, LM Studio, Groq, etc.).
> • Built-in customizable prompt presets (Explain, Summarize, Fix Grammar, Translate, Code Review, Key Takeaways) plus multi-turn follow-up chat.
> • Real-time streaming GitHub-Flavored Markdown with tables, syntax-highlighted code blocks, one-click Copy Code, Copy Markdown, Copy Plain Text, and Save as Snippet.
>
> **Privacy-First & Lightweight**
> • 100% local SQLite database — zero telemetry, zero cloud sync required.
> • API keys encrypted locally with Windows DPAPI.
> • Automatically unloads hidden UI after 60 seconds of inactivity to keep idle RAM around ~12 MB.

## Product Features (Bullet List)
1. Clipboard history for text, images & files with configurable retention (default 10 days) and pinning
2. Instant auto-paste back into your active Windows app on Enter
3. Snippets library with collections, tags, dynamic placeholders ({date}, {time}, {clipboard}) & JSON import/export
4. Global snippet auto-expansion keywords across any Windows application
5. Configurable global hotkeys: Shift+Win+C (History), Shift+Win+X (Snippets), Shift+Win+A (AI Search)
6. Separate streaming Markdown AI Search window supporting OpenRouter, Gemini, DeepSeek, Claude, OpenAI & local Ollama
7. Syntax-highlighted code blocks with one-click Copy and multi-turn follow-up chat
8. Local-first privacy with Windows DPAPI encrypted API keys and ~12 MB idle tray RAM

## Search Terms (up to 7)
1. `clipboard manager`
2. `clipboard history`
3. `text expander`
4. `snippets`
5. `alfred windows`
6. `ai assistant`
7. `markdown ai`

## What's New in Version 2.0.0
> Initial Microsoft Store release featuring a native .NET 8 + Edge WebView2 architecture (~12 MB idle RAM), event-driven clipboard history (text, images & files), snippet auto-expansion with dynamic placeholders, configurable global hotkeys, and a separate streaming Markdown AI Search window supporting 6 AI providers.

---

## Submission Options — Notes for Certification (Copy-Paste Verbatim)
> myClipClip is a Win32 desktop productivity utility (clipboard manager, snippet expander, and BYOK AI search assistant). It declares the `runFullTrust` capability for the following core user-facing features:
> 1. Monitoring Windows clipboard updates (`AddClipboardFormatListener` / `WM_CLIPBOARDUPDATE`) and registering configurable global hotkeys (`Shift+Win+C`, `Shift+Win+X`, `Shift+Win+A`) from the system tray.
> 2. Auto-pasting a user-selected history item or snippet back into their previously active application (`SetForegroundWindow` + `SendInput` Ctrl+V), and running an optional user-toggleable keyboard hook (`WH_KEYBOARD_LL`) for expanding user-defined snippet trigger keywords (e.g., `!standup`).
>
> Testing instructions:
> - Launch myClipClip (on first run the launcher opens automatically; afterwards it runs in the system tray).
> - Copy any text or screenshot in another app, then press `Shift+Win+C` (or click the tray icon) to view history and press Enter to paste.
> - Press `Shift+Win+X` to open Snippets, create/edit snippets, or preview `{date}`/`{clipboard}` placeholders.
> - AI Search is BYOK (Bring Your Own Key): users optionally enter their own API key in Settings → AI Providers (encrypted locally via Windows DPAPI) or point Custom OpenAI-Compatible to a local Ollama endpoint. All core clipboard and snippet features work fully offline with no account or API key required.
