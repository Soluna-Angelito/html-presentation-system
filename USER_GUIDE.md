# User Guide

## Overview

`presentation.html` is a self-contained presentation controller that loads each slide (`slide1.html`, `slide2.html`, ...) in an iframe and provides navigation, overview mode, and responsive scaling.

Current repository defaults:

- `TOTAL_SLIDES = 6`
- `ALLOW_UPSCALE = true`
- Slide size target: `1920 x 1080`

## How It Works

1. On `DOMContentLoaded`, the controller creates slide containers and iframe elements.
2. The first `eagerLoadCount` slides use eager loading; others start lazy.
3. Once eager slides are loaded, the loading screen is dismissed.
4. Navigation state drives active slide visibility, preload neighbors, progress bar, and counter.
5. Overview mode repositions all slides into a grid and enables click-to-jump.

## Configuration

There are two config layers in `presentation.html`.

### A) User Options (top of file)

```js
const TOTAL_SLIDES  = 6;
const ALLOW_UPSCALE = true;
```

- `TOTAL_SLIDES`: total number of `slideN.html` files.
- `ALLOW_UPSCALE`: when `true`, scaling can exceed 1.0 on large displays.

### B) Advanced `CONFIG` object

```js
const CONFIG = {
  totalSlides: TOTAL_SLIDES,
  slideFilePrefix: 'slide',
  slideFileExtension: '.html',
  slideWidth: 1920,
  slideHeight: 1080,

  eagerLoadCount: 3,
  preloadAdjacent: true,

  overviewCols: 9,
  overviewScale: 0.12,
  overviewGapX: 20,
  overviewGapY: 20,
  overviewPaddingTop: 50,
  overviewPaddingBottom: 50,

  showLoadingScreen: true,
  showHintOnStart: true,
  hintDisplayTime: 5000,
  enableKeyboard: true,
  enableMouse: true,
  enableTouch: true,
  wheelThrottle: 600,

  enableOverviewMode: true,
  enableFullscreen: true,
  enableProgressBar: true,
  enableSlideCounter: true,
  enableNavigationButtons: true,
  preventAccidentalExit: true,
};
```

## Interaction Reference

### Keyboard

- Next: `ArrowRight`, `ArrowDown`, `Space`, `PageDown`
- Previous: `ArrowLeft`, `ArrowUp`, `PageUp`
- First/Last: `Home` / `End`
- Jump: `1` to `9` (normal mode)
- Overview toggle: `O` or `Esc`
- Fullscreen toggle: `F`
- UI visibility toggle: `H`

### Mouse

- Wheel down/up: next/previous slide (throttled by `wheelThrottle`)
- Overview mode: click a thumbnail to jump

### Touch

- Horizontal swipe (>50px threshold) for prev/next slide

## Overview Mode Details

When overview mode is enabled:

- `body.overview-active` is applied.
- Every slide is positioned in a grid using `overviewCols`, scale, and gap settings.
- Lazy iframes are switched to normal loading on first overview entry.
- Slide click handlers are attached for direct navigation.

When overview mode is disabled:

- Positioning variables and click handlers are removed.
- Standard centered single-slide layout is restored.

## JavaScript API

Use `window.presentation`:

```js
window.presentation.goToSlide(4);
window.presentation.nextSlide();
window.presentation.prevSlide();
window.presentation.firstSlide();
window.presentation.lastSlide();
window.presentation.toggleOverviewMode();
window.presentation.toggleFullscreen();

const current = window.presentation.getCurrentSlide();
const total = window.presentation.getTotalSlides();
const config = window.presentation.getConfig();
const state = window.presentation.getState();
```

## Editing and Extending Slides

### Add more slides

1. Create `slide7.html`, `slide8.html`, etc.
2. Increase `TOTAL_SLIDES` to match.
3. Keep slide dimensions at `1920 x 1080` for best fit.

### Change file naming pattern

If you want files like `page1.html`:

```js
slideFilePrefix: 'page',
slideFileExtension: '.html',
```

## Troubleshooting

### Blank slide or missing content

- Confirm each referenced file exists (`slide1.html` ... `slideN.html`).
- Open browser DevTools and check iframe load errors.
- Verify all files are in the same folder, or update `slideFilePrefix` path.

### Wrong number in counter / navigation stops early

- `TOTAL_SLIDES` does not match actual slide files.

### Wheel feels too sensitive or too slow

- Tune `wheelThrottle` (milliseconds).

### Slide looks too small on a large display

- Keep `ALLOW_UPSCALE = true`.

### Accidental close warning appears

- Controlled by `preventAccidentalExit`; warning appears after moving past slide 1.

## Known Caveats

These are current implementation details in this repository state:

- `showHintOnStart` and `hintDisplayTime` are currently not used to control hint behavior.
- `H` toggles all major UI components via `body.ui-hidden`.
- `enableProgressBar`, `enableSlideCounter`, `enableNavigationButtons` do not fully remove elements from DOM; they mainly affect updates/listeners.
- If `showLoadingScreen` is set to `false`, you should also adjust loading-screen logic/markup to avoid overlay issues.

## Browser Support

Test on current versions of:

- Chrome
- Edge
- Firefox
- Safari

Requires modern CSS/JS support (CSS variables, Flexbox/Grid, ES6, Fullscreen API).
