# Professional Presentation System

This project is centered on `presentation.html`, a standalone HTML presentation controller.

`presentation.html` loads slide files (for example, `slide1.html`, `slide2.html`, ...) in iframes and provides navigation, overview mode, fullscreen support, responsive scaling, and a small JavaScript API.

## Scope

- Main runtime: `presentation.html`
- Slide content: user-provided `slideN.html` files
- Backend/build tools: not required

## Current Defaults in `presentation.html`

```js
const TOTAL_SLIDES  = 6;
const ALLOW_UPSCALE = true;
```

These are just defaults. Update them to match your deck.

## Features

- Lazy/eager slide loading
- Adjacent-slide preloading
- Overview grid mode with click-to-jump
- Keyboard, mouse wheel, touch swipe navigation
- Fullscreen toggle
- Progress bar and slide counter
- Responsive scaling with optional upscaling

## Quick Start

1. Put `presentation.html` and your `slideN.html` files in the same folder.
2. Set `TOTAL_SLIDES` to match your actual slide count.
3. Open `presentation.html` in a browser.

## Keyboard Shortcuts

- Next: `ArrowRight`, `ArrowDown`, `Space`, `PageDown`
- Previous: `ArrowLeft`, `ArrowUp`, `PageUp`
- First/Last: `Home` / `End`
- Jump: `1` to `9` (normal mode)
- Toggle overview: `O` or `Esc`
- Toggle fullscreen: `F`
- Toggle UI visibility: `H`

Overview mode also supports numeric jump keys (`0` to `9`) and thumbnail click navigation.

## API (`window.presentation`)

- `goToSlide(slideNum)`
- `nextSlide()`
- `prevSlide()`
- `firstSlide()`
- `lastSlide()`
- `toggleOverviewMode()`
- `toggleFullscreen()`
- `getCurrentSlide()`
- `getTotalSlides()`
- `getConfig()`
- `getState()`

## Documentation

- `QUICK_START.md` for setup in a few minutes
- `USER_GUIDE.md` for full configuration, behavior, and troubleshooting
