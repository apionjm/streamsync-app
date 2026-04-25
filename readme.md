```markdown
# StreamSync Desktop App 🖥️

<p align="center">
  <img src="https://streamsync.apionlabs.org/logo.png" alt="StreamSync Logo" width="200"/>
</p>

<p align="center">
  <strong>Share your screen. Connect face-to-face. Instantly.</strong>
</p>

<p align="center">
  <a href="#features">Features</a> •
  <a href="#how-it-works">How It Works</a> •
  <a href="#installation">Installation</a> •
  <a href="#building">Building</a> •
  <a href="#privacy">Privacy</a>
</p>

---

> **StreamSync** enables real-time screen sharing with two-way video chat — no accounts, no downloads, no friction. Just share a code and start collaborating.

🔗 [Launch StreamSync Web App →](https://streamsync.apionlabs.org/app/)

---

## ✨ Features

| Feature                        | Description                                                                                                                                           |
| ------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------- |
| 🖥 **Instant Screen Sharing**  | Share your entire screen, a specific window, or browser tab with a single click. High-quality video with adaptive bitrate for smooth playback.        |
| 👥 **Two-Way Video Chat**      | See and hear each other while collaborating. Both participants have camera and microphone controls with real-time audio/video synchronization.        |
| 🔐 **Peer-to-Peer Privacy**    | Connections happen directly between devices. Your screen content and video never pass through our servers — only signaling data for connection setup. |
| 🔗 **Simple Room Codes**       | Generate a unique 6-character code to share. No accounts, no sign-ups. Just share the code or a link and start connecting instantly.                  |
| ⚡ **Low-Latency Performance** | Optimized WebRTC implementation with smart relay fallback ensures minimal delay, even on slower connections.                                          |
| 🎨 **Clean, Focused UI**       | Minimal interface designed for focus. Dark mode by default with intuitive controls that stay out of your way while you work.                          |

---

## 🔄 How StreamSync Works

Three simple steps to start collaborating in seconds:

### 1️⃣ Host starts session

- Click "Host", share your screen when prompted
- Allow camera/mic access
- A unique room code is generated instantly

### 2️⃣ Share the code

- Copy the room code or share the auto-generated link
- Send via chat, email, or messaging app

### 3️⃣ Guest joins & connect

- Guest enters the code or clicks the link
- Grants camera/mic access
- You're connected — screen sharing and video chat live 🎉
```

┌─────────────────┐ ┌─────────────────┐ ┌─────────────────┐
│ HOST │ │ SHARE CODE │ │ GUEST │
│ │ │ │ │ │
│ • Click Host │────▶│ • Copy code │────▶│ • Enter code │
│ • Share screen │ │ • Send link │ │ • Allow perms │
│ • Allow camera │ │ │ │ • Connect! │
└─────────────────┘ └─────────────────┘ └─────────────────┘
│
▼
🎉 Peer-to-Peer Connection Established

````

---

## 📦 Installation

### Option 1: Download Pre-built Installer (Windows)

1. Visit the [Releases](https://github.com/apionlabs/streamsync-desktop/releases) page
2. Download `StreamSync Setup x.x.x.exe`
3. Run the installer and follow the prompts
4. Launch **StreamSync** from your Start Menu or Desktop

### Option 2: Build from Source

#### Prerequisites
- Node.js 18.x or higher ([Download](https://nodejs.org/))
- npm or yarn package manager
- Git

#### Steps
```bash
# Clone the repository
git clone https://github.com/apionlabs/streamsync-desktop.git
cd streamsync-desktop

# Install dependencies
npm install

# Run in development mode
npm start

# Build for production
npm run dist
````

📁 Built installers will appear in the `dist/` folder:

```
dist/
├── StreamSync Setup 1.0.0.exe    ← Windows installer (NSIS)
├── win-unpacked/                  ← Portable Windows app
├── StreamSync-1.0.0.dmg           ← macOS installer
├── StreamSync-1.0.0.AppImage      ← Linux portable app
└── latest.yml                     ← Auto-update metadata
```

---

## 🛠️ Building for Different Platforms

| Platform    | Command                   | Output Format       | Requirements        |
| ----------- | ------------------------- | ------------------- | ------------------- |
| **Windows** | `npm run dist -- --win`   | `.exe` (NSIS)       | Windows or Wine     |
| **macOS**   | `npm run dist -- --mac`   | `.dmg`              | macOS + Xcode CLI   |
| **Linux**   | `npm run dist -- --linux` | `.AppImage`, `.deb` | Linux (glibc 2.28+) |

### Build Options

```bash
# Build for specific architecture
npm run dist -- --win --x64
npm run dist -- --win --ia32
npm run dist -- --win --arm64

# Build portable version only
npm run dist -- --win --dir

# Publish to GitHub Releases
npm run dist -- --win --publish always
```

### Customizing the Build

Edit `package.json` build configuration:

```json
{
  "build": {
    "appId": "org.apionlabs.streamsync",
    "productName": "StreamSync",
    "icon": "build/icon.png",
    "win": {
      "target": ["nsis", "portable"],
      "artifactName": "${productName}-Setup-${version}.${ext}",
      "requestedExecutionLevel": "asInvoker"
    },
    "mac": {
      "target": ["dmg", "zip"],
      "category": "public.app-category.productivity",
      "notarize": true
    },
    "linux": {
      "target": ["AppImage", "deb"],
      "category": "Network",
      "desktop": {
        "Name": "StreamSync",
        "Comment": "Real-time screen sharing with video chat"
      }
    },
    "nsis": {
      "oneClick": false,
      "allowToChangeInstallationDirectory": true,
      "createDesktopShortcut": true,
      "createStartMenuShortcut": true,
      "shortcutName": "StreamSync"
    },
    "files": [
      "main.js",
      "preload.js",
      "renderer/**/*",
      "package.json",
      "build/icon.png",
      "!**/*.{md,log,gitignore}",
      "!node_modules/*/{CHANGELOG.md,README.md,readme.md}"
    ]
  }
}
```

---

## ▶️ Usage Guide

### Launching the App

1. Open StreamSync from your desktop or applications folder
2. Choose your role:
   - **🎬 Host**: Start a new session and share your screen
   - **🔗 Join**: Enter a room code to connect with a host

### Hosting a Session

```
1. Click "Host" button
2. Select screen/window/tab to share when prompted
3. Allow camera and microphone permissions
4. Copy the generated 6-character room code
5. Share the code or link with your collaborator
6. Wait for guest to join — connection is automatic!
```

### Joining a Session

```
1. Click "Join" button
2. Enter the 6-character room code provided by host
   OR click the shared link directly
3. Allow camera and microphone permissions
4. You're connected! View host's screen and video chat
```

### In-Session Controls

| Control           | Icon | Function                         |
| ----------------- | ---- | -------------------------------- |
| Toggle Camera     | 📷   | Enable/disable your video feed   |
| Toggle Microphone | 🎙   | Mute/unmute your audio           |
| Stop Screen Share | ⏹    | End your screen sharing session  |
| Leave Room        | 🚪   | Disconnect and exit the session  |
| Copy Room Code    | 🔗   | Copy shareable link to clipboard |

### Keyboard Shortcuts

| Shortcut             | Platform      | Action                         |
| -------------------- | ------------- | ------------------------------ |
| `Ctrl+Shift+I`       | Windows/Linux | Open Developer Tools           |
| `Cmd+Option+I`       | macOS         | Open Developer Tools           |
| `Ctrl+R`             | Windows/Linux | Reload application             |
| `Cmd+R`              | macOS         | Reload application             |
| `F11` / `Ctrl+Cmd+F` | All           | Toggle fullscreen mode         |
| `Esc`                | All           | Exit fullscreen / Close modals |

---

## 🔐 Privacy & Security

### End-to-End Encryption

- All media streams use **DTLS-SRTP** encryption
- Signaling data transmitted over **WSS** (WebSocket Secure)
- No media content is ever stored or logged

### Peer-to-Peer Architecture

```
┌─────────────┐                    ┌─────────────┐
│   Host      │◀────WebRTC───────▶│   Guest     │
│   Device    │   Encrypted P2P    │   Device    │
└─────────────┘                    └─────────────┘
         │                              │
         │                              │
         ▼                              ▼
┌─────────────────────────────────────────┐
│         Signaling Server (Apionlabs)    │
│  • Only exchanges connection metadata   │
│  • Never accesses screen/video content  │
│  • No persistent data storage           │
└─────────────────────────────────────────┘
```

### Data Collection Policy

✅ **We DO collect:**

- Anonymous crash reports (opt-in via settings)
- Aggregate usage metrics (session duration, connection success rate)

❌ **We DO NOT collect:**

- Screen content or shared media
- Camera/microphone audio or video
- Room codes or participant identifiers
- IP addresses beyond connection routing
- Personal information or account data

### Platform Permissions

#### macOS

First-time screen sharing requires manual permission:

```
System Settings → Privacy & Security → Screen Recording → StreamSync ✓
```

> 💡 If permissions don't appear, restart the app after installation.

#### Windows

- Screen sharing works out-of-the-box
- Camera/mic permissions prompted on first use
- Firewall may prompt for network access — allow for P2P connectivity

#### Linux

- Works with PipeWire (modern distros) or X11
- Wayland support requires `xdg-desktop-portal`
- Camera access may require `v4l2loopback` module

---

## 🧰 Technical Architecture

### Tech Stack

```
Frontend Framework:   React 18 + TypeScript
Build Tool:           Vite 5
State Management:     Zustand
WebRTC Library:       PeerJS + native RTCPeerConnection
Desktop Runtime:      Electron 30 + electron-builder
Styling:              Tailwind CSS + CSS Modules
Icons:                Lucide React + custom SVG
```

### Project Structure

```
streamsync-desktop/
├── main.js                 # Electron main process
├── preload.js              # Preload script (context bridge)
├── package.json            # Dependencies & build config
├── README.md               # This file
│
├── src/
│   ├── renderer/           # React frontend
│   │   ├── components/     # UI components
│   │   ├── hooks/          # Custom React hooks
│   │   ├── lib/            # WebRTC utilities
│   │   ├── App.tsx         # Root component
│   │   └── main.tsx        # Entry point
│   │
│   └── shared/             # Code shared between main/renderer
│       └── types.ts        # TypeScript interfaces
│
├── build/
│   ├── icon.png            # App icon (1024x1024)
│   ├── entitlements.plist  # macOS code signing
│   └── installer.nsh       # NSIS custom scripts
│
└── dist/                   # Build output (gitignored)
    ├── StreamSync Setup *.exe
    ├── *.dmg
    └── *.AppImage
```

### Key Files Explained

#### `main.js` — Electron Main Process

```javascript
// Handles window creation, permissions, and native APIs
- BrowserWindow configuration
- setDisplayMediaRequestHandler for screen sharing
- setPermissionRequestHandler for camera/mic access
- Auto-update integration with electron-updater
```

#### `preload.js` — Context Bridge

```javascript
// Securely exposes limited APIs to renderer
-window.electronAPI.showNotification() -
  window.electronAPI.getPlatform() -
  window.electronAPI.openExternalLink();
// Never exposes Node.js directly to web content
```

#### `src/renderer/lib/webrtc.js` — WebRTC Logic

```javascript
// Manages peer connections and media streams
-createPeerConnection(config) -
  setupScreenShare(stream, constraints) -
  handleIceCandidate(candidate) -
  monitorConnectionQuality();
```

---

## 🤝 Contributing

We welcome contributions! Please follow these steps:

### Getting Started

1. Fork the repository
2. Clone your fork: `git clone https://github.com/YOUR_USERNAME/streamsync-desktop.git`
3. Create a feature branch: `git checkout -b feat/your-feature-name`
4. Install dependencies: `npm install`
5. Start development: `npm start`

### Development Guidelines

- Follow existing code style (ESLint + Prettier configured)
- Add TypeScript types for all new functions/components
- Write tests for critical logic (`npm test`)
- Update documentation for user-facing changes
- Test screen sharing on at least 2 platforms before PR

### Pull Request Process

1. Ensure your branch is up to date with `main`
2. Run linting and tests: `npm run lint && npm test`
3. Build and test locally: `npm run dist -- --win --dir`
4. Submit PR with clear description of changes
5. Respond to review feedback promptly

### Code of Conduct

Please be respectful and inclusive. We're building tools for global collaboration — let's make our community welcoming for everyone.

---

## 🐛 Troubleshooting

### Common Issues

#### ❌ Screen sharing not working

```bash
# Check Electron version (requires 25+)
npm list electron

# Verify permission handler is implemented in main.js
# Ensure macOS Screen Recording permission is granted
# Try restarting the app after granting permissions
```

#### ❌ Blank screen / loading forever

```bash
# Open DevTools: Ctrl+Shift+I (Win/Linux) or Cmd+Option+I (macOS)
# Check Console tab for errors
# Verify network connectivity to streamsync.apionlabs.org
# Ensure your firewall allows WebRTC (UDP ports 1024-65535)
```

#### ❌ Camera/microphone not detected

```bash
# Check system permissions for camera/mic access
# Ensure no other app is exclusively using the device
# Try restarting the app or your computer
# On Linux: verify v4l2loopback or PipeWire is configured
```

#### ❌ Build fails on Windows

```bash
# Run terminal as Administrator
# Disable antivirus temporarily during build
# Clear node_modules and reinstall:
rm -rf node_modules package-lock.json
npm install
# Ensure Python 3.x is installed (for node-gyp)
```

#### ❌ App shows "Unknown Publisher" warning

```bash
# This is normal for unsigned apps
# For production: obtain code signing certificate
# Add to package.json:
"win": {
  "certificateFile": "path/to/cert.pfx",
  "certificatePassword": "${CSC_KEY_PASSWORD}"
}
```

### Getting Help

1. Check this README and existing [Issues](https://github.com/apionlabs/streamsync-desktop/issues)
2. Search error messages in our [Discussions](https://github.com/apionlabs/streamsync-desktop/discussions)
3. Open a new issue with:
   - Your OS and version
   - Electron version (`npm list electron`)
   - Steps to reproduce
   - Console logs or screenshots
   - Network tab output if connection-related

---

## 📄 License

StreamSync Desktop is released under the **MIT License**.

```
MIT License

Copyright (c) 2026 Apionlabs

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

---

## 🌐 Links & Resources

- 🌍 **Web App**: [https://streamsync.apionlabs.org/app/](https://streamsync.apionlabs.org/app/)
- 📦 **Releases**: [github.com/apionlabs/streamsync-desktop/releases](https://github.com/apionlabs/streamsync-desktop/releases)
- 🐛 **Issues**: [github.com/apionlabs/streamsync-desktop/issues](https://github.com/apionlabs/streamsync-desktop/issues)
- 💬 **Discussions**: [github.com/apionlabs/streamsync-desktop/discussions](https://github.com/apionlabs/streamsync-desktop/discussions)
- 🏢 **Apionlabs**: [https://apionlabs.org](https://apionlabs.org)
- 📧 **Contact**: hello@apionlabs.org

---

<p align="center">
  <strong>StreamSync © 2026 • Built with ❤️ by <a href="https://apionlabs.org">Apionlabs</a></strong><br/>
  <sub>All connections are peer-to-peer. We never store or access your screen content or video streams.</sub>
</p>

<p align="center">
  <a href="https://streamsync.apionlabs.org/app/">🚀 Launch StreamSync Now</a>
</p>
```
