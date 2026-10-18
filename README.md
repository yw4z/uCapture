<img src="https://github.com/user-attachments/assets/debac80a-df93-4c27-b62b-0b1a7af8567b" width="64">
<h1>uCapture</h1>

Lightweight, portable, fast screenshot and screen-recording tool for Windows 10

---

## 🚀 Lightweight, fast & fully featured
Just 160kb! starts instantly, uses practically no CPU and RAM while idle

## 🌄 Multiple screen capture modes
**Region capturing:** just draw a rectangle or capture last used again<br>
**Screen and window capture:** capture whatever you want easily

## 🎥 Fully featured screen recording
**MP4 & GIF support:** hardware-accelerated H.264 encoding and built-in GIF encoder with smart dithering<br>
**Various options:** with cursor visibility, timer, fps, quality options

## 💫 Simplified experience
All UI designed to reduce time you have spent on repeating tasks 

## 🎨 Utilities
**Color picker:** that can copy `#RRGGBB`, `RGB(…)` or `R, G, B` formats to clipboard

## 😎 Customizable
**Settings:** New options will be added on each release<br>
**Hotkeys:** Soon<br>
**Command line:** can be scripted or bound to a hotkey tools

## 🔒 Private
never connects to the internet

---

## Contents

- [Download and installation](#download-and-installation)
- [Quick start](#quick-start)
- [Tray menu](#tray-menu)
- [Capturing](#capturing)
- [Recording](#recording)
- [Colour picker](#colour-picker)
- [After a capture](#after-a-capture)
- [Command line](#command-line)
- [Keyboard and mouse](#keyboard-and-mouse)
- [Settings](#settings)
- [Captured files](#captured-flies)
- [Privacy](#privacy)
- [Verifying your download](#verifying-your-download)
- [System requirements](#system-requirements)
- [License](#license)

---

## Download and installation

### Installation & Running
1. Download latest version from [Releases](../../releases) page. [Verify your download](#verifying-your-download)
2. Put it in any folder you like, for example `C:\ProgramData\Apps\uCapture\`
3. Run it. App icon appears in the system tray

- No installer. uCapture is portable and stores its settings in `settings.ini` next to the exe
- Ensure put it on a folder that doesnt require permissions like `C:\Program Files`
- Only one instance of uCapture can run at a time

### Uninstallation
- Exit it from the tray and just delete it. it doesn't store any additional files or registry keys

### To start with Windows
- Press `Win + R`, type `shell:startup`, and put a shortcut of `uCapture.exe` to the folder that opens

---

## Quick start

Currently app only usable with tray menu or using cli commands that can be combined with hotkey tools<br>
Built-in keyboard shortcuts in development plan

---

## Tray menu
Open the menu via left or right clicking the tray icon.

<img width="155" height="287" alt="20261016_230044_Screenshot" src="https://github.com/user-attachments/assets/2a5ddbf4-3e12-4857-8bf1-36a8772b19fe" />

| Item | What it does |
|---|---|
| **Region draw** | Draw a rectangle on the screen to capture |
| **Last region** | Capture the last drawn region again, without drawing |
| **Pick region** | Hover over windows to highlight them, then click one to capture. Hover the desktop to capture screen |
| **Capture Screens** | Capture every monitor as per monitor or combined image. See `CaptureMonsToOne` |
| **Screens ▸** | **Pick**  Hover over screens to highlight them, then click one to capture. Also each monitor is listed with its number and resolution for a direct capture. *Only appears if multiple monitors exist |
| **Windows ▸** | A list of open windows. Choose one to capture it directly|
| **Record** | Shows the recording frame |
| **Color picker** | Opens the color picker |
| **More ▸** | **Open captures folder**, **Settings** (opens `settings.ini`), **About**, **Exit** |

---

## Capturing

### Region draw

Press and drag to draw the capture area<br>
- Hold **Shift** to draw a perfect square
- Hold **Ctrl** to keep the current aspect ratio
- **Right-click** or **Esc** to cancel capturing

When you release the left mouse button, the region will be captured and saved, copied to the clipboard (if enabled) and selected rectangle remembered for **Last region**

### Last region

Captures exactly the same rectangle as the previous region draw, instantly. Useful for taking "before / after" shots of the same area. The region is remembered across restarts

### Pick region

Move the mouse around: the window or screen under the cursor gets a blue frame and a size label. Click
to capture it. If the window is on background, it will be moved to foreground first

If you hover the desktop instead of a window, the whole monitor is highlighted and captured

- Hold **Shift** to highlight screen contains the cursor
- **Right-click** or **Esc** to cancel capturing

### Capture Screens

Captures all monitors at once. By default each monitor becomes its own file (`..._Screen_1.png`, `..._Screen_2.png`, …). With `[Capture] CaptureMonsToOne=1` setting you get one image of the whole desktop instead.

A short shutter flash confirms the capture (can be turned off with `[Capture] Shutter=0`).

### Screens Submenu

With more than one monitor, the submenu has one entry per monitor captures that monitor straight away

### Windows Submenu

Lists the open windows by title. Choosing one brings it to the front and captures it, which is handy when the window you want is covered by others

---

## Recording

### Recording frame

**Tray → Record** shows a blue frame with a control bar. Everything inside the frame is
recorded

- **Move:** drag the control bar.
- **Resize:** drag an edge or a corner of the frame. The size is shown while you drag.
  - Hold **Ctrl** to keep the aspect ratio.
  - Hold **Shift** to make it square.

### Control bar

From left to right:

| Button | What it does |
|---|---|
| Record | **●** Starts recording. During recording it becomes **■** Stop and timer countdown visible in here|
| Cursor | Show or hide the mouse pointer in recordings |
| Timer | Countdown before recording. (Disabled / 3 / 5 / 10) seconds |
| **G** / **M** | Output format: GIF or MP4 |
| **H** / **L** | MP4 quality: high or low |
| Frame rate | Frames per second. MP4:10/15/30/60. GIF:5/10/20/25/30/50. Each format has its own value |
| **⌃** / **⌄** | Move the bar above or below the frame |
| **✕** | Hides frame |

- During recording the frame turns red, and the elapsed time is shown in the bar

### Countdown timer

With a timer set, clicking Record starts a countdown. Record button turns orange and shows the seconds left, and the frame turns orange too. Hover button to see a **✕** and click it to cancel countdown. Recording starts automatically when the countdown reaches zero

### Stopping

Click **■**, or click the frame or press **Esc**

Esc works in these steps:
1. During a countdown, it cancels the countdown
2. During recording, it stops the recording
3. Otherwise, it hides the frame

After stopping recording, Record button shows **…** while the file is finished. Then notification appears with buttons for **Show** and **Edit**

### MP4

- **Encoding:** H.264 video, encoded by Windows Media Foundation using your graphics card's hardware encoder when available
- **Quality:** constant-quality mode, so file size follows the content: a still screen uses very little space. The **H/L** button switches between two quality levels that you can tune in `settings.ini` (`Mp4QualityHi`, `Mp4QualityLo`; lower values are better)
- **Fast path:** when the recording area is on a single monitor, frames go straight from
  the screen to the encoder on the graphics card, without a round trip through system
  memory

> Windows "N" editions don't include Media Foundation. Install the **Media Feature Pack**
> (Settings → Apps → Optional features) to record MP4. GIF recording works without it.

### GIF

uCapture has its own GIF encoder:

- **One palette** for the whole GIF, built from all recorded frames, so colours never flicker
- **Smart dithering:** gradients and photos are smoothed, while flat UI colours and text stay crisp
- **Small files:** only the changed part of each frame is stored, and if nothing changes,
  no frame is added at all. This results 50% smaller gif files compared to other solutions
- **Exact timing:** frames are captured at exactly the GIF frame rate, so every captured frame becomes one GIF frame. 20, 25 and 50 fps play at exactly that speed
- **Progress:** while the GIF is built after recording, the notification shows the progress.

Colours, dithering, looping and frame rate are set in the `[Gif]` section of `settings.ini`.

### Capture method

By default, recordings use **Desktop Duplication**, the same API screen-sharing apps use.
It's fast, and an unchanged screen costs almost nothing. It falls back to classic GDI method automatically where Desktop Duplication isn't available. If you ever get
black or frozen recordings, set `[Record] CaptureMethod=gdi`.

---

## After a capture

### Notification

A small popup appears at the bottom of the screen after each capture:

- **Show** opens the captures folder with the new file selected
- **Edit** opens the file in your editor

It closes by itself after a few seconds. It never steals focus from the window you are working in, and it never appears in your captures

### Clipboard

Every screenshot is also copied to the clipboard as an image, ready to paste into chat apps, documents or image editors. With several monitors, the clipboard gets one image of the whole desktop. Turn this off with `[Capture] CopyToClipboard=0`

### Editors

The first time you press **Edit**, uCapture asks you to choose a program, separately for
images, MP4 videos and GIFs. Your choice is saved in `[Editors]` in `settings.ini` and used from then on. After **Capture Screens**, `PreferredMons` controls which monitors' images are opened

---

## Colour picker

**Tray → Color picker** shows a 4× magnifier with the values of color

| Action | Copies |
|---|---|
| **Left-click** | `#RRGGBB` (hex) |
| **Ctrl + left-click** | `RGB(R, G, B)` |
| **Right-click** | `R, G, B` |
| **Shift** (while moving) | Slows the cursor down for fine positioning |
| **Esc** | Cancel |

After picking, a notification in the picked colour shows the copied value

---

## Command line

Every capture can be started from the command line, a script, a shortcut or a hotkey tool
(AutoHotkey, PowerToys Keyboard Manager, a Stream Deck…)

```
uCapture.exe <command>
```

| Command | What it does |
|---|---|
| `RegionDraw` | Draw a region to capture |
| `LastRegion` | Capture the last region again |
| `RegionPick` | Click a window (or the desktop for a monitor) to capture it |
| `CaptureScreens <n / "1,2,3">` | `0` or blank argument captures all monitors<br> `n` captures targeted screen<br> Or use a list with comma for a selective capture `"1,3,5"` |
| `CaptureRect "x y w h"` | Capture a rectangle in screen pixels |
| `ColorPicker` | Open the colour picker |
| `OpenFolder` | Open the captures folder |

- **Syntax:** commands are case-insensitive and may start with `-`, `--` or `/` (`uCapture.exe -RegionDraw` works too)
- **Running instance:** if uCapture is already running, the command is sent to it and the
  command launchs immediately. Otherwise uCapture starts in the tray and runs the command
- **Help:** an unknown command shows a help window listing all commands

**Examples:**

```
uCapture.exe RegionDraw
uCapture.exe CaptureScreens 2
uCapture.exe CaptureScreens "1,3,5"
uCapture.exe CaptureRect "100 200 800 600"
```

---

## Keyboard and mouse

| Where | Input | Action |
|---|---|---|
| Region draw | Drag | Draw the region |
| Region draw | Shift | Use aspect ratio as 1:1 (Square) |
| Region draw | Ctrl | Keep aspect ratio |
| Region draw | Right-click / Esc | Cancel |
| Region Pick | Click | Capture the highlighted window or monitor |
| Region Pick | Shift | Highlight screen that contains cursor and click to capture |
| Region Pick | Right-click / Esc | Cancel |
| Recording frame | Drag bar | Drag to move frame |
| Recording frame | Drag edge or corner | Resize (Ctrl = keep ratio, Shift = use aspect ratio as 1:1 (Square)) |
| Recording frame | Esc | Cancel countdown → stop recording → hide frame |
| Colour picker | Left-click | Copy `#RRGGBB` |
| Colour picker | Ctrl + left-click | Copy `RGB(R, G, B)` |
| Colour picker | Right-click | Copy `R, G, B` |
| Colour picker | Shift | Fine movement |
| Colour picker | Esc | Cancel |

---

## Settings

All settings lives in `settings.ini` next to `uCapture.exe`. You can quickly access it from **Tray → More → Settings**

- Close uCapture before editing settings because the app saves its settings when it exits

Highlights (Non listed settings controlled by UI):

| Setting | What it controls |
|---|---|
| `[Capture] ImageFormat` | (`png`/`jpg`) Lossless png is the default|
| `[Capture] JpgQuality` | Quality setting for jpg format with (50-100) range |
| `[Capture] CopyToClipboard` | Also copy screenshots to the clipboard after capture (1/0)|
| `[Capture] CaptureMonsToOne` | One combined image for **Capture Screens** (1/0)|
| `[Capture] Shutter` | Shutter effect after capturing screen(s) (1/0)|
| `[Capture] PreferredMons` | 0 - **Capture Screens** will capture all monitors. You can chooice which monitors to capture with a numbers list (like 2,3,5) |
| `[Record] Mp4QualityHi` / `Mp4QualityLo` | MP4 quality levels for the H/L button |
| `[Record] Timer` | Countdown before recording (0/3/5/10)|
| `[Record] CaptureMethod` | (`auto`/`gdi`) Auto is the default and uses Desktop Duplication method |
| `[Record] Osd` | Informations that centered on frame (1/0) |
| `[Record] FPS Cursor Quality` | MP4 frame rate(10/15/30/60), Cursor(1/0) and Quality(1/0) |
| `[Gif] FPS Colors Dither Loop` | GIF frame rate(10/20/30/50), colors(256), dithering(1/0) and looping(1/0) |
| `[Output] Dir` | Where captures are saved |
| `[Editors] Image Video Gif` | Editor program paths used by the **Edit** button |

---

## Captured files

Captures are saved to `%USERPROFILE%\Desktop\Captures` by default; You can change it with
`[Output] Dir`. If the folder can't be created (for example a disconnected drive), captures go
to the default folder instead

- **Environment variables** are supported on paths. So you don't have worry about user name while using documents, desktop or your custom folder that placed on user folder

Captures are named with proper timestamp;

| Capture | Example |
|---|---|
| Screenshot | `20261016_153012_Screenshot.png` |
| One of several screens | `20261016_153012_Screenshot_Screen_2.png` |
| MP4 recording | `20261016_153012_Recording.mp4` |
| GIF recording | `20261016_153012_Recording.gif` |

---

## Privacy

- **No network access:** never requests internet connection. no telemetry, no update check
- **Local only:** settings are stored in `settings.ini` next to the exe, and captures are saved only to your captures folder that you choice

---

## Verifying your download

Each release lists the **SHA-256** checksum and a link to its **VirusTotal** scan.
To check that your download is the original file, open PowerShell in the download folder and run:

```powershell
Get-FileHash .\uCapture.exe -Algorithm SHA256
```

The result must match the checksum in the release notes.

uCapture is a small, new and unsigned app, Windows SmartScreen may show "Windows protected your PC" the first time.
Click **More info → Run anyway** if the checksum matches.

---

## System requirements

- Windows 10 and higher (x64)
- MP4 recording: Windows Media Foundation (included in Windows, except "N" editions without the Media Feature Pack)
- Hardware video encoding: any GPU with a Windows H.264 encoder (NVIDIA, AMD, Intel); otherwise Windows' software encoder is used automatically
- DPI aware: sharp on high-DPI and mixed-DPI setups

---

## License

See [LICENSE](LICENSE).
