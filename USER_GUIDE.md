# User Guide

## Overview

`presentation.html` is a self-contained presentation controller.

It creates an iframe per slide and manages:

- slide loading
- navigation state
- overview layout
- fullscreen mode
- UI updates (progress/counter/buttons)
- responsive scaling

## Startup Flow

1. `DOMContentLoaded` fires.
2. Responsive scale is computed (`updateResponsiveScale`).
3. Slide containers + iframes are created (`createSlides`).
4. First `eagerLoadCount` slides load eagerly, the rest lazily.
5. Loading screen hides after eager load threshold is reached.
6. Event listeners are attached.

## Configuration

### User options (top of file)

```js
const TOTAL_SLIDES  = 6;
const ALLOW_UPSCALE = true;
```

- `TOTAL_SLIDES`: total slide file count.
- `ALLOW_UPSCALE`: allows scale > 1.0 on large screens.

### Advanced config (`CONFIG` object)

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

## Navigation Behavior

### Keyboard

- Next: `ArrowRight`, `ArrowDown`, `Space`, `PageDown`
- Previous: `ArrowLeft`, `ArrowUp`, `PageUp`
- First/Last: `Home` / `End`
- Direct jump: `1` to `9`
- Overview toggle: `O` or `Esc`
- Fullscreen toggle: `F`
- UI visibility toggle: `H`

### Mouse

- Wheel navigation (throttled by `wheelThrottle`)
- Overview thumbnail click to jump

### Touch

- Horizontal swipe with 50px threshold

## Overview Mode

When enabled:

- `body.overview-active` class is applied.
- Slides are placed into a grid using overview settings.
- On first entry, lazy iframes are switched to normal loading.
- Clicking any thumbnail navigates to that slide.

When disabled:

- Per-slide overview position variables are removed.
- Single-slide centered view resumes.

## JavaScript API

Exposed as `window.presentation`:

```js
window.presentation.goToSlide(4);
window.presentation.nextSlide();
window.presentation.prevSlide();
window.presentation.firstSlide();
window.presentation.lastSlide();
window.presentation.toggleOverviewMode();
window.presentation.toggleFullscreen();

window.presentation.getCurrentSlide();
window.presentation.getTotalSlides();
window.presentation.getConfig();
window.presentation.getState();
```

## Usage Patterns

### Add more slides

1. Add `slideN.html` files.
2. Increase `TOTAL_SLIDES` accordingly.

### Change naming scheme

```js
slideFilePrefix: 'page',
slideFileExtension: '.html',
```

This resolves to `page1.html`, `page2.html`, etc.

## Known Implementation Notes

- `H` currently toggles visibility of all major UI elements.
- `showHintOnStart` and `hintDisplayTime` are present in config but are not currently used by active logic.
- `enableProgressBar`, `enableSlideCounter`, and `enableNavigationButtons` mainly affect updates/listeners; elements still exist in markup.

## Troubleshooting

### Slides do not appear

- Verify file names and count match `TOTAL_SLIDES`.
- Check browser console for iframe load errors.
- Confirm relative path from `slideFilePrefix` is correct.

### Navigation stops before expected end

- `TOTAL_SLIDES` is lower than actual files.

### Mouse wheel too fast/slow

- Adjust `wheelThrottle`.

### Slide too small on large display

- Set `ALLOW_UPSCALE = true`.

### Leave-page warning appears

- Controlled by `preventAccidentalExit`; triggered after passing slide 1.

## Browser Compatibility

Use current versions of Chrome, Edge, Firefox, or Safari with modern CSS/JS support.
