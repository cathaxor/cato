# Cato v1.0.0 — Your Expressive Desktop Cat Companion 🐾

Meet **Cato**, a native, ultra-lightweight desktop cat companion built with C++20, Win32 API, and OpenGL. Cato wanders your desktop, climbs onto your active application windows, takes naps on your title bar, and keeps you company while you work or code!

This first public release provides a completely standalone, portable executable (`Cato.exe`) with **zero external dependencies** and no installation required.

---

### ✨ Highlights & Features

- **🐾 32 Handcrafted Pixel-Art Animation Frames**:
  - **Authentic 4-Leg Walk**: Coordinated feline diagonal gait (contact, passing, reach, push-off) synchronized with movement speed to eliminate foot-sliding.
  - **Bounding Sprint / Gallop**: Clear extension (reach) and compression (gather) phases with aerodynamic lean and speed streaks.
  - **Living Micro-Animations**: Subtle breathing chest expansion, varied natural blinking with occasional double-blinks, smooth sinusoidal tail swaying, ear twitches, and curious gaze shifts.
  - **Full Jumping Sequence**: Preparation crouch, takeoff leap, airborne fall, landing cushion impact recovery, and stable return.
  - **Expressive Behaviors**: Rear-leg ear scratching, paw-licking and face-washing grooming, morning yawn stretch, cozy curled sleep, yarn ball batting, window climbing, blissful petting purrs with floating hearts, and scruff dragging.

- **🪟 Smart Window Perching**:
  - Automatically detects your active application window (VS Code, Browser, Notepad, etc.).
  - Walks to the window edge, climbs up the border, and perches comfortably on the title bar ledge without teleporting or obstructing your work.

- **🪂 Parachute Jump Action**:
  - Triggerable anytime from the system tray menu or Settings window.
  - Features a colorful 4-panel canopy, suspension lines, body harness, and a gentle floating descent to land safely on a window ledge or taskbar.

- **📏 Exact 0 px Taskbar Floor Alignment**:
  - Dynamic surface-anchoring ensures Cato stands firmly on your Windows taskbar with zero hovering gap across 1x, 2x, 3x, and 4x scales.

- **🐱 6 Cat Breeds**:
  - Classic Cato Grey Tabby (Slate fur, pure white bib & paws, vibrant sapphire blue eyes)
  - Ginger Tabby (Warm marmalade orange with emerald green eyes)
  - Tuxedo (Formal black & white with amber eyes)
  - Calico (Tri-color patch coat with emerald eyes)
  - Midnight Black (Velvety dark charcoal with golden eyes)
  - Siamese (Cream body, dark chocolate points, sapphire eyes)

- **⏱️ Eye-Care Break Timer**:
  - Follows the optometrist-recommended 20-20-20 rule.
  - Gently reminds you every 20 minutes to rest your eyes by looking 20 feet away for 20 seconds.

- **⚡ Lightweight & 100% Standalone**:
  - Native C++20 with statically linked runtime (`/MT`).
  - Less than 1 MB file size, near-zero CPU usage at idle, and zero external DLL requirements.

---

### 🚀 Quick Start (How to Run)

1. Download **`Cato.exe`** (or **`Cato-v1.0.0-Portable-x64.zip`**) below.
2. Double-click **`Cato.exe`** to launch immediately. No setup or admin privileges required!
3. **Controls**:
   - **Right-Click Cato or Tray Icon**: Open context menu to access Settings, Behaviors, Parachute Jump, or Exit.
   - **Left-Click & Drag**: Pick up Cato by the scruff to place it anywhere on your desktop.
   - **Mouse Hover**: Pet Cato to make it purr!
   - **Double-Click**: Open the Settings GUI.

---

### 📦 Checksums & Verification

| File | Size | SHA-256 Checksum |
| :--- | :--- | :--- |
| **`Cato.exe`** | 930 KB | `13D42B9379F9C96DB3510B187322DDF2319FFF1CFBE3C50F309878AF70A2E474` |
| **`Cato-v1.0.0-Portable-x64.zip`** | 450 KB | `39AB3625C9953E7872096251C2FD5D9DFEF6FB40CEFD2F4F1E7877952B0D5E56` |

---

### 💻 System Requirements

- **Operating System**: Windows 10 or Windows 11 (64-bit)
- **Graphics**: Any GPU supporting OpenGL 2.0+
- **Architecture**: x86-64

---

**Developed with ❤️ by Abdur Rahaman Abdulla ([@CatHaxor](https://github.com/CatHaxor))**
