# 🎨 Boojy Suite – Early Preview Design Document

> **Version:** 0.1 Preview Phase  
> **Date:** November 2025  
> **Timeline:** 2-Month Sprint (Weeks 1-10)  
> **Purpose:** Development guide and tester onboarding for Boojy Suite Preview apps

---

## 1. Executive Summary

**What is Boojy Suite?**

Boojy Suite is a free, open-source ecosystem of creative tools designed to replace Adobe Creative Cloud for hobbyists, students, and independent creators. The suite includes:

- **Boojy Audio** – Digital audio workstation (DAW)
- **Boojy Draw** – Digital illustration and painting
- **Boojy Design** – Photo editing and vector design
- **Boojy Board** – Note-taking and visual brainstorming
- **Boojy Video** – Video editing with motion graphics
- **Boojy Animate** – 2D animation
- **Boojy Score** – Music notation
- **Boojy Cloud** – Creative-aware storage and sync

**Why a Preview Phase?**

Before investing 20+ months in full development, we're building **Preview versions** of Audio, Draw, Design, Board, and Cloud to:

- Validate core workflows with real users
- Gather early feedback to guide v1.0 feature priorities
- Test cross-platform compatibility (Windows/Mac)
- Test cloud sync between apps
- Build community before public launch
- Ensure "it just works" philosophy from day one

**Preview Timeline:**

- **Weeks 1-2:** Build Boojy Audio Preview
- **Weeks 3-4:** Build Boojy Draw Preview
- **Weeks 5-6:** Build Boojy Design Preview
- **Weeks 7-8:** Build Boojy Cloud Preview
- **Weeks 9-10:** Build Boojy Board Preview
- **Weeks 11-12:** Holistic testing (all five components together)
- **Week 13:** Analyze feedback and identify patterns
- **Week 14:** Adjust roadmap and finalize v1.0 plans

---

## 2. Preview Philosophy

### Core Principles

**Foundation, Not Throwaway**

- Preview code becomes the foundation for v1.0 (not prototype to discard)
- Clean architecture from day one
- Flutter codebase designed for future platform expansion

**Actually Usable**

- Not just tech demos—testers should be able to create real work
- Audio: Record and mix an actual song
- Draw: Create finished digital art
- Design: Edit photos and design simple posters
- Cloud: Sync projects across devices seamlessly

**"It Just Works"**

- Intuitive UI inspired by GarageBand and iMovie
- No manual required for basic tasks
- Minimal friction between idea and creation

**Hobbyist-First**

- Features prioritized for accessibility over pro complexity
- Friendly to beginners, powerful enough for regular use
- Advanced features come in v1.0+, not Preview

---

## 3. Boojy Audio Preview

### Overview

Full-featured 4+ track recorder with plugin support and basic MIDI capabilities. Inspired by GarageBand meets Ableton Live.

### Feature List

#### ✅ Recording & Playback

- Record audio via microphone input
- Import audio files (.wav, .mp3, .flac, .aiff)
- Multi-track recording (record multiple sources simultaneously)
- Playback controls (play, pause, stop, loop region)
- Click track/metronome (adjustable BPM)
- Waveform display with zoom/pan

#### ✅ Tracks

- **4+ audio tracks** (expandable based on system performance)
- Volume faders (per track + master)
- Pan controls (stereo positioning)
- Mute/solo buttons
- Track color coding
- Track naming and organization

#### ✅ Basic MIDI Support

- MIDI recording (keyboard input)
- Piano roll editor (basic note editing)
- Velocity editing
- Quantization (snap to grid)
- Virtual instruments (2-3 basic presets: piano, synth, drums)

#### ✅ Plugin Support ⭐

- VST plugin loading (reverb, delay, EQ, compression)
- Per-track effect chains (up to 5 plugins per track)
- Real-time preview (hear changes while playing)
- Plugin preset management
- Bypass/enable toggle per plugin

#### ✅ Mixing

- Track-level volume automation (draw volume curves)
- Master output meter (prevent clipping)
- Simple EQ (3-band: low/mid/high)
- Basic compression (threshold, ratio)

#### ✅ Project Management

- Save/load projects (.audio format)
- Auto-save (every 2 minutes)
- **Cloud sync integration** (save to Boojy Cloud)
- Export mixdown (.wav, .mp3, .flac)
- Export quality settings (bit depth, sample rate)
- Project templates (empty, 4-track, 8-track)

### What's NOT in Preview

❌ Advanced automation (only volume automation)  
❌ Audio routing/buses  
❌ Advanced MIDI editing (no CC automation)  
❌ Time-stretching/pitch-shifting  
❌ Built-in synthesizers (beyond basic presets)  
❌ Video sync

### Success Criteria

- Tester can record a 3-minute song with vocals + 2-3 instruments
- Plugins load and apply effects without crashes
- Export produces clean audio file
- Cloud sync works without file corruption
- UI feels intuitive ("I figured it out without a manual")

---

## 4. Boojy Draw Preview

### Overview

Digital illustration app with pressure-sensitive brushes, unlimited layers, and essential drawing tools. Inspired by Procreate and Krita with GarageBand-level approachability.

### Feature List

#### ✅ Canvas

- Create new canvas (custom dimensions up to 5000×5000px)
- Canvas presets (A4, letter, square Instagram, HD video)
- Background color picker (or transparent)
- Zoom (pinch/scroll, up to 3200%)
- Pan (two-finger drag or spacebar+drag)
- Rotate canvas (for natural drawing angles)

#### ✅ Brushes (5 Core Types)

1. **Pencil** – Hard-edged, pressure-sensitive, sketch-friendly
2. **Pen** – Smooth ink line, pressure affects width
3. **Marker** – Soft semi-transparent edge, good for shading
4. **Airbrush** – Gradual spray effect, pressure-sensitive opacity
5. **Eraser** – Hard-edged removal, pressure affects size

#### ✅ Brush Controls

- Size slider (1-500px, pressure-sensitive)
- Opacity slider (0-100%)
- **Pressure sensitivity support** (Wacom, Apple Pencil, Surface Pen)
- Pressure curve adjustment (light/medium/heavy presets)
- Color picker (HSV color wheel)
- Recent colors palette (last 10 colors)
- Eyedropper tool (sample color from canvas)

#### ✅ Layers

- **Unlimited layers** (system memory permitting)
- Create/delete/duplicate layers
- Reorder (drag to rearrange)
- Layer opacity slider (0-100%)
- **Blend modes** (Normal, Multiply, Screen, Overlay, Add)
- Hide/show layers (eye icon)
- Lock layers (prevent editing)
- Merge layers (combine selected)

#### ✅ Selection Tools

- **Rectangle selection** (click-drag to define area)
- **Lasso selection** (freehand selection path)
- **Magic wand** (select similar colors, adjustable tolerance)
- Selection actions: cut, copy, paste, delete, move
- Transform selection (scale, rotate, flip)
- Feather selection edges (soft transitions)

#### ✅ Transform Tools

- Move tool (reposition layer content)
- Scale (proportional or free)
- Rotate (free rotation with angle input)
- Flip horizontal/vertical

#### ✅ History & Undo

- Unlimited undo/redo
- History panel (see list of actions, jump to any point)

#### ✅ Project Management

- Save/load projects (.draw format, preserves layers)
- Auto-save (every 90 seconds)
- **Cloud sync integration** (save to Boojy Cloud)
- Export flattened image (.png, .jpg, .tiff)
- Export with transparency (.png)
- Export individual layers

### What's NOT in Preview

❌ Custom brush creation  
❌ Advanced filters (blur, sharpen, distort)  
❌ Layer masks  
❌ Text tool  
❌ Symmetry mode  
❌ Animation timeline

### Success Criteria

- Tester can create finished character illustration or landscape painting
- Pressure sensitivity feels natural (like drawing on paper)
- Layer system is intuitive (testers understand layer order)
- Selection tools work smoothly for editing existing work
- Cloud sync preserves all layers without corruption

---

## 5. Boojy Design Preview

### Overview

Photo editing and vector design tool combining Photoshop + Illustrator capabilities. Replaces both for hobbyist workflows.

### Feature List

#### ✅ Photo Mode

**Import & Basic Edits**

- Import images (.jpg, .png, .tiff, .webp)
- Drag-and-drop support
- Crop tool (freeform + aspect ratio presets)
- Rotate (90° increments + free rotation)
- Resize (maintain aspect ratio toggle, smart scaling)
- Flip horizontal/vertical

**Color Adjustments**

- Brightness slider (-100 to +100)
- Contrast slider (-100 to +100)
- Saturation slider (-100 to +100)
- Temperature slider (warm/cool)
- Exposure adjustment
- Vibrance (intelligent saturation boost)
- Hue shift

**Layers**

- **Unlimited layers** (raster and vector)
- Layer types: image, shape, text
- Opacity and blend modes (same as Draw)
- Layer groups (organize related layers)
- Layer effects: drop shadow, stroke outline

**Selection Tools**

- Rectangle/ellipse selection
- Lasso (freehand)
- Magic wand (color-based)
- Select inverse, grow/shrink selection
- Feather edges

#### ✅ Vector Mode

**Shape Tools**

- Rectangle (rounded corners optional)
- Ellipse/circle
- Polygon (3-12 sides)
- Star (customizable points)
- Line tool

**Pen Tool**

- Bezier curve creation
- Add/delete anchor points
- Convert corner to curve (and vice versa)
- Path editing (adjust handles)

**Shape Properties**

- Fill color (solid, gradient, none)
- Stroke color and width (1-50px)
- Stroke style (solid, dashed)
- Corner radius (for rectangles)

**Text Tool**

- Text layers (editable after creation)
- Font selection (system fonts)
- Size, weight (bold, italic), alignment
- Character spacing (tracking/kerning)
- Line height
- Text color and stroke

#### ✅ Transform & Arrange

- Move, scale, rotate (per layer)
- Align tools (left, center, right, top, middle, bottom)
- Distribute evenly (horizontal/vertical)
- Bring to front / send to back
- Lock position (prevent accidental moves)

#### ✅ Project Management

- Save/load projects (.design format, preserves layers and vectors)
- Auto-save (every 90 seconds)
- **Cloud sync integration** (save to Boojy Cloud)
- Export flattened (.jpg, .png, .pdf)
- Export for web (optimize file size)
- Export individual layers or groups
- SVG export (vector elements only)

### What's NOT in Preview

❌ Advanced color correction (curves, levels, HSL)  
❌ Layer masks  
❌ Clipping masks  
❌ Advanced filters (blur, sharpen, noise)  
❌ Clone stamp / healing brush  
❌ Gradient mesh  
❌ Path text (text along curves)

### Success Criteria

- Tester can edit a photo (crop, color correct, add text overlay)
- Tester can design a simple poster (shapes + text + imported image)
- Pen tool feels learnable (not frustrating for beginners)
- Export produces clean, usable files
- Cloud sync preserves all layers and vectors

---

## 6. Boojy Board Preview

### Overview

Note-taking and visual brainstorming app combining the simplicity of Notability with the collaborative power of Miro. Infinite canvas for ideas, notes, and team collaboration.

### Feature List

#### ✅ Canvas & Navigation

- **Infinite canvas** (pan, zoom, unlimited workspace)
- Canvas presets (A4, whiteboard, brainstorm grid)
- Multi-touch gestures (pinch to zoom, two-finger pan)
- Canvas rotation for natural note-taking angles
- Minimap navigation (bird's-eye view of entire workspace)
- Grid overlay (optional, customizable spacing)

#### ✅ Note-Taking Tools

- **Rich text notes** (formatting, bullets, checklists)
- **Handwriting support** (Apple Pencil, Wacom, Surface Pen)
- Pressure-sensitive pen tool
- Highlighter tool (semi-transparent overlay)
- Eraser with multiple sizes
- Text-to-shape recognition (circles, squares, arrows)
- Color picker (custom colors + recent palette)

#### ✅ Sticky Notes & Cards

- Draggable sticky notes (resize, recolor)
- Card templates (to-do, idea, question, decision)
- Auto-arrange sticky notes (align, distribute, grid snap)
- Color-coding system (8 default colors)
- Pin notes to keep in place
- Link notes together (visual connections)

#### ✅ Visual Brainstorming

- **Mind map mode** (auto-layout, hierarchical branches)
- Flowchart tools (shapes, connectors, decision boxes)
- Diagrams (Venn, org chart, timeline templates)
- Freeform drawing tools (pen, marker, shapes)
- Image import (drag-and-drop photos, screenshots)
- Emoji picker (quick visual markers)

#### ✅ Real-Time Collaboration

- **Multi-user cursors** (see teammates' positions live)
- Presence indicators (who's viewing the board)
- Live edits (changes sync instantly)
- User color-coding (each person has a unique color)
- Follow mode (follow a teammate's viewport)
- Comments and reactions (@ mentions, emojis)

#### ✅ Organization & Structure

- Frames (group related content, name sections)
- Layers (organize content in stacks)
- Search across all boards (find text, tags, notes)
- Tags system (categorize notes and ideas)
- Board templates (meeting notes, project planning, design sprint)
- Favorites/bookmarks (quick access to sections)

#### ✅ Project Management

- Save/load boards (.board format)
- Auto-save (every 60 seconds)
- **Cloud sync integration** (save to Boojy Cloud)
- Export options (PDF, PNG, Markdown for notes)
- Share boards (generate view-only or edit links)
- Version history (restore previous saves)

### What's NOT in Preview

❌ Video/audio embedding
❌ Advanced diagramming (UML, database schemas)
❌ Presentation mode
❌ API integrations (Slack, Google Drive, etc.)
❌ Mobile apps (iOS/Android)
❌ Offline collaboration (only online real-time)

### Success Criteria

- Tester can take meeting notes on infinite canvas
- Handwriting feels natural with stylus/pen input
- Tester can brainstorm visually with sticky notes and mind maps
- Real-time collaboration works smoothly (2-4 people editing simultaneously)
- Cloud sync preserves all content without data loss
- Export to PDF produces clean, usable document
- UI is intuitive ("figured it out without instructions")

---

## 7. Boojy Cloud Preview

### Overview

Creative-aware cloud storage and sync platform that connects all Boojy apps. Unlike generic storage (Google Drive, Dropbox), Boojy Cloud understands creative projects and enables seamless workflows across apps.

### Feature List

#### ✅ Storage & Sync

- **1GB free storage** for all Preview testers
- Real-time sync across devices (Windows, Mac)
- Project versioning (auto-save creates versions)
- Conflict resolution (if same file edited on two devices)
- Offline mode (work without internet, sync when connected)

#### ✅ File Management

- Web dashboard (view all projects from browser)
- Folder organization (organize by project type)
- Search (find projects by name, date, app type)
- Sharing (generate shareable links to projects)
- Trash/restore (recover deleted files for 30 days)

#### ✅ Cross-App Integration

- **Open in...** menu (open Draw file in Design, etc.)
- Asset library (shared colors, brushes across apps)
- Project linking (Audio project can reference Draw artwork)
- Version history per app (see previous saves, restore any version)

#### ✅ Creative-Aware Features

- **Smart previews** (thumbnails show actual artwork, not generic icons)
- **Project metadata** (tracks which app created it, when, canvas size, etc.)
- **Auto-tagging** (Music, Art, Design categories)
- **Activity feed** ("You edited Song Draft v3 on MacBook")

#### ✅ Account & Security

- Email sign-up (no social login required for privacy)
- Password reset via email
- Two-factor authentication (optional)
- End-to-end encryption (files encrypted at rest)
- Privacy-first (no scanning files for ads or data mining)

### What's NOT in Preview

❌ Real-time collaboration (multiple people editing same file)  
❌ Comments/annotations on projects  
❌ Third-party integrations (Google Drive, Dropbox, OneDrive)  
❌ Mobile apps (iOS/Android)  
❌ Paid tiers (Plus/Pro/Max — everyone gets 1GB free)

### Success Criteria

- Tester can save Audio project to Cloud, open on different computer, continues working
- Draw file syncs with all layers intact (no corruption)
- Design file syncs with vectors preserved
- Version history allows reverting to previous save
- Sync feels invisible ("it just works, I don't think about it")
- Web dashboard is easy to navigate

### Technical Notes

- **Backend:** Firebase (Authentication, Firestore, Cloud Storage)
- **File format:** Projects stored as-is (.audio, .draw, .design)
- **Compression:** Files compressed during upload (reduce bandwidth)
- **Bandwidth:** No throttling for Preview (test real-world performance)

---

## 8. Testing Protocol

### Tester Recruitment (10-20 people total)

**Ideal tester profiles:**

- Musicians/podcasters (for Audio)
- Digital artists/illustrators (for Draw)
- Photographers/graphic designers (for Design)
- Note-takers/project managers/team collaborators (for Board)
- People who work across multiple devices (for Cloud)
- Mix of experience levels (beginners to intermediate)
- Access to Windows or Mac computer (bonus: multiple devices)
- Willing to spend 30-60 minutes testing

**Recruitment channels:**

- Friends and family (5-8 people)
- Reddit: r/WeAreTheMusicMakers, r/DigitalPainting, r/graphic_design
- Discord: Creative software communities
- Twitter/X: "Building free creative tools, need testers"

### Testing Phases

#### Phase 1: Individual App Quick Tests (Weeks 2, 4, 6, 8)

**Per app: 2-3 people, in-person observation**

**Method:**

1. Hand tester the app (laptop/tablet) with minimal instruction
2. Task: "Try to [record a song / draw something / edit this photo / save to Cloud]"
3. **Observe silently for 5-10 minutes** (don't help unless truly stuck)
4. Take detailed notes (see template below)
5. After 10 minutes: Debrief (what worked, what confused them)

**Goal:** Catch major UX issues early before holistic testing

#### Phase 2: Holistic Testing (Weeks 9-10)

**Full tester group: 10-20 people**

**Scenario-based tasks:**

**Task 1: "Create a Song with Album Art (Multi-Device)"**

1. Record a 30-second melody in Boojy Audio Preview on Computer A
2. Save to Boojy Cloud
3. Open on Computer B (or same computer, different session)
4. Add reverb via plugin, save to Cloud again
5. Draw cover art in Boojy Draw Preview
6. Save art to Cloud
7. Open Boojy Design Preview, import both Audio waveform reference and Draw artwork
8. Create album cover mockup

**Task 2: "Cross-Device Workflow"**

- Start Draw project on desktop, save to Cloud
- Open Cloud web dashboard, verify file appears
- Download and open on different device
- Make edits, save to Cloud
- Verify version history shows both saves

**Task 3: "Quick Creative Sampler"**

- Audio: Record vocals, add EQ and compression, save to Cloud
- Draw: Sketch a simple character (5 minutes), save to Cloud
- Design: Edit a photo (crop, adjust colors, add text), save to Cloud
- Cloud: View all three projects in web dashboard

**Goal:** Test cross-app workflows, cloud sync reliability, and overall "suite" experience

### Feedback Collection Methods

#### 1. In-Person Observation (Priority Method)

**For 5-10 key testers:**

**Observation Note Template:**

```
TESTER: [Name] | APP: Boojy [Audio/Draw/Design/Cloud] Preview | DATE: [Date]

TIMELINE (What they did):
- 0:00 - Opened app, first impression: ...
- 0:30 - Clicked on [button/tool], expected: ...
- 2:00 - Got confused when: ...
- 5:00 - Successfully completed: ...
- 10:00 - Overall feeling: ...

QUOTES (Exact words):
- "I expected this button to..."
- "This feels really smooth"
- "Where's the [feature]?"

BODY LANGUAGE:
- Smiled/excited when: ...
- Frowned/paused when: ...
- Looked confident / hesitant

FEATURE REQUESTS:
1. ...
2. ...

BUGS ENCOUNTERED:
- ...

OVERALL IMPRESSION: ⭐⭐⭐⭐⭐ (1-5 stars)
WOULD THEY USE IT? ☐ Yes ☐ No ☐ Maybe
WOULD THEY SWITCH FROM [Current Software]? ☐ Yes ☐ No ☐ Maybe
```

#### 2. Google Form (All Testers)

**Structured feedback form:**

```
BOOJY SUITE PREVIEW FEEDBACK

Which apps/services did you test?
☐ Audio ☐ Draw ☐ Design ☐ Cloud

FOR EACH APP YOU TESTED:

What did you try to create?
[Text field]

What worked well?
[Text field]

What was confusing or frustrating?
[Text field]

What feature do you wish existed?
[Text field]

Rate your experience (1-5 stars):
⭐⭐⭐⭐⭐

Would you use this over [your current software]?
☐ Yes ☐ No ☐ Maybe - because: [Text field]

FOR BOOJY CLOUD:

Did sync work reliably?
☐ Yes, flawless ☐ Mostly ☐ Had issues - describe: [Text field]

Did you test multi-device sync?
☐ Yes ☐ No
If yes, describe experience: [Text field]

Would you pay £2/month for 10GB storage?
☐ Yes ☐ No ☐ Maybe

OVERALL:

Which app excited you most? Why?
[Text field]

Would you recommend Boojy Suite to a friend?
☐ Yes ☐ No ☐ Maybe

Would you donate to support development?
☐ Yes ☐ No ☐ Maybe - if: [Text field]

OPTIONAL:
Email (for beta updates): [Text field]
Twitter/Discord (stay involved): [Text field]
```

#### 3. GitHub Issues (Technical Users)

- Dedicated repo: `boojy-suite-preview`
- Issue templates: Bug Report, Feature Request, General Feedback
- Encourages community early (testers become contributors)

#### 4. Follow-Up Conversations

- After initial testing, reach out to 5-10 most engaged testers
- 15-minute video calls or voice messages
- Deep dive: "Tell me more about when you got frustrated..."

---

## 9. Success Criteria

### Quantitative Thresholds

✅ **70%+ of testers say:** "I would use this" or "I would switch from [current software]"
✅ **4+ stars average** across all five components (on 5-star scale)
✅ **Zero critical bugs** (app crashes, data loss, file corruption, sync failures)
✅ **80%+ task completion** (testers accomplish goals without asking for help)  
✅ **Cloud sync success rate: 95%+** (files sync without corruption or loss)

### Qualitative Signals

✅ **"It just works"** – Testers accomplish goals intuitively  
✅ **Enjoyment** – Testers smile, seem engaged (not just tolerating the experience)  
✅ **Feature clarity** – Multiple testers request the same features (tells you v1.0 priorities)  
✅ **Cloud invisibility** – Testers don't think about sync, it "just happens"  
✅ **Competitive advantage** – Testers say things like:

- "This is easier than [Audacity/Krita/Photoshop]"
- "I'd switch if it had [specific feature]"
- "The UI makes way more sense"
- "Cloud sync is smoother than Dropbox"

### Red Flags (Pivot Indicators)

🚨 **50%+ say "I wouldn't use this"** → Core concept problem, need redesign  
🚨 **2-3 stars average** → UI or feature set fundamentally wrong  
🚨 **Multiple critical bugs** → Need more development time before wider testing  
🚨 **Everyone requests same missing feature** → That feature is mandatory for v1.0  
🚨 **Cloud sync failures >10%** → Infrastructure not ready, need to fix before proceeding

---

## 10. Week-by-Week Timeline

### Week 1-2: Boojy Audio Preview Development

- Build recording engine (mic input, waveform display)
- Implement 4+ track system with mixing
- Integrate VST plugin support
- Add basic MIDI recording and piano roll
- **Add Cloud save/load integration**
- Internal testing (you + 1-2 close friends)
- **Deliverable:** Working Audio Preview app with Cloud sync

### Week 3-4: Boojy Draw Preview Development

- Build canvas system (zoom, pan, rotate)
- Implement 5 core brushes with pressure sensitivity
- Create layer system (unlimited layers, blend modes)
- Add selection tools (rectangle, lasso, magic wand)
- **Add Cloud save/load integration**
- Internal testing (you + 1-2 artist friends)
- **Deliverable:** Working Draw Preview app with Cloud sync

### Week 5-6: Boojy Design Preview Development

- Build photo editing tools (crop, color adjustments)
- Implement layer system (shared codebase with Draw)
- Add vector tools (shapes, pen tool, text)
- Create export system (multiple formats)
- **Add Cloud save/load integration**
- Internal testing (you + 1-2 designer friends)
- **Deliverable:** Working Design Preview app with Cloud sync

### Week 7-8: Boojy Cloud Preview + Website Development

#### **Week 7: Website Foundation + Cloud Backend**

**Website Setup (Days 1-2):**

- Initialize React + Vite project
- Set up Tailwind CSS for styling
- Configure domain (boojy.org)
- Set up Netlify hosting (continuous deployment from GitHub)
- Build reusable components:
    - Header component (navigation, logo)
    - Footer component (links, copyright)
    - Button components (primary, secondary, download)
    - Card components (project cards, info cards)
- Build landing page (boojy.org):
    - Hero section (tagline, brief description)
    - Preview phase explanation
    - Brief overview of apps (Audio, Draw, Design, Cloud)
    - Links to social media (YouTube, X, GitHub)
    - Call-to-action: "Preview launching soon"

**Cloud Backend Setup (Days 3-4):**

- Firebase Authentication setup (email/password)
- Firestore database schema:
    - Users collection (profile, storage quota, created_at)
    - Projects collection (file metadata, owner, app_type, last_modified)
    - Versions collection (version history per project)
- Firebase Storage setup:
    - Organize by user_id → project_id → files
    - Security rules (users only access their own files)
- Cloud Functions for:
    - File upload processing (compression, metadata extraction)
    - Storage quota checking
    - Conflict resolution logic

**Tech Stack:**

- **Frontend:** React + Vite (fast hot reload, modern tooling)
- **Styling:** Tailwind CSS (utility-first, mobile-responsive)
- **State Management:** React hooks + Context API
- **Auth Library:** react-firebase-hooks (simple Firebase integration)
- **Backend:** Firebase (Auth, Firestore, Storage, Functions)
- **Hosting:** Netlify (auto-deploy from GitHub, free SSL)
- **Domain:** boojy.org

**Deliverable:** Landing page live at boojy.org, Cloud backend infrastructure ready

---

#### **Week 8: Authentication + Cloud Dashboard**

**Authentication Flow (Days 1-2):**

- Sign up page (boojy.org/auth/signup):
    - Email + password form
    - Form validation (email format, password strength)
    - Firebase Auth integration
    - Auto-create Firestore user profile (1GB quota)
    - Welcome email (optional)
- Sign in page (boojy.org/auth/signin):
    - Email + password login
    - "Remember me" checkbox
    - Link to password reset
- Password reset flow:
    - Email-based reset link
    - New password form
- Auth state management:
    - useAuth hook (wraps react-firebase-hooks)
    - Protected routes (redirect to signin if not authenticated)
    - Persist auth state across sessions

**Cloud Web Dashboard (Days 3-4):**

- Project browser (boojy.org/dashboard):
    - Grid/list view of all user projects
    - ProjectCard component shows:
        - Thumbnail/preview (if available)
        - Project name
        - App type icon (Audio/Draw/Design)
        - File size
        - Last edited timestamp
    - Filter by app type (Audio, Draw, Design)
    - Search projects by name
    - Sort options (name, date, size)
- Storage meter component:
    - Visual progress bar (used / total)
    - "47 MB / 1 GB" text display
    - Warning when approaching limit (>80%)
- Version history viewer:
    - Click project → view version history
    - List of saves with timestamps
    - "Restore" button to revert to previous version
    - Compare versions (future feature, not in Preview)
- Project actions:
    - Download project file
    - Delete project (with confirmation modal)
    - Share project (generate public link - basic implementation)
    - Rename project
- Settings page (boojy.org/settings):
    - View/edit email
    - Change password
    - Storage usage breakdown
    - Account deletion (with confirmation)

**Preview Downloads Page (Day 5):**

- Create boojy.org/preview:
    - Preview phase explanation
    - Download section:
        - Boojy Audio Preview (Windows .exe, macOS .dmg)
        - Boojy Draw Preview (Windows .exe, macOS .dmg)
        - Boojy Design Preview (Windows .exe, macOS .dmg)
    - Boojy Cloud section:
        - [Create Account] button → /auth/signup
        - [Sign In] button → /auth/signin
    - Resources section:
        - Link to GitHub (design documents)
        - Link to GitHub Issues (bug reports)
        - Link to feedback form (Google Form)
    - Help section:
        - Email contact
        - Link to GitHub Discussions
- Responsive design (mobile, tablet, desktop)
- Download tracking (optional analytics)

**Integration Testing (Day 5 continued):**

- Test full workflow:
    1. User visits boojy.org/preview
    2. Creates Cloud account
    3. Downloads Audio Preview app
    4. Launches app, signs in with Cloud credentials
    5. Creates project, saves to Cloud
    6. Opens boojy.org/dashboard, sees project appear
    7. Opens project on different device, continues working
- Test edge cases:
    - Offline mode (app works, syncs when online)
    - Large file uploads (>50MB)
    - Simultaneous edits on two devices (conflict resolution)
    - Password reset flow
    - Storage quota exceeded

**Deployment:**

- Push to GitHub (boojyorg/boojy-website repository)
- Netlify auto-deploys on push to main branch
- Custom domain configured (boojy.org)
- SSL certificate auto-provisioned by Netlify
- Test production build on multiple browsers/devices

**Deliverable:**

- Complete website with landing page, preview downloads, and Cloud dashboard
- Full authentication system integrated with Firebase
- Cloud web dashboard for viewing/managing projects
- All hosted at boojy.org with HTTPS
- Ready for Preview testers (Week 11-12)

### Week 9-10: Boojy Board Preview Development

- Build infinite canvas system (pan, zoom, navigation)
- Implement note-taking tools (text, handwriting, highlighting)
- Create sticky notes and cards system
- Add visual brainstorming tools (mind maps, flowcharts, diagrams)
- **Implement real-time collaboration** (multi-user cursors, live sync)
- Add organization features (frames, layers, search, tags)
- **Add Cloud save/load integration**
- Internal testing (you + 1-2 collaborator friends)
- **Deliverable:** Working Board Preview app with collaboration and Cloud sync

### Week 11-12: Holistic Testing Phase

- Recruit 10-20 testers (mix of musicians, artists, designers)
- **Testers access everything via boojy.org/preview:**
    - Download apps (Windows + Mac builds)
    - Create Boojy Cloud accounts (1GB free)
    - Access web dashboard to view/manage projects
- Conduct in-person observations (5-10 key testers)
- Test multi-device workflows (testers with 2+ computers)
- Test website usability:
    - Sign-up flow (easy to create account?)
    - Dashboard navigation (can find projects?)
    - Download process (clear instructions?)
    - Mobile responsiveness (works on phones/tablets?)
- Send Google Form to all testers
- Monitor GitHub Issues for bug reports
- Track Cloud sync success rate (monitor backend logs)
- Monitor website analytics (page views, sign-ups, downloads)
- **Deliverable:** 50+ feedback responses, observation notes, sync reliability data, website usage metrics

### Week 13: Feedback Analysis

- Compile all feedback (forms, notes, GitHub issues)
- Categorize by theme (feature requests, bugs, UX confusion, sync issues)
- Count frequency (how many people mentioned each issue)
- Identify patterns (what are the top 5 requests per app?)
- Analyze Cloud sync failures (what caused them?)
- Create priority matrix (must-have vs nice-to-have for v1.0)
- **Deliverable:** Analysis document with clear priorities

### Week 14: Roadmap Adjustment

- Update v1.0 feature lists based on Preview feedback
- Adjust timeline estimates (now that you know development velocity)
- Decide on Cloud infrastructure (Firebase long-term, or migrate to Supabase?)
- Write success summary ("20 testers, 85% would use it, 98% sync success, top requests: X, Y, Z")
- Plan next steps (begin v1.0 development or iterate on Preview)
- Publish results to early community (GitHub, social media)
- **Deliverable:** Refined v1.0 roadmap, ready to proceed

---

## 11. What Happens After Preview

### If Preview is Successful (hits success criteria):

**Month 3 onwards: Full v1.0 Development**

- **Boojy Audio v1.0** (Months 3-5)
    
    - Add top-requested features from Preview feedback
    - Expand track count, add automation, refine MIDI
    - Polish UI, fix all Preview bugs
    - Beta release (wider testing, 100+ users)
- **Boojy Draw v1.0** (Months 6-8)
    
    - Add custom brush creator (if highly requested)
    - Advanced filters (blur, sharpen)
    - Layer masks
    - Text tool
    - Beta release
- **Boojy Cloud v1.0** (Month 9-10)
    
    - Paid storage tiers launch (Plus £2/10GB, Pro £5/100GB, Max £15/1TB)
    - Third-party integration (optional Google Drive/Dropbox sync)
    - Mobile apps (iOS/Android) for file browsing
    - Real-time collaboration (future feature, not v1.0)
- **Boojy Design v1.0** (Months 11-13)

    - Advanced photo editing (curves, levels, healing brush)
    - Layer masks
    - Advanced filters
    - Vector refinements
    - Beta release
- **Boojy Board v1.0** (Months 14-16)

    - Advanced collaboration features (if highly requested)
    - Presentation mode
    - Advanced diagramming tools
    - API integrations (optional)
    - Mobile app development begins (iOS/Android)
    - Beta release

**Public Launch:** Month 12-15 (website, YouTube devlogs, social media)

### If Preview Needs Work (doesn't hit criteria):

**Option 1: One-Month Iteration**

- Fix top 3 pain points identified in feedback
- Address critical Cloud sync issues
- Re-test with same testers or new group
- Achieve success criteria before proceeding

**Option 2: Pivot**

- If fundamental concept is flawed, reassess
- Maybe one app resonates (focus there first)
- Cloud might need different approach (investigate infrastructure issues)
- Adjust vision based on real-world learnings

### Either Way: Publish Full Design Document (Month 3)

After Preview phase (success or pivot), write the **Complete Boojy Suite Design Document** incorporating:

- Preview results and learnings
- Updated v1.0 feature priorities
- Realistic timeline based on actual dev velocity
- Cloud sync reliability data
- Testimonials from testers
- Refined business model

---

## 12. Technical Notes

### Platform

- **Desktop:** Windows 10/11, macOS 12+ (Intel & Apple Silicon)
- **Framework:** Flutter (shared codebase, native performance)
- **Backend:** Firebase
    - Authentication (email/password)
    - Firestore (project metadata, user accounts)
    - Cloud Storage (file hosting)
    - Cloud Functions (backend logic, conflict resolution)

### Website Tech Stack

- **Frontend Framework:** React 18 + Vite (fast development, hot reload)
- **Styling:** Tailwind CSS (utility-first, mobile-responsive)
- **State Management:** React hooks (useState, useEffect, useContext)
- **Auth Integration:** react-firebase-hooks (Firebase Auth wrapper)
- **Routing:** React Router v6 (client-side routing)
- **Hosting:** Netlify
    - Continuous deployment from GitHub
    - Automatic HTTPS (SSL certificate)
    - Custom domain (boojy.org)
    - CDN for fast global access
- **Build Tool:** Vite (modern, fast bundler)
- **Version Control:** GitHub (boojyorg/boojy-website)

### File Formats

- **Audio:** .audio (project), .wav/.mp3/.flac (export)
- **Draw:** .draw (project), .png/.jpg/.tiff (export)
- **Design:** .design (project), .png/.jpg/.svg/.pdf (export)

### Cloud Sync Implementation

- **Strategy:** Optimistic sync (local changes happen immediately, sync in background)
- **Conflict resolution:** Last-write-wins (with version history for rollback)
- **Compression:** Files compressed during upload (gzip)
- **Chunking:** Large files split into chunks (resume interrupted uploads)
- **Offline mode:** Changes queued locally, sync when connection restored

### Distribution

- Direct download (no app store initially)
- Installer packages (.exe for Windows, .dmg for Mac)
- Website: boojy.org/preview (hosted on Netlify)
- GitHub Releases page (testers download from there)
- Cloud accounts created via web dashboard (boojy.org/auth/signup)

### System Requirements (Minimum)

- **OS:** Windows 10 or macOS 12+
- **RAM:** 4GB (8GB recommended)
- **Storage:** 500MB per app + cloud storage (1GB free)
- **Display:** 1280×720 minimum
- **Internet:** Required for Cloud sync (apps work offline, sync when connected)

---

## 13. Boojy Cloud Infrastructure Considerations

### Preview Phase (Firebase)

**Why Firebase for Preview:**

- ✅ Fast to implement (built-in auth, storage, database)
- ✅ Reliable (Google infrastructure)
- ✅ Free tier supports 20-50 testers
- ✅ Easy to monitor (Firebase Console shows usage, errors)

**Preview Limitations:**

- ⚠️ Costs scale up quickly after free tier
- ⚠️ Vendor lock-in (harder to migrate later)
- ⚠️ Limited control over infrastructure

### Post-Preview Decision (Month 3)

**Option A: Stay on Firebase**

- If Preview shows low storage usage per user
- If ease of development outweighs cost concerns
- Simplest path forward

**Option B: Migrate to Self-Hosted (Supabase + Backblaze B2)**

- If Preview shows high storage needs (users save many large files)
- **Cost comparison:**
    - Firebase: $0.18/GB storage + $0.12/GB bandwidth
    - Backblaze B2: $0.005/GB storage + $0.01/GB bandwidth (36x cheaper!)
- More control, better long-term economics
- Requires migration work (2-4 weeks)

**Recommendation:** Start Firebase for Preview, evaluate costs after testing, migrate to Supabase/B2 if needed before public launch.

---

## Appendix A: Tester Onboarding Message

```
Subject: Welcome to Boojy Suite Preview Testing!

Hi [Name],

Thank you for joining the Boojy Suite Preview phase! You're helping shape the future of free, open-source creative software.

WHAT YOU'RE TESTING:
- Boojy Audio Preview (record, mix, plugins, MIDI)
- Boojy Draw Preview (digital painting, layers, pressure sensitivity)
- Boojy Design Preview (photo editing, vector design)
- Boojy Board Preview (note-taking, brainstorming, real-time collaboration)
- Boojy Cloud Preview (sync projects across devices)

GET STARTED:
1. Visit: boojy.org/preview
2. Create your Boojy Cloud account (1GB free storage)
3. Download the apps for Windows or Mac
4. Sign in to the apps with your Cloud credentials
5. Start creating!

YOUR MISSION:
Try to create something real:
- Audio: Record a short song or podcast → save to Cloud
- Draw: Sketch or paint something you'd be proud of → save to Cloud
- Design: Edit a photo or design a simple poster → save to Cloud
- Board: Take notes or brainstorm ideas on infinite canvas → save to Cloud
- Cloud: Open your projects from the web dashboard at boojy.org/dashboard

BONUS CHALLENGE:
Try this multi-device workflow:
1. Record music in Audio on Computer A, save to Cloud
2. Log in to boojy.org/dashboard, verify file appears
3. Draw album art in Draw, save to Cloud
4. Open Design, import both, create album cover mockup

FEEDBACK:
After testing, fill out this form: [Google Form link]
Found a bug? Report it: [GitHub Issues link]
Questions? Join the discussion: [GitHub Discussions link]

HELP & SUPPORT:
- Website: boojy.org
- Email: [your email]
- GitHub: github.com/boojyorg

Thanks for being part of this!

– Tyr / Boojy Development
```

---

## Appendix B: Cloud Sync Test Scenarios

### Test Case 1: Basic Sync

1. Create Audio project on Computer A
2. Save to Cloud
3. Open Cloud web dashboard, verify file appears with correct preview
4. Log in on Computer B
5. Open same project, verify it loads correctly
6. Make edit, save to Cloud
7. Return to Computer A, open project, verify edit appears

**Expected:** Seamless sync, no data loss, correct version loaded

---

### Test Case 2: Conflict Resolution

1. Create Draw project, save to Cloud
2. Turn off internet on Computer A
3. Make edits (add layer), save locally
4. On Computer B, open same project, make different edits (change color)
5. Save on Computer B to Cloud
6. Turn internet back on for Computer A
7. Trigger sync

**Expected:** Conflict detected, user chooses which version to keep (or keep both as separate versions)

---

### Test Case 3: Large File Sync

1. Create Design project with high-res images (50MB+ project size)
2. Save to Cloud
3. Monitor upload progress
4. On different device, download project
5. Verify all layers and images intact

**Expected:** Progress indicator shows upload/download, large files sync without corruption

---

### Test Case 4: Offline Mode

1. Create Draw project while offline
2. Make edits, save (goes to local queue)
3. Turn on internet
4. Verify automatic sync to Cloud
5. Check Cloud web dashboard for file

**Expected:** Offline changes sync automatically when connection restored

---

### Test Case 5: Version History

1. Create Audio project, save to Cloud (Version 1)
2. Make major edit, save (Version 2)
3. Make another edit, save (Version 3)
4. Open Cloud web dashboard, view version history
5. Restore to Version 2
6. Verify Audio project reverts correctly

**Expected:** All versions listed with timestamps, restore works without data loss

---

**End of Early Preview Design Document**
