# CATO v1.2.3 — THE LIVING DESKTOP COMPANION

## 🐾 Release Overview
- **Tag**: `v1.2.3`
- **Release Title**: `Cato v1.2.3 — Emergency Parachute Descent & Window Dynamics`
- **Developer**: Abdur Rahaman Abdulla (CatHaxor)
- **Target OS**: Windows 10 / 11 (64-bit)
- **Tech Stack**: Native C++20, Win32 API, Hardware-Accelerated OpenGL, MultiThreaded MSVC Static Runtime (`/MT`)

---

## 🌟 What's New in v1.2.3

### 1. Emergency Parachute Descent on Window Close / Minimize
- **Automatic Vanishing Surface Detection**: When Cato is lounging or perched on top of any browser tab, editor, or application window, and you close or minimize that window, Cato instantly detects the vanishing surface.
- **Mid-Air Parachute Blossom**: Instead of falling awkwardly or snapping, Cato immediately blossoms its emergency parachute overhead, lets out an alert meow/jump sound, and flashes a surprised expression (`CatEmotion::Surprised` 🙀).
- **Graceful Desktop Floor Gliding & Rest**: Cato glides smoothly downward with gentle aerodynamic sway directly towards the desktop taskbar floor (`desktopFloor`), safely lands, packs the parachute away, and curls up into a peaceful sitting pose (`AnimState::Sit`) on your desktop floor.

### 2. Lifelike Cursor Trailing & Organic Locomotion ("Picone Picone Asbe")
- **Motion-Vector Wake Trailing**: Cato trails naturally behind in the wake of the cursor motion vector (`desiredTrail = cursorPos - normCursorVelocity * trailDistance`). Clicks and desktop interaction remain 100% unimpeded via `HTTRANSPARENT`.
- **Dynamic Feline Gait Switching ("Aste Aste Haita" vs "Douray")**:
  - **Gentle Walking (`AnimState::Walk`)**: Relaxed 4-frame alternate foot pacing (1.8 to 4.2 px/frame) when following closely (`dist <= 95px`) or during subtle pointer adjustments.
  - **Agile Sprinting (`AnimState::Run`)**: High-energy sprint (up to 26 px/frame) with speed streaks when the cursor dashes across screens or multi-monitor setups.
- **Organic Newtonian Steering**: Smooth velocity steering curves (`accelRate = 0.18f / 0.26f`) create natural, rounded feline turns with inertia and momentum.
- **Attentive Resting & Automatic Sitting**: Decelerates smoothly to a stop (`AnimState::Idle`), and curls up into a peaceful sitting pose (`AnimState::Sit`) after 1.2s of mouse inactivity. Leaps up immediately the moment the mouse moves again!

### 3. Full Cat Sound System with Granular Activity Toggles
- **Built-in Procedural Audio Synthesizer**: Generates authentic 16-bit 44.1kHz mono PCM WAV buffers in-memory with zero external DLL dependencies (using Windows `winmm.lib` / `PlaySoundW` with `SND_ASYNC | SND_MEMORY`).
- **8 Distinct Activity Sounds**:
  - **Meow**: Gentle friendly vocal greeting on petting, click, startup, or tray command.
  - **Purr**: Soft rhythmic vibrating purr triggered when the cursor hovers over Cato or while lounging.
  - **Playful Chirp**: High-pitched energetic chirp emitted during playful cursor chases and toy batting.
  - **Toy Swat**: Crisp percussion impact swoosh when batting yarn balls, bouncing balls, feathers, or laser dots.
  - **Agile Jump**: Swift airy swoosh on vertical leaps, window climbing, and parachute jumps.
  - **Grumpy Hiss / Grumble**: Annoyed raspy hiss when dragged abruptly across the desktop.
  - **Sleep Snoring**: Cozy micro-snore sound emitted during sleep cycles.
  - **Reminder Chime**: Harmonic focus break alert for 20-20-20 eye strain reminder.
- **Granular Controls in Settings GUI & System Tray**:
  - Individual ON/OFF switches for every single activity sound type.
  - Master volume slider / selector (Mute, 30%, 70%, 100%) with real-time waveform amplitude scaling.
  - Inline **"▶ Test"** preview buttons for every sound effect.
  - **Custom Sound Override Support**: Drop custom `.wav` files into `%APPDATA%\Cato\sounds\` to replace procedural sounds.

### 4. Interactive Desktop Toy Physics
- **4 Physical Desktop Toys**: `Yarn Ball`, `Red Bouncy Ball`, `Feather Wand`, and `Laser Dot`.
- Dedicated layered toy window with floor gravity, bounce damping, momentum throws, and multi-monitor canvas support.

### 5. Window Ledge Sitting, Perching & Anti-Drop Protection
- Unbreakable `HWND_TOPMOST` assertion ensures Cato remains visible over foreground applications, games, and browser windows.
- Stable window perching: Cato detects active window title bars, climbs gracefully, and stays perched without plummeting or resetting when apps are switched or clicked.

### 6. 7-Emotion Reactive Expression System
- Centralized `EmotionController` with 7 reactive emotional states:
  - `Happy` (floating hearts, purring, petting)
  - `Curious` (question mark observing nearby cursor and toys)
  - `Sleepy` (gentle `Zzz` micro-breathing, late night hours)
  - `Excited` (sparkles, chasing toys, high-energy leaps)
  - `Annoyed` (anger marks, rapid dragging)
  - `Relaxed` (musical notes, baseline contentment)
  - `Surprised` (exclamation, parachute deployment, sudden window close)
- Automatic natural mood transitions with decay and cooldown guards.

### 7. Modern Glass Acrylic Settings Interface
- Frosted dark obsidian glass card design with 1px specular reflection top rim and Windows 11 Acrylic / Mica backdrop support.
- 11 categorized tabs covering every aspect of Cato's personality, physics, appearance, and audio.
- Bidirectional real-time synchronization between System Tray and Settings GUI.

### 8. Complete Update Center
- Direct GitHub Releases API integration with semantic version comparison (`v1.2.3`).
- Live animated download progress bar with 120ms UI refresh timer.
- Direct Inno Setup executable updater support (`Cato-Setup.exe` / `Cato.exe`).

### 9. Full Multi-Monitor & Dual-Monitor Support
- Seamless cross-monitor roaming across the entire desktop virtual canvas (`SM_XVIRTUALSCREEN`, `SM_CXVIRTUALSCREEN`).
- Dynamic floor positioning (`getDesktopFloorAt`) anchors Cato smoothly to each display's work area taskbar without boundary hitches.

---

## 🛠 Architectural Audit & Bug Fixes

- **Parachute Window Escape**: Implemented `Companion::parachuteFromClosedWindow()`, `m_parachuteTargetFloor`, and elevation-aware parachute deployment logic when perched application windows close or minimize.
- **Floor Sit Transition**: Added direct transition to `AnimState::Sit` upon landing on the floor after a window closure event, preventing erratic instant roaming.
- **Locomotion Resumption**: Added `isFreshTracking` guard so Cato snaps trail target coordinates immediately to current cursor coordinates when waking from idle, preventing stale ease arcs.
- **Cursor Delta Initialization**: Seeded `m_lastCursorPos` on initial detection; eliminated the 1600+ px first-frame speed spike.
- **Multi-Monitor Toy Boundaries**: Extended horizontal physics bounds to `bounds.virtualLeft` and `bounds.virtualRight`.
- **Emotion Emoji Surrogate**: Corrected Annoyed emotion Unicode symbol to authentic pouting cat `\U0001F63F` (😾).
- **User-Agent Version Header**: Updated HTTP User-Agent string to `Cato-Desktop-Companion/1.2.3`.

---

## 📦 Verified Release Artifacts & SHA-256 Checksums

| Artifact File | Description | Size | SHA-256 Checksum |
| :--- | :--- | :---: | :--- |
| **`Cato.exe`** | Standalone Production Binary | **1,123.0 KB** | `d979e3294e3fd3750927a8771ef7b0cb415764510acf9d956b0e3e8caeddd7ba` |
| **`Cato-Portable-x64.zip`** | Self-Contained Archive Package | **533.4 KB** | `671c346f4acdcd2f6d37f24bfb667aa8b41e05c10aeba401a40d4cabfa2b0dd8` |
| **`Cato-Setup.exe`** | Official Inno Setup Windows Installer | **2,897.6 KB** | `1fe8a65b24695a58d77f518b9ac410c0ca078a628930cc590e81cdfa622d9ad0` |

---

## 🚀 How to Install & Run

### Option 1: Official Windows Installer (Recommended)
1. Download **`Cato-Setup.exe`**.
2. Run the installer.
3. Cato will start automatically and create desktop and start menu shortcuts.

### Option 2: Portable Archive (Zero Installation)
1. Download **`Cato-Portable-x64.zip`**.
2. Extract the archive into any folder.
3. Run **`Cato.exe`**. User settings are saved in `%APPDATA%\Cato\settings.json`.
