# Quick Start

Use this when you just need to run or edit the presentation quickly.

## 1) Open the project

Keep these files together:

```text
presentation.html
slide1.html
slide2.html
slide3.html
slide4.html
slide5.html
slide6.html
```

## 2) Launch

Open `presentation.html` in your browser.

## 3) Navigate

- Next: `ArrowRight` / `Space`
- Previous: `ArrowLeft`
- Overview grid: `O`
- Fullscreen: `F`
- Hide/show UI: `H`

## 4) Update slide count (when adding slides)

Edit the top of `presentation.html`:

```js
const TOTAL_SLIDES  = 6;    // set this to your real slide count
const ALLOW_UPSCALE = true; // true = allow >100% scale on large displays
```

If you add `slide7.html`, change `TOTAL_SLIDES` to `7`, and so on.

## 5) Typical edit workflow

1. Edit one or more `slideN.html` files.
2. Refresh the browser tab.
3. Press `O` to verify thumbnails in overview mode.
4. Test keyboard navigation from first to last slide.

## 6) Optional advanced config

Inside `presentation.html`, edit `CONFIG` to tune:

- `eagerLoadCount`
- `preloadAdjacent`
- `overviewCols`
- `overviewScale`
- `wheelThrottle`

See `USER_GUIDE.md` for full details and caveats.
