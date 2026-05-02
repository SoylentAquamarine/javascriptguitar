# System Overview — Javascript Guitar

## Purpose

A guitar fretboard visualizer originally built in the late 1990s using JavaScript image-swapping. The project has two goals: preserve an authentic piece of late-1990s web development history, and provide a modernized version with equivalent functionality built using current web standards. Both versions coexist in the same repository and are served from the same GitHub Pages site.

> **Historical note**: This project captures the creative problem-solving of the pre-jQuery, pre-framework era — when interactive web UI meant preloading GIF arrays and swapping image `src` attributes on click. The original code runs unmodified in modern browsers.

## Tech Stack

- **Frontend**: 100% static HTML + Vanilla JavaScript
- **Media**: GIF images for fretboard note/chord visualizations
- **Dependencies**: None (zero external libraries)
- **Build system**: None
- **Hosting**: GitHub Pages, served from repository root
- **License**: GPL v3

## Repository Structure

```
/
├── index.html                  # Landing page — links to both versions
│
├── original/                   # Preserved 1990s implementation (unmodified)
│   ├── index.html              # Note Builder
│   ├── barrechords.html        # Barre Chord Builder
│   ├── chordsminmaj.html       # Misc Chords
│   ├── scales.html             # Scales
│   ├── a_chordsbig.html        # Variations on A and D
│   ├── b_chords.html           # Misc Chords 2
│   └── a_chords.html           # A Chords Vertical
│
└── optimized/                  # AI-modernized version (Claude + OpenAI)
    ├── index.html              # Modern entry point
    ├── images/                 # GIF assets (large set)
    │   ├── note1.gif, note2.gif ...    # Standard note GIFs
    │   ├── a_note1.gif, a_note2.gif ... # Alternate note GIFs
    │   ├── awt.gif, awt1.gif            # Chord diagram assets
    │   └── [many more encoding fret/string/position]
    └── Guitar - Copy*.html, Guitar.backup*.html  # Working copies / backups
```

## Two Versions

### Original (1990s)

Authentic late-1990s code, preserved exactly as written. Runs in modern browsers without modification.

- **Technique**: Image flipping via `document.images[]` array manipulation
- **Interaction model**: `onmouseover` / `onclick` inline event handlers
- **Architecture**: Pure procedural JavaScript, no functions beyond inline handlers
- **State management**: Direct `document.images[n].src = '...'` mutation
- **Tools**: Note Builder, Barre Chord Builder, Misc Chords, Scales, Variations on A and D, Misc Chords 2, A Chords Vertical

### Optimized (AI-Modernized)

Rebuilt using HTML5 and modern JavaScript while preserving original functionality.

- **Tools**: Combined into a single modernized entry point
- **Attribution**: "Thanks Claude and OpenAI!" (credited in index.html)

## Key Technique (Original Version)

The original relies on the image-flipping pattern that was standard for interactive web UI before CSS and DOM APIs matured:

1. **Preload**: All GIF variants are created as `Image()` objects and loaded into the browser cache on page load.
2. **Swap**: User interaction (hover or click) replaces an `<img>` element's `src` with the preloaded variant.
3. **GIF naming convention**: Filenames encode the note, string, and fret position.
   - Example: `a_note21.gif` → note A, position 2, variant 1
   - Example: `note215.gif` → note at position 2, string 1, fret 5
4. **No server round-trips**: All state lives in preloaded image objects — fully offline-capable once loaded.

## Hosting

- GitHub Pages serves directly from the repository root.
- `index.html` at the root is the entry point.
- No CI/CD pipeline — updates deploy automatically on push to `main`.
- No build step, no minification, no bundling.

## Maintenance

- The `original/` directory should never be modified — preserve the 1990s code exactly.
- The `optimized/` directory is the active development area.
- `index.html` (root) links to both versions and should be updated if new tools are added to either version.
