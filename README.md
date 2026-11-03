# CATO v1.2.2 — THE LIVING DESKTOP COMPANION

### 🐾 Release Overview
- **Version**: `1.2.2` (Official Stable Release)
- **Developer**: Abdur Rahaman Abdulla ([@cathaxor](https://github.com/cathaxor))
- **Target OS**: Windows 10 / 11 (64-bit)
- **Architecture**: Native C++20, Win32 API, Hardware-Accelerated OpenGL, MultiThreaded Static MSVC (`/MT`)

---

### 🌟 What's New in v1.2.2

#### 1. Lifelike Cursor Trailing & Organic Locomotion
- **Motion-Vector Wake Trailing**: Instead of snapping onto the cursor tip, Cato now trails naturally behind in the motion vector wake of your cursor (`desiredTrail = cursorPos - normCursorVelocity * trailDistance`). Clicks and desktop interaction remain 100% unimpeded via `HTTRANSPARENT`.
- **Dynamic Feline Gait Switching ("Aste Aste Haita" vs "Douray")**:
  - **Gentle Walking (`AnimState::Walk`)**: Relaxed 4-frame alternate foot pacing (1.8 to 4.2 px/frame) when following closely (`dist <= 95px`) or during subtle pointer movements.
  - **Agile Sprinting (`AnimState::Run`)**: High-energy sprint (up to 26 px/frame) with speed streaks when the cursor dashes across screens or multi-monitor setups.
- **Organic Newtonian Steering**: Replaced linear translation with smooth velocity steering curves (`accelRate = 0.18f / 0.26f`). Cato takes natural, rounded turns with realistic inertia and momentum rather than sharp polygonal corners.
- **Attentive Resting & Automatic Sitting**: Decelerates smoothly to a stop (`AnimState::Idle`), and curls up into a peaceful sitting pose (`AnimState::Sit`) after 1.2s of mouse inactivity. Leaps up immediately the moment the mouse moves again!

#### 2. Full Cat Sound System with Granular Activity Toggles
- **Built-in Procedural Audio Synthesizer**: Generates authentic 16-bit 44.1kHz mono PCM WAV buffers in-memory with zero external DLL dependencies (using Windows `winmm.lib` / `PlaySoundW` with `SND_ASYNC | SND_MEMORY`).
- **8 Distinct Activity Sounds**:
  - **Meow**: Gentle friendly vocal greeting on petting, click, startup, or tray command.
  - **Purr**: Soft rhythmic vibrating purr triggered when the cursor hovers over Cato or while lounging.
  - **Playful Chirp**: High-pitched energetic chirp emitted during playful cursor chases and toy batting.
  - **Toy Swat**: Crisp percussion impact swoosh when batting yarn balls, bouncing balls, feathers, or laser dots.
  - **Agile Jump**: Swift airy swoosh on vertical leaps, window climbing, and playful dangles.
  - **Grumpy Hiss / Grumble**: Annoyed raspy hiss when dragged abruptly or yanked across the desktop.
  - **Sleep Snoring**: Cozy micro-snore sound emitted during sleep cycles.
  - **Reminder Chime**: Harmonic focus break alert for 20-20-20 eye strain reminder.
- **Granular Controls in Settings GUI & System Tray**: Individual switches for each sound, volume control (Mute, 30%, 70%, 100%), inline test preview buttons, and custom `.wav` override support in `%APPDATA%\Cato\sounds\`.

#### 3. Interactive Desktop Toy Physics
- **4 Physical Desktop Toys**: `Yarn Ball`, `Red Bouncy Ball`, `Feather Wand`, and `Laser Dot`.
- Dedicated layered toy window with floor gravity, bounce damping, momentum throws, and multi-monitor canvas support.

#### 4. Window Ledge Sitting, Perching & Anti-Drop Safeguards
- Unbreakable `HWND_TOPMOST` assertion ensures Cato remains visible over foreground applications, games, and browser windows.
- Stable window perching: Cato detects active window title bars, climbs gracefully, and stays perched without plummeting or resetting when apps are switched or clicked.

#### 5. 7-Emotion Reactive Expression System
- Centralized `EmotionController` with 7 reactive emotional states: `Happy`, `Curious`, `Sleepy`, `Excited`, `Annoyed`, `Relaxed`, and `Surprised`.
- Automatic natural mood transitions with decay and cooldown guards.

#### 6. Modern Glass Acrylic Settings Interface
- Frosted dark obsidian glass card design with 1px specular reflection top rim and Windows 11 Acrylic / Mica backdrop support.
- 11 categorized tabs covering every aspect of Cato's personality, physics, appearance, and audio.
- Bidirectional real-time synchronization between System Tray and Settings GUI.

#### 7. Complete Update Center
- Direct GitHub Releases API integration with semantic version comparison (`v1.2.2`).
- Live animated download progress bar with 120ms UI refresh timer.
- Direct Inno Setup executable updater support (`Cato-Setup.exe` / `Cato.exe`).

#### 8. Full Multi-Monitor & Dual-Monitor Support
- Seamless cross-monitor roaming across the entire desktop virtual canvas (`SM_XVIRTUALSCREEN`, `SM_CXVIRTUALSCREEN`).
- Dynamic floor positioning (`getDesktopFloorAt`) anchors Cato smoothly to each display's work area taskbar without boundary hitches.

---

### 🛠 Architectural Audit & Bug Fixes

- **Locomotion Resumption**: Added `isFreshTracking` guard so Cato snaps trail target coordinates immediately to current cursor coordinates when waking from idle, preventing stale ease arcs.
- **Cursor Delta Initialization**: Seeded `m_lastCursorPos` on initial detection; eliminated the 1600+ px first-frame speed spike.
- **Multi-Monitor Toy Boundaries**: Extended horizontal physics bounds to `bounds.virtualLeft` and `bounds.virtualRight`.
- **Emotion Emoji Surrogate**: Corrected Annoyed emotion Unicode symbol to authentic pouting cat `\U0001F63F` (😾).
- **User-Agent Version Header**: Updated HTTP User-Agent string to `Cato-Desktop-Companion/1.2.2`.
- **Installer Compiler**: Added `RunOnceId: "KillCato"` to Inno Setup `[UninstallRun]` section, compiling with 0 warnings.

---

### 📦 Checksums (SHA-256)

| Artifact File | Size | SHA-256 Checksum |
| :--- | :---: | :--- |
| **`Cato.exe`** | 1,121.5 KB | `862263f5ccf09a62000e42492d891dfe8e2c307720d0bd17464630e90579247d` |
| **`Cato-Portable-x64.zip`** | 533.0 KB | `03946ffaf88744ae1cc26e18176773c779fd09a72a03e4b4044c199f062e29af` |
| **`Cato-Setup.exe`** | 2,897.3 KB | `328a994d957790e4eb3d750402a38c4845359cd88d4a1412725c012fca4f69c1` |

---

### 🚀 How to Install & Run

#### Option 1: Official Windows Installer (Recommended)
1. Download **`Cato-Setup.exe`**.
2. Run the installer.
3. Cato will start automatically and create desktop and start menu shortcuts.

#### Option 2: Portable Archive (Zero Installation)
1. Download **`Cato-Portable-x64.zip`**.
2. Extract the archive into any folder.
3. Run **`Cato.exe`**. User settings are saved in `%APPDATA%\Cato\settings.json`.
