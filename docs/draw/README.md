# Boojy Draw

**Free, open-source digital painting & illustration app**

![Preview Status](https://img.shields.io/badge/status-preview-orange)
![Platform](https://img.shields.io/badge/platform-macOS%20%7C%20Windows-blue)
![License](https://img.shields.io/badge/license-MIT-green)

> Part of the [Boojy Suite](https://github.com/tsbujacncl/boojy) — a creative ecosystem for hobbyists and indie creators.

---

## Overview

Boojy Draw is an expressive digital painting and illustration app built with Flutter. It combines natural-feeling brushes with a simple, learnable interface—powerful enough for finished artwork, approachable enough for beginners.

**Current Phase:** Early Preview (Weeks 3-4 of 12-week sprint)

### What's This Preview?

A **2-week MVP** focused on proving core painting workflows:
- ✏️ Natural brush strokes with pressure sensitivity
- 🎨 Essential layer operations with blend modes
- 🔧 Selection & transform tools
- 💾 Project save/load with `.draw` format
- ☁️ Optional Boojy Cloud backup

**Not included yet:** custom brush editor, masks, text, symmetry tools, filters, animation.

---

## Features (Preview)

### Canvas
- Presets: A4, Square (1000×1000), HD (1920×1080)
- Custom sizes up to 5000×5000 pixels
- Zoom, pan, rotate view

### Brushes (5 Essential Tools)
- **Pencil** — crisp, aliased strokes
- **Pen** — smooth, anti-aliased ink
- **Marker** — soft-edge, buildable opacity
- **Airbrush** — spray effect with falloff
- **Eraser** — clear pixels or reduce opacity

**Controls:** size, opacity, pressure curves, eyedropper

### Colours
- HSV colour wheel
- Recent swatches (8 slots)
- Eyedropper tool

### Layers
- Unlimited layers (RAM-limited)
- Opacity per layer
- Blend modes: Normal, Multiply, Screen, Overlay, Add
- Operations: show/hide, lock, merge, reorder

### Selection & Transform
- **Select:** rectangle, lasso, magic wand (tolerance)
- **Transform:** move, scale, rotate, flip
- **Refine:** feather edges

### History
- Undo/redo (Cmd+Z / Cmd+Shift+Z)
- Compact history panel

### Project Management
- Save/load `*.draw` files (JSON + PNG layers)
- Autosave every 2 minutes
- Optional Cloud sync (Boojy Cloud, opt-in)

### Export
- PNG (with transparency)
- JPG (flatten, quality slider)

---

## Tech Stack

- **Framework:** Flutter 3.24+ (desktop: macOS 12+, Windows 10+)
- **Rendering:** Flutter CustomPainter + Skia (GPU-accelerated)
- **Stylus:** Pointer events API (pressure, tilt support for Wacom, Surface, Apple Pencil via sidecar)
- **Stabilization:** Kalman filter for smooth mouse/stylus strokes
- **File Format:** JSON metadata + gzip-compressed PNG blobs
- **Dependencies:**
  - `boojy_core` (shared UI shell, theme, file dialogs, undo/redo)
  - `image` (Dart image manipulation)
  - `path_provider` (local file I/O)

---

## Getting Started

### Prerequisites
- Flutter 3.24+ ([install](https://flutter.dev/docs/get-started/install))
- macOS 12+ or Windows 10+
- 8 GB RAM recommended (4 GB minimum)

### Install & Run

```bash
# Clone the repo
git clone https://github.com/tsbujacncl/boojy-draw.git
cd boojy-draw

# Get dependencies
flutter pub get

# Run on desktop
flutter run -d macos   # or -d windows
```

### Build

```bash
# macOS
flutter build macos --release

# Windows
flutter build windows --release
```

Binaries will be in `build/macos/Build/Products/Release/` or `build/windows/runner/Release/`.

---

## Project Structure

```
boojy-draw/
├── lib/
│   ├── main.dart              # App entry point
│   ├── canvas/                # Canvas rendering, brush engine
│   ├── layers/                # Layer management, compositing
│   ├── tools/                 # Brushes, selection, transform
│   ├── ui/                    # Panels, toolbars (uses boojy_core)
│   └── file/                  # .draw file I/O, autosave
├── assets/                    # Icons, presets
├── test/                      # Unit & widget tests
└── pubspec.yaml
```

---

## Roadmap

### Preview (Current - Weeks 3-4)
- Core painting workflow
- 5 brushes + pressure
- Layers with blend modes
- Selection & transform
- File save/load

### v1.0 (Months 6-7)
- Custom brush editor
- Layer masks
- Symmetry tools (horizontal, vertical, radial)
- Text layers
- Basic filters (blur, sharpen, adjust levels)

**See [SPRINT-MVP.md](./SPRINT-MVP.md) for detailed preview plan.**

---

## Testing the Preview

We're looking for feedback from illustrators, hobbyists, and digital artists!

### What to Test
1. **Brush feel:** Does pressure feel natural with a stylus? Is mouse drawing usable?
2. **Layers:** Are blend modes intuitive? Can you finish a multi-layer piece?
3. **Selection:** Do selection tools work as expected?
4. **Performance:** Does 3000×3000 canvas stay responsive?
5. **Stability:** Any crashes or data loss?

### Report Issues
- [GitHub Issues](https://github.com/tsbujacncl/boojy-draw/issues)
- Include: OS, device (mouse/stylus), canvas size, steps to reproduce

---

## Success Criteria (Preview)

✅ **Tester can finish a complete illustration** in one session
✅ **Pressure sensitivity rated ≥4/5** by stylus users
✅ **Layer operations feel obvious** (no documentation needed)
✅ **Mouse drawing usable** with stabilization
✅ **No data-loss bugs** or critical crashes

---

## Contributing

Boojy Draw is open source! We welcome contributions:
- 🐛 Bug fixes
- ✨ Feature implementations (check [Issues](https://github.com/tsbujacncl/boojy-draw/issues) for "good first issue")
- 📝 Documentation improvements

See [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines.

---

## License

MIT License - see [LICENSE](./LICENSE)

---

## Community

- **Main Repo:** [Boojy Suite](https://github.com/tsbujacncl/boojy)
- **Website:** [boojy.app](https://boojy.app) (coming soon)
- **Discord:** (coming soon)

---

## Positioning

**Boojy Draw** — Simple enough for hobbyists, powerful enough for pros.
Part of a free, open-source creative suite that works the way you do.
