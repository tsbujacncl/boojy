# Boojy Draw — Early Preview Sprint (MVP)

**2-Week Sprint: Weeks 3-4 of Boojy Suite Preview**
**Goal:** Ship a usable digital painting app that proves core workflows and validates cross-platform Flutter desktop.

---

## Table of Contents

1. [Sprint Overview](#sprint-overview)
2. [Success Criteria](#success-criteria)
3. [Technical Architecture](#technical-architecture)
4. [Feature Specifications](#feature-specifications)
5. [Sprint Timeline](#sprint-timeline)
6. [Testing Plan](#testing-plan)
7. [Risks & Mitigation](#risks--mitigation)

---

## Sprint Overview

### Objective
Build an **actually usable** painting app in 2 weeks where testers can:
- Start a new canvas
- Paint with natural-feeling brushes (stylus + mouse)
- Organize work in layers with blend modes
- Select and transform regions
- Save/load projects
- Export clean PNG/JPG

### Scope: In vs. Out

#### ✅ In Scope (Preview)
- Canvas with presets + zoom/pan/rotate
- 5 brushes (pencil, pen, marker, airbrush, eraser)
- Pressure sensitivity + stroke stabilization
- Unlimited layers with 5 blend modes
- Selection tools (rect, lasso, wand)
- Transform (move, scale, rotate, flip)
- Undo/redo
- `.draw` file format (save/load)
- Autosave
- Cloud sync (opt-in, via boojy_core)
- Export PNG/JPG

#### ❌ Out of Scope (v1.0+)
- Custom brush editor
- Layer masks
- Text layers
- Symmetry tools
- Filters/adjustments (blur, sharpen, curves)
- Animation/onion skinning
- Reference images
- Gradient fills
- Vector tools

---

## Success Criteria

### User Experience Metrics
- **Avg rating ≥4/5** from tester survey
- **≥70%** say they'd use Boojy Draw for real work
- **≥80%** complete test tasks without help
- **Pressure sensitivity ≥4/5** rating from stylus users
- **Mouse users can finish a piece** with stabilization

### Technical Metrics
- **≥99% crash-free rate** (zero data-loss bugs)
- **Startup time <2s** on 8 GB RAM, SSD
- **Canvas 3000×3000, 10 layers** stays responsive (≥30 FPS)
- **Autosave completes in <500ms** (non-blocking)
- **Export 5000×5000 PNG in <5s**

### Functional Gates
- ✅ Finish a complete multi-layer illustration
- ✅ Pressure curves feel natural (no lag, accurate)
- ✅ Layers blend correctly (Normal, Multiply, Screen, Overlay, Add)
- ✅ Selection tools work on first try
- ✅ Save/load preserves all data (layers, blends, colours)
- ✅ Cloud sync doesn't lose work

---

## Technical Architecture

### Tech Stack

| Component | Technology |
|-----------|-----------|
| **Framework** | Flutter 3.24+ (desktop) |
| **Rendering** | CustomPainter + Skia (GPU) |
| **Stylus Input** | Pointer events API (pressure, tilt) |
| **Stabilization** | Kalman filter (mouse/stylus) |
| **File Format** | JSON + gzip PNG blobs |
| **State Management** | Provider or Riverpod |
| **Undo/Redo** | boojy_core command pattern |
| **UI Shell** | boojy_core (theme, panels, dialogs) |

### Dependencies

```yaml
dependencies:
  flutter:
    sdk: flutter

  # Boojy Core (shared UI & framework)
  boojy_core:
    git:
      url: https://github.com/tsbujacncl/boojy-core.git
      ref: main

  # Image manipulation
  image: ^4.0.0

  # File I/O
  path_provider: ^2.1.0
  file_picker: ^6.0.0

  # State management
  provider: ^6.1.0

  # Cloud (optional, via boojy_core)
  # firebase_core, firebase_storage (boojy_core handles)
```

### Architecture Diagram

```
┌─────────────────────────────────────────────────┐
│              UI Layer (boojy_core)              │
│  ┌─────────┬──────────┬──────────┬───────────┐ │
│  │ Toolbar │ Brush    │ Layers   │ Colour    │ │
│  │         │ Panel    │ Panel    │ Picker    │ │
│  └─────────┴──────────┴──────────┴───────────┘ │
└─────────────────────────────────────────────────┘
                       ↓
┌─────────────────────────────────────────────────┐
│            Canvas Controller                    │
│  - Manages viewport (zoom, pan, rotate)         │
│  - Dispatches tool events                       │
│  - Coordinates layers & rendering               │
└─────────────────────────────────────────────────┘
           ↓                    ↓
┌──────────────────┐   ┌────────────────────────┐
│  Brush Engine    │   │  Layer Manager         │
│  - Stroke buffer │   │  - Layer stack         │
│  - Pressure map  │   │  - Blend compositor    │
│  - Stabilizer    │   │  - Raster cache        │
└──────────────────┘   └────────────────────────┘
           ↓
┌─────────────────────────────────────────────────┐
│       Renderer (CustomPainter + Skia)           │
│  - Composites layers with blend modes           │
│  - Draws active stroke overlay                  │
│  - GPU-accelerated where possible               │
└─────────────────────────────────────────────────┘
           ↓
┌─────────────────────────────────────────────────┐
│          File I/O & Persistence                 │
│  - .draw format (JSON + PNG blobs)              │
│  - Autosave background thread                   │
│  - Cloud sync (boojy_core)                      │
└─────────────────────────────────────────────────┘
```

---

## Feature Specifications

### 1) Canvas

#### Presets
| Name | Size | Aspect | Use Case |
|------|------|--------|----------|
| **A4 Portrait** | 2480×3508 @ 300 DPI | 1:√2 | Print illustration |
| **Square** | 1000×1000 | 1:1 | Social media icon |
| **HD Landscape** | 1920×1080 | 16:9 | Wallpaper/concept |

**Custom:** Width/height input (100–5000 px), DPI selector (72/150/300).

#### Viewport Controls
- **Zoom:** 10%–3200% (Cmd+Plus/Minus, pinch/scroll)
- **Pan:** Space+drag, two-finger drag
- **Rotate:** Cmd+drag rotate handle (bottom-right), snap to 0°/90°/180°/270°
- **Fit to window:** Cmd+0

#### Performance Targets
- 60 FPS pan/zoom up to 3000×3000, 10 layers
- 30 FPS acceptable for 5000×5000

---

### 2) Brushes

#### Brush Types (Preview)

| Brush | Behaviour | Pressure Response | Stabilization |
|-------|-----------|-------------------|---------------|
| **Pencil** | Hard-edge, aliased | Size only | Light (0.3) |
| **Pen** | Smooth, anti-aliased | Size + opacity | Medium (0.5) |
| **Marker** | Soft-edge, buildable | Opacity | Medium (0.5) |
| **Airbrush** | Spray falloff | Flow rate | Heavy (0.7) |
| **Eraser** | Clear or reduce alpha | Size + opacity | Light (0.3) |

#### Brush Settings Panel
- **Size:** 1–500 px (slider + number input)
- **Opacity:** 0–100% (slider)
- **Pressure Curve:** dropdown (Linear, Ease In, Ease Out, S-Curve)
- **Preview:** live stroke preview on hover over settings

#### Pressure Mapping (Stylus)
- **Curve Types:**
  - **Linear:** 1:1 pressure to effect
  - **Ease In:** gentle start, strong finish
  - **Ease Out:** strong start, gentle finish
  - **S-Curve:** gentle both ends, strong middle

- **Fallback (Mouse):** Size follows cursor speed (fast = thin, slow = thick) + stabilization

#### Stroke Stabilization
- **Algorithm:** Kalman filter or weighted moving average
- **Strength:** 0.0 (off) – 1.0 (max smoothing)
  - Pencil: 0.3
  - Pen/Marker: 0.5
  - Airbrush: 0.7
- **Lag tolerance:** <16ms (1 frame at 60 FPS)

#### Technical Implementation
```dart
class BrushStroke {
  List<StrokePoint> points;
  BrushType type;
  double size;
  double opacity;
  Color color;
  PressureCurve curve;

  void addPoint(Offset position, double pressure, double tilt) {
    // Apply stabilization
    Offset stabilized = _stabilizer.filter(position);
    // Map pressure via curve
    double mappedPressure = curve.map(pressure);
    points.add(StrokePoint(stabilized, mappedPressure, tilt));
  }

  void render(Canvas canvas) {
    // Render stroke with brush characteristics
  }
}
```

---

### 3) Colour Picker

#### UI Components
- **HSV Wheel:** circular hue ring + SV triangle
- **Hex Input:** `#RRGGBB` or `#RRGGBBAA`
- **RGBA Sliders:** 0–255 (when wheel closed)
- **Recent Swatches:** 8 slots, MRU order
- **Eyedropper:** Cmd+click canvas (or `I` key)

#### Eyedropper Behaviour
- Samples **current layer only** by default
- Hold **Alt** to sample **all visible layers** (flattened)

---

### 4) Layers

#### Layer Stack
- **Unlimited layers** (RAM-limited, ~50–100 typical)
- Each layer:
  - **Thumbnail:** 64×64 preview
  - **Name:** "Layer 1", "Layer 2", ... (editable)
  - **Visibility:** eye icon toggle
  - **Lock:** lock icon (prevents edits)
  - **Opacity:** 0–100% slider
  - **Blend Mode:** dropdown

#### Blend Modes (Preview)
| Mode | Formula | Use Case |
|------|---------|----------|
| **Normal** | `src` | Default |
| **Multiply** | `src × dst` | Shadows, darken |
| **Screen** | `1 - (1-src)×(1-dst)` | Highlights, lighten |
| **Overlay** | Multiply < 0.5, Screen ≥ 0.5 | Contrast boost |
| **Add** | `src + dst` (clamped) | Glow, light effects |

#### Layer Operations
- **New Layer:** Cmd+Shift+N
- **Duplicate:** Cmd+J
- **Merge Down:** Cmd+E
- **Flatten All:** Shift+Cmd+E
- **Reorder:** drag in panel
- **Delete:** Delete key (with confirmation if layer has content)

#### Technical Implementation
```dart
class Layer {
  ui.Image raster;  // PNG bitmap
  String name;
  bool visible;
  bool locked;
  double opacity;
  BlendMode blendMode;

  void composite(Canvas canvas, Rect viewport) {
    if (!visible) return;
    Paint paint = Paint()
      ..blendMode = blendMode
      ..color = Color.fromRGBO(255, 255, 255, opacity);
    canvas.drawImage(raster, Offset.zero, paint);
  }
}
```

---

### 5) Selection & Transform

#### Selection Tools

| Tool | Behaviour | Keyboard Shortcut |
|------|-----------|-------------------|
| **Rectangle** | Click+drag rect | `M` |
| **Lasso** | Freehand path | `L` |
| **Magic Wand** | Flood-fill by tolerance | `W` |

**Modifiers:**
- **Add to selection:** Shift+tool
- **Subtract:** Alt+tool
- **Intersect:** Shift+Alt+tool

**Tolerance (Wand):** 0–100 slider (default 32)

**Feather:** 0–100 px (softens selection edge)

#### Transform Operations
- **Move:** drag selection (or arrow keys: 1px, Shift+arrow: 10px)
- **Scale:** corner handles (hold Shift = constrain aspect)
- **Rotate:** rotate handle (Shift = snap 15°)
- **Flip:** Horizontal / Vertical buttons
- **Apply:** Enter (rasterize)
- **Cancel:** Esc

**Anti-aliasing:** Use bicubic interpolation for scale/rotate.

---

### 6) History (Undo/Redo)

#### Implementation
- **Command Pattern** (via boojy_core)
- **Stack Size:** 50 actions (configurable in prefs)
- **Memory:** Store incremental diffs, not full layer copies (for large canvases)

#### Actions Tracked
- Brush strokes
- Layer operations (new, delete, merge, reorder)
- Transform (move, scale, rotate)
- Selection changes
- Colour/brush setting changes (grouped per stroke)

#### UI
- **Undo:** Cmd+Z
- **Redo:** Cmd+Shift+Z
- **History Panel:** compact list (optional, low priority)

---

### 7) File Format (*.draw)

#### Structure
```json
{
  "version": "0.1",
  "canvas": {
    "width": 3000,
    "height": 2000,
    "dpi": 300
  },
  "layers": [
    {
      "id": "uuid-1",
      "name": "Background",
      "visible": true,
      "locked": false,
      "opacity": 1.0,
      "blendMode": "normal",
      "data": "layer_uuid-1.png"  // embedded or external
    },
    {
      "id": "uuid-2",
      "name": "Sketch",
      "visible": true,
      "locked": false,
      "opacity": 0.6,
      "blendMode": "multiply",
      "data": "layer_uuid-2.png"
    }
  ],
  "metadata": {
    "created": "2025-11-03T12:00:00Z",
    "modified": "2025-11-03T14:30:00Z",
    "author": "User Name",
    "thumbnail": "thumbnail.png"  // 512×512
  }
}
```

#### Storage
- **Container:** ZIP archive (or single JSON if small)
- **Compression:** gzip on PNGs (lossless)
- **Thumbnail:** 512×512 PNG for Cloud preview

#### Compatibility
- **Forward-compatible:** Ignore unknown fields
- **Version migration:** `0.1` → `1.0` handled by boojy_core

---

### 8) Autosave

#### Behaviour
- **Frequency:** Every 2 minutes (if canvas modified)
- **Location:** `~/Documents/Boojy/Autosaves/`
- **Naming:** `{project-name}_autosave_{timestamp}.draw`
- **Retention:** Keep last 3 autosaves, delete older
- **Recovery:** On launch, check for autosaves newer than last saved file

#### Implementation
- Run on background isolate (non-blocking)
- Use file lock to prevent corruption
- Show subtle "Autosaving..." indicator (bottom-right, 1s fade)

---

### 9) Export

#### Formats

| Format | Options | Use Case |
|--------|---------|----------|
| **PNG** | Transparency, compression | Web, print (lossless) |
| **JPG** | Quality 1–100, flatten | Web, photos (lossy) |

#### Export Dialog
- **Format:** dropdown (PNG/JPG)
- **Size:** Current / 50% / 200% / Custom
- **Quality (JPG):** slider (default 85)
- **Flatten:** checkbox (JPG auto-flattens)
- **Transparent BG (PNG):** checkbox

#### Performance
- **Target:** 5000×5000 PNG in <5s
- Use Dart `image` package with isolate for encoding

---

## Sprint Timeline

### Week 3: Core Painting (Days 1–7)

#### Day 1-2: Canvas & Basic UI
- [ ] Set up Flutter project + boojy_core integration
- [ ] Canvas widget with zoom/pan (no rotate yet)
- [ ] Toolbar scaffold (brush selector, size/opacity sliders)
- [ ] Colour picker (HSV wheel)

#### Day 3-4: Brush Engine
- [ ] Implement Pencil + Pen brushes
- [ ] Stylus pressure input (test with Wacom/Surface)
- [ ] Stroke stabilization (Kalman filter)
- [ ] Mouse fallback (speed-based size)

#### Day 5: Layers (Basics)
- [ ] Layer stack (add, delete, reorder)
- [ ] Layer visibility + opacity
- [ ] Normal blend mode rendering

#### Day 6: Remaining Brushes
- [ ] Marker + Airbrush + Eraser
- [ ] Pressure curve dropdown
- [ ] Brush preview

#### Day 7: Testing & Polish
- [ ] Test on macOS + Windows
- [ ] Fix stylus lag/jitter
- [ ] Optimize rendering for 3000×3000

---

### Week 4: Layers, Tools & Export (Days 8–14)

#### Day 8-9: Blend Modes & Layer Ops
- [ ] Implement 4 blend modes (Multiply, Screen, Overlay, Add)
- [ ] Layer merge, duplicate, flatten
- [ ] Thumbnail generation per layer

#### Day 10: Selection Tools
- [ ] Rectangle + Lasso selection
- [ ] Magic Wand (tolerance slider)
- [ ] Marching ants UI

#### Day 11: Transform
- [ ] Move, scale, rotate on selection
- [ ] Flip horizontal/vertical
- [ ] Apply/cancel transform

#### Day 12: File I/O
- [ ] Save `.draw` format (ZIP + JSON)
- [ ] Load `.draw` with layer restoration
- [ ] Autosave every 2 min
- [ ] Thumbnail generation

#### Day 13: Export & Cloud
- [ ] Export PNG/JPG
- [ ] Cloud sync (opt-in, via boojy_core)
- [ ] Undo/redo integration

#### Day 14: Final Testing & Package
- [ ] End-to-end test: create, save, load, export
- [ ] Pressure test with 10+ layers, 5000×5000
- [ ] Fix critical bugs
- [ ] Build macOS + Windows packages
- [ ] Write README & CONTRIBUTING

---

## Testing Plan

### Internal Testing (Day 7, 14)
- **Devices:**
  - macOS 13 (Intel + Apple Silicon)
  - Windows 11 (x64)
- **Stylus:**
  - Wacom Intuos Pro
  - Surface Pen
  - Apple Pencil (via sidecar)
- **Mouse:**
  - Standard USB mouse (test stabilization)

### Tester Scenarios (Week 4 End)

#### Scenario 1: Simple Illustration
1. Create 1920×1080 canvas
2. Sketch outline with Pen (pressure)
3. Add colour on new layer (Marker)
4. Use Multiply blend for shadows
5. Erase mistakes
6. Export PNG

**Success:** Complete in <20 min, no confusion

#### Scenario 2: Complex Layering
1. Create 3000×3000 canvas
2. Build 10+ layers (base, sketch, flats, shadows, highlights)
3. Use all 5 blend modes
4. Merge some layers
5. Save project
6. Reload and verify all layers intact

**Success:** No data loss, blend modes render correctly

#### Scenario 3: Selection & Transform
1. Draw on layer
2. Select region (lasso)
3. Scale + rotate selection
4. Move to new position
5. Apply transform

**Success:** Transformation smooth, no artifacts

---

## Risks & Mitigation

### Technical Risks

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| **Stylus pressure unreliable** | Medium | High | Test early (Day 3), fallback to mouse mode if needed |
| **Rendering lag on large canvas** | Medium | High | Profile on Day 7, optimize compositor, use GPU layers |
| **Blend modes incorrect** | Low | Medium | Unit test each mode against reference images |
| **File I/O corrupts data** | Low | Critical | Validate ZIP integrity, write tests for save/load round-trip |
| **Cross-platform UI bugs** | Medium | Medium | Test Windows build daily from Day 5 |

### Schedule Risks

| Risk | Likelihood | Impact | Mitigation |
|------|-----------|--------|------------|
| **Boojy Core not ready** | Low | High | Use placeholder UI if needed, integrate later |
| **Brush engine takes >2 days** | Medium | High | Start with basic strokes, add pressure curves later |
| **Testing reveals showstoppers** | Medium | High | Day 14 is buffer; cut export features if needed |

---

## Post-Sprint

### Success → v1.0 (Months 6-7)
If preview hits success criteria:
- Custom brush editor
- Layer masks
- Symmetry tools
- Text layers
- Filters (blur, sharpen, levels)

### Pivot → Iterate
If <3/5 rating or critical bugs:
- Identify top 3 pain points
- 1-week focused sprint
- Re-test with same cohort

---

## Appendix: Key Metrics Checklist

Before shipping:
- [ ] Pressure sensitivity rated ≥4/5 by 3+ stylus users
- [ ] Mouse users complete a piece (with stabilization)
- [ ] 3000×3000, 10 layers renders at ≥30 FPS
- [ ] Save/load preserves all layer data
- [ ] Zero data-loss bugs in testing
- [ ] Export PNG matches canvas
- [ ] Autosave recovers unsaved work
- [ ] Builds run on fresh macOS + Windows installs
