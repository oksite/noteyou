# NOTEYOU

[中文](README.md) | [English](README_EN.md)

> NOTEYOU is currently maintained by an individual developer. Features and data structures may change. Back up important documents before using a preview release.

NOTEYOU is a local-first Markdown desktop editor built with Tauri 2, Next.js, and CodeMirror 6.

It requires no account, provides no cloud synchronization, and uses no proprietary note database. Documents are stored locally as standard `.md` or `.markdown` files that can be opened with any other editor.


## Screenshots

### Dark Theme

![NOTEYOU dark theme interface](/dark.jpg)

### Light Theme

![NOTEYOU light theme interface](/light.jpg)


## Key Features

### File and Folder Management

- Manage folders and Markdown documents in a tree view
- Create, rename, and delete files or folders
- Expand and collapse nested folders
- Filter the file tree by name
- Drag files or folders up and down to reorder items within the same directory
- Persist custom ordering across application restarts
- Display the active storage location in the status bar

### Markdown Editing

- CodeMirror 6 editor with Markdown syntax highlighting
- Open multiple documents in tabs
- Editor, split, and preview view modes
- GFM, tables, code blocks, links, lists, and other common syntax
- Quick formatting controls for headings, bold, italic, links, and lists
- Automatic saving 1.2 seconds after typing stops
- Manual saving with `Ctrl/Cmd + S`
- Confirmation before closing an unsaved tab

### Interface

- Instant switching between Chinese and English
- Persisted language preference
- Light and dark themes
- Persisted theme preference
- Native Windows title bar theme synchronization
- In-app dialogs for creation, renaming, deletion, and unsaved changes

## Technology

| Layer | Technology |
| --- | --- |
| Desktop shell and filesystem | Tauri 2 / Rust |
| Frontend | Next.js 15 / React 19 / TypeScript |
| Editor | CodeMirror 6 |
| Markdown | marked + DOMPurify |
| Icons | Lucide React |
| Testing | Vitest + Testing Library |

Next.js is statically exported and bundled directly into the desktop application by Tauri. All local filesystem operations are performed by the Rust backend through Tauri IPC.

## Download

> The current preview release provides Windows x64 packages only.

[Download the latest NOTEYOU pre-release](https://github.com/oksite/noteyou/releases)

Windows users can choose either the NSIS `.exe` installer or the `.msi` package on the Releases page. NOTEYOU requires Microsoft Edge WebView2 Runtime, which is normally preinstalled on modern Windows systems.

## Data Storage

NOTEYOU first attempts to create the following directory beside the executable:

```text
NOTEYOU/DB/
```

If the installation directory is not writable, it automatically falls back to the operating system's application data directory. The status bar displays the complete path currently in use.

Custom ordering is stored in a hidden `.noteyou-order.json` file inside the workspace. Markdown documents remain standard files.

Regularly backing up the complete workspace shown in the status bar is recommended.

## Security and Privacy

- Filesystem operations are handled by the Rust backend
- Only safe paths relative to the workspace are accepted
- Absolute paths and `..` path traversal are rejected
- Symbolic links are ignored
- File reading and writing are limited to `.md` and `.markdown`
- Characters unsupported in Windows file names are rejected
- Preview HTML is sanitized with DOMPurify
- No account, document uploads, or telemetry collection

## License

This project is licensed under the [Mulan Permissive Software License, Version 2](LICENSE).
