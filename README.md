# Cato — Desktop Cat Companion (v1.0.2 Release Notes)

**Release Version:** `v1.0.2`  
**Release Date:** October 30, 2026  
**Developer:** Abdur Rahaman Abdulla (CatHaxor)  
**Repository:** [https://github.com/cathaxor/cato](https://github.com/cathaxor/cato)  
**Target Platform:** Windows 10 / 11 (x64)  
**Architecture:** Native C++20, Win32 API, OpenGL Hardware-Accelerated  

---

## 🌟 Overview & Highlights

Cato `v1.0.2` delivers a complete **Functionality Restoration, Behavior Engine Integration, and Release Polish** update.

Every setting on the Behavior, Appearance, and Sounds pages is now fully wired from the UI to the underlying companion engine and persisted across sessions. Cato autonomously strolls the desktop floor, respects user-configured roaming and jump frequencies, synchronizes leg animation rates to movement speed multipliers, responds instantly to personality mode changes, and features a functional parachute jump.

---

## 🔧 Key Improvements & Restorations in v1.0.2

### 1. Behavior Settings Pipeline Fully Connected
- **Movement Speed Multiplier:** Added `0.7x (Slow)`, `1.0x (Normal)`, `1.5x (Brisk)`, and `2.0x (Turbo)`. Adjusts horizontal walking velocity (`1.05 px/frame` to `3.0 px/frame`) as well as running and climbing velocities.
- **Animation Gait Synchronization:** Scaled sprite walk step rates (`CatSpriteGenerator::generateFrame`) inversely with movement speed so Cato's legs cycle faster at higher speeds, preventing foot-sliding.
- **Autonomous Roaming Frequency:** Added `Rare (0.5x)`, `Normal (1.0x)`, and `Frequent (2.0x)`. Dynamically scales autonomous walk probabilities (22% up to 75%) and idle pause durations.
- **Jump Frequency:** Added `Cautious (0.5x)`, `Normal (1.0x)`, and `Acrobatic (2.0x)`. Adjusts autonomous leap probability from 1% up to 28% in Playful mode.
- **Instant Personality Switching:** Changing mode to **Sleeping** instantly curls Cato into peaceful sleep with zero roaming; switching to **Playful** prompts immediate energetic activity without delayed transitions.
- **Surface Movement Modes:**
  - *Desktop Only:* Stays strictly on the taskbar floor; immediately leaves any window if currently perched.
  - *Window Sitting:* Climbs and tracks active windows without automatic dismount.
  - *Roam Everywhere:* Roams the entire desktop floor, visits windows, and dismounts after 15–20 seconds with cooldown.

### 2. Parachute Jump Action
- Triggering Parachute Jump (via Settings or Context Menu) launches Cato high into the air and gracefully deploys an animated parachute to float back down to the taskbar floor. Fixed state management to allow smooth repeated activations.

### 3. Opacity & Rendering Controls
- Connected window opacity settings (`20%` to `100%`) directly to `UpdateLayeredWindow` via `BLENDFUNCTION.SourceConstantAlpha`.
- Connected animation quality settings: `Retro (30 FPS)` sets timer to 33 ms, while `High (60 FPS)` runs at silky-smooth 16 ms.

### 4. Settings Persistence & Migration
- Standardized configuration format on `%APPDATA%\Cato\settings.json` with fallback migration from legacy `config.json`.
- Safely handles both string representation and numerical values for breeds and modes.

---

## 📦 Release Deliverables & Checksums

| File | Type | Size | SHA-256 Checksum |
| :--- | :--- | :--- | :--- |
| **`Cato.exe`** | Standalone Executable (x64) | 935,424 bytes | `20232e7d1846f503fa03c1db417f9400d43176bb423c7296133fc77b8075daad` |
| **`Cato-Portable-x64.zip`** | Portable Archive (`Cato.exe` + `README.txt`) | 451,777 bytes | `a784ca82d986d44183db3bd91b516ee6e65023acfb6b80d73d273d762eefd948` |
| **`Cato-Setup.exe`** | Windows Inno Setup Installer | 2,900,050 bytes | `137500c0ba731be796b9adb0ac3f138fb3623481d3470fb0e10c905330be370f` |

---

## 🚀 Quick Start Guide

### Standalone Executable (`Cato.exe`)
1. Download `Cato.exe` and place it anywhere (e.g. Desktop or Downloads).
2. Double-click `Cato.exe` to run. No installer or administrator permissions required!
3. Right-click Cato or the tray icon to customize settings or exit.

### Windows Installer (`Cato-Setup.exe`)
1. Download and run `Cato-Setup.exe`.
2. Follow the modern setup wizard. It installs cleanly into `%LOCALAPPDATA%\Programs\Cato` without requiring admin rights.
3. Creates convenient Start Menu and Desktop shortcuts with clean uninstaller support.
