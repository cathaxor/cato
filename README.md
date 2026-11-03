# CATO v1.2.1 THE LIVING DESKTOP COMPANION

### Release Overview
- **Version**: 1.2.1 (Official Stable Release)
- **Developer**: Abdur Rahaman Abdulla (CatHaxor)
- **Target OS**: Windows 10 / 11 (x64)
- **Architecture**: Native C++20, Win32 API, OpenGL, Hardware Accelerated

---

### New Features & Critical Fixes

1. **Window Perching, Stable Climbing & Anti-Drop Fix**
   - Eliminated sudden resets and drop bugs while Cato climbs up or sits on application windows.
   - Guarded climbing state machine so activating or clicking background windows never cancels the climb or plummets Cato to the floor.
   - Stable perched lounging on window title bars that naturally tracks window moving, resizing, and maximizing.

2. **Absolute Always-On-Top Visibility Guarantee**
   - Cato, the speech bubble, and desktop toys remain visibly on top across all open applications.
   - Immediate re-assertion of HWND_TOPMOST upon any window activation or creation ensures Cato is never buried or obscured.

3. **Complete Update Center Overhaul**
   - GitHub Releases API integration gracefully handles up-to-date states and release discovery.
   - Live animated download progress bar with responsive 120ms UI refresh timer.
   - Direct Inno Setup executable updater support (Cato-Setup.exe / Cato.exe).
   - All update preferences (automatic check, notification, auto-download, auto-install) fully configurable from UI and System Tray.

4. **Instant Cursor Sprint & Playful Chase Overhaul**
   - Eliminated activity lockups during cursor chasing: stationary activities (Scratch, Groom, Sit, Idle, Sleep) are immediately cancelled when the cursor moves away.
   - Dynamic distance-scaled sprint speed up to 810 px/s (13.5 px/frame in Playful Chase) for instant responsiveness.
   - Excited aerial leaps: when the user dangles the cursor above Cato, Cato leaps upward enthusiastically.
   - Smooth ledge disengagement when cursor is lured across the screen.

2. **Window Perching & Z-Order Fix**
   - Clicking background apps or interacting with the active window no longer causes Cato to fall off the window ledge or sink underneath.
   - Dynamic HWND_TOPMOST maintenance keeps Cato stably positioned on the title bar and visible over foreground applications.

3. **Full Multi-Monitor & Dual-Monitor Support**
   - Seamless cross-monitor roaming across the entire desktop virtual canvas (SM_XVIRTUALSCREEN, SM_CXVIRTUALSCREEN).
   - Dynamic floor positioning (getDesktopFloorAt) anchors Cato smoothly to each display's work area taskbar without hitting artificial boundary walls or bouncing.

4. **Bidirectional System Tray & GUI Synchronization**
   - Every toggle, mode selector, cursor tracking option, and toy action altered via the System Tray context menu instantly synchronizes with the Settings Window GUI in real time.

5. **Modern Glass & Acrylic Settings Interface**
   - Frosted obsidian glass aesthetic with translucent cards, 1px specular reflection top rim, and glowing interactive hover states.
   - Native Windows 11 Acrylic / Mica backdrop support via Desktop Window Manager (DWMWA_SYSTEMBACKDROP_TYPE).
   - Refined segmented toggles, pill switches, and smooth typography.

6. **Emotion & Expression System**
   - Centralized EmotionController with 7 reactive emotional states:
     - Happy (floating hearts purring, petting)
     - Curious (question mark observing nearby cursor and toys)
     - Sleepy (gentle Zzz micro-breathing, late night hours)
     - Excited (sparkles, chasing toys, high-energy leaps)
     - Annoyed (anger marks rapid dragging)
     - Relaxed (musical notes baseline contentment)
     - Surprised (exclamation, parachute deployment, sudden changes)
   - Intensity levels: Subtle, Normal, and Expressive.
   - Automatic natural mood transitions with decay and cooldown guards.

7. **Desktop Toy Interaction & Custom Skins**
   - 4 Physical Desktop Toys: Yarn Ball, Red Ball, Feather Wand, and Laser Dot.
   - Dedicated layered toy window with floor gravity, bounce damping, and momentum throws.
   - Custom skins loader with high-performance WIC PNG decoding from %APPDATA%\Cato\skins\.

8. **Day & Night Diurnal Cycle**
   - Synchronized with local system clock with customizable day/night hours and subtle nocturnal visual effects.

---

### Improvements & Stability
- Completely eliminated foot sliding and unnatural pause interruptions.
- Zero CPU overhead rendering pipeline via OpenGL 32-bit alpha layered window.
- Verified binary compatibility across Windows 10 and Windows 11.
