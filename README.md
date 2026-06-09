# Screen Recorder

A clean, dark-themed screen recorder built with Tauri v2 + vanilla HTML/CSS/JS.

**Features:** screen capture · system audio · mic (off by default) · camera PiP · audio level meters · crash recovery · quality presets up to 4K

---

## Build via GitHub (no local Rust needed)

1. **Fork or push this repo to GitHub**
2. Go to **Actions** tab → the `Build Windows` workflow runs automatically on every push to `main`
3. When it finishes, click the run → scroll to **Artifacts** → download:
   - `screen-recorder-setup-windows` — NSIS installer (`.exe`)
   - `screen-recorder-msi-windows` — MSI installer
   - `screen-recorder-portable-windows` — standalone `.exe`

### Automatic versioned releases

Every push to `main` now auto-generates a new tag in the format `v<yyyymmdd>-<commit-sha>` and creates a GitHub Release with the built installers attached.

---

## Build locally (optional)

### Prerequisites

- [Rust](https://rustup.rs/) (stable)
- [Tauri v2 system deps for Windows](https://tauri.app/start/prerequisites/) — WebView2 is pre-installed on Windows 10/11

```bash
# Install Tauri CLI
cargo install tauri-cli --version "^2.0" --locked

# Run in dev mode (opens the app window)
cargo tauri dev

# Build release installers
cargo tauri build
# Output: src-tauri/target/release/bundle/
```

---

## Project structure

```
screen-recorder/
├── index.html              ← Frontend (single file)
├── Cargo.toml              ← Workspace
├── .github/workflows/
│   └── build.yml           ← GitHub Actions CI/CD
└── src-tauri/
    ├── Cargo.toml
    ├── build.rs
    ├── tauri.conf.json      ← App config (window size, bundle, icons)
    ├── icons/               ← App icons (add your own)
    └── src/
        ├── main.rs
        └── lib.rs
```

---

## Icons

Drop your icon files into `src-tauri/icons/`:

| File | Size |
|------|------|
| `32x32.png` | 32×32 |
| `128x128.png` | 128×128 |
| `128x128@2x.png` | 256×256 |
| `icon.ico` | Windows icon |
| `icon.icns` | macOS icon |

Generate all sizes from a single PNG with:

```bash
cargo install tauri-cli --locked
cargo tauri icon path/to/your-icon-1024.png
```

---

## Keyboard shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl + R` | Start recording |
| `Ctrl + Shift + S` | Stop recording |
| `Ctrl + Space` | Pause / Resume |
