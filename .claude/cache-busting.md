# Cache Busting Workflow

## Problem
Netlify caches CSS/JS files for 1 year (`max-age=31536000, immutable` in netlify.toml).
This means browsers won't see CSS/JS changes without a hard refresh.

## Solution
Version numbers are added to CSS/JS file references in all HTML files.

## Current Version
All files currently use `?v=1`

## When Making CSS or JavaScript Changes

**IMPORTANT:** After editing `styles.css` or `main.js`, you MUST increment the version number in all HTML files.

### Steps:
1. Make changes to `website/css/styles.css` or `website/js/main.js`
2. Update version number in ALL HTML files:
   - Find: `?v=1`
   - Replace: `?v=2` (or increment to next number)
3. Commit and push

### Files that need version updates:
- `website/index.html`
- `website/devlog.html`
- `website/donate.html`
- `website/roadmap.html`
- `website/feature-request.html`

### Example:
```bash
# After editing CSS
# Find and replace in all HTML files: ?v=1 → ?v=2
git add -A
git commit -m "Update styles and bump cache version to v2"
git push
```

### Alternative versioning schemes:
- Sequential: `?v=1`, `?v=2`, `?v=3`
- Date-based: `?v=20251103`, `?v=20251104`
- Timestamp: `?v=202511022300`

## Why This Works
When the browser sees `styles.css?v=2` it treats it as a completely different file from `styles.css?v=1`, forcing a fresh download.

## Remember
✅ Always increment version after CSS/JS changes
✅ Update ALL HTML files, not just one
❌ Don't commit CSS/JS changes without bumping version
