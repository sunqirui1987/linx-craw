# Aicraw

AI personal assistant powered by Qiniu Cloud. Supports DingTalk, Feishu, QQ, and more.

![LinCraw Chat](docs/image.png)

## Install

```bash
git clone https://github.com/sunqirui1987/linx-craw.git
cd linx-craw
pip install -e .
cd console && pnpm install && pnpm run build
cp -R dist/* ../src/aicraw/console/
```

Requires Python 3.10+, Node.js 20+, pnpm.

## Quick Start
```bash
aicraw app
```

Open http://127.0.0.1:8088/ in your browser.

## Electron Desktop Client

Following the structure of [qiniu-aistudio](https://github.com/qiniu/qiniu-aistudio), an Electron client is provided that bundles the Python backend.

### Development

```bash
# Terminal 1: Start Python backend
aicraw app

# Terminal 2: Start Electron
pnpm install
pnpm approve-builds  # If Electron fails to install, run this then pnpm install again
pnpm run dev:electron
```

### Build (with Python bundled)

**Two-step flow**: First compile Python to exe, then package with Electron.

```bash
pnpm install

# Step 1: Compile Python to executable (run on target platform, e.g. run on Windows for Windows build)
pnpm run build:python

# Step 2: Package Electron
pnpm run build:electron        # Current platform
pnpm run build:electron:mac   # macOS
pnpm run build:electron:win   # Windows
```

Output is in `release/`. `build:python` builds the console, copies to `src/aicraw/console`, and packages Python with PyInstaller to `python-dist/Aicraw`; `build:electron:*` bundles `python-dist` with Electron.

## Qiniu Cloud Setup

For Qiniu MaaS (qnaigc), go to **Settings → Models** in the console, select Qiniu MaaS, and enter your API Key. Please [log in to Qiniu Console](https://portal.qiniu.com/ai-inference/api-key) to get your API Key.
