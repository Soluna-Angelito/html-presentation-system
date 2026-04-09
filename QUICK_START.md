# Quick Start

## 1) Prepare files

Keep `presentation.html` with your slide files:

```text
presentation.html
slide1.html
slide2.html
...
slideN.html
```

## 2) Configure

At the top of `presentation.html`:

```js
const TOTAL_SLIDES  = 6;    // change to your real slide count
const ALLOW_UPSCALE = true; // true: allow scaling above 100% on large displays
```

## 3) Run

Open `presentation.html` in a modern browser.

## 4) Controls

- Next: `ArrowRight` / `Space`
- Previous: `ArrowLeft`
- Overview: `O`
- Fullscreen: `F`
- Hide/show UI: `H`

## 5) Common edits

- Add or remove slides: update `TOTAL_SLIDES`
- Change file naming (for example `page1.html`):

```js
slideFilePrefix: 'page',
slideFileExtension: '.html',
```

See `USER_GUIDE.md` for full config and troubleshooting.
