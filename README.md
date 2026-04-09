# AI-Based Aerodynamic Coefficient Presentation System

This repository contains a browser-based presentation controller (`presentation.html`) and a 6-slide deck (`slide1.html` to `slide6.html`) for the topic **"AI-Based Aerodynamic Coefficient Prediction for Multirotor Drones"**.

The system is dependency-light (pure HTML/CSS/JS runtime), with optional CDN assets for icons, fonts, and Tailwind used by individual slides.

## Current Project Snapshot

- Total slides configured: `6` (`TOTAL_SLIDES` in `presentation.html`)
- Upscaling on large displays: enabled (`ALLOW_UPSCALE = true`)
- Slide format: standalone HTML files loaded as iframes
- Controller features: lazy loading, overview grid mode, keyboard/mouse/touch navigation, fullscreen toggle, progress/counter UI, JavaScript API

## Repository Structure

```text
presentation.html   # Main presentation controller
slide1.html         # Deck slide 1 (title)
slide2.html         # Deck slide 2 (agenda)
slide3.html         # Deck slide 3
slide4.html         # Deck slide 4
slide5.html         # Deck slide 5
slide6.html         # Deck slide 6
README.md
QUICK_START.md
USER_GUIDE.md
```

## Run

1. Keep all files in one directory.
2. Open `presentation.html` in a modern browser.
3. Navigate with keyboard, mouse wheel, touch swipe, or on-screen buttons.

No build step or backend is required.

## Keyboard Shortcuts

- Next slide: `ArrowRight`, `ArrowDown`, `Space`, `PageDown`
- Previous slide: `ArrowLeft`, `ArrowUp`, `PageUp`
- First slide: `Home`
- Last slide: `End`
- Jump to slide: `1` to `9` (normal mode)
- Toggle overview: `O` or `Esc`
- Toggle fullscreen: `F`
- Toggle UI visibility: `H`

In overview mode, `0` jumps to slide 10 (if present), and `1` to `9` jump directly.

## Quick Configuration

At the top of `presentation.html`:

```js
const TOTAL_SLIDES  = 6;
const ALLOW_UPSCALE = true;
```

- Increase `TOTAL_SLIDES` when adding more `slideN.html` files.
- Set `ALLOW_UPSCALE` to `false` to avoid scaling above 100%.

Advanced options are in the `CONFIG` object inside `presentation.html`.

## JavaScript API

Available at `window.presentation` after load:

- `goToSlide(slideNum)`
- `nextSlide()` / `prevSlide()`
- `firstSlide()` / `lastSlide()`
- `toggleOverviewMode()`
- `toggleFullscreen()`
- `getCurrentSlide()`
- `getTotalSlides()`
- `getConfig()`
- `getState()`

## Known Caveats (Current Code)

- `showHintOnStart` and `hintDisplayTime` are legacy config fields and currently do not change runtime behavior.
- `H` toggles the visibility of all controller UI (not only the hint panel).
- `enableProgressBar`, `enableSlideCounter`, and `enableNavigationButtons` currently gate updates/listeners, but do not fully remove the corresponding DOM elements.
- `showLoadingScreen` should remain `true` unless you also adjust loading screen markup/logic.

## Documentation

- `QUICK_START.md`: setup and first run
- `USER_GUIDE.md`: full behavior, configuration, API, and troubleshooting
