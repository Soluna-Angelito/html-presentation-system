# 📖 Professional Presentation System - Complete User Guide

## 🎯 Table of Contents

1. [Quick Start](#quick-start)
2. [Configuration](#configuration)
3. [Features](#features)
4. [Keyboard Shortcuts](#keyboard-shortcuts)
5. [Customization](#customization)
6. [API Reference](#api-reference)
7. [Troubleshooting](#troubleshooting)
8. [Best Practices](#best-practices)

---

## 🚀 Quick Start

### Prerequisites
- Modern web browser (Chrome, Firefox, Safari, Edge)
- Slide files named `slide1.html`, `slide2.html`, etc.
- All files in the same directory

### Basic Setup
1. Place `presentation.html` in your slide directory
2. Update the configuration (see below)
3. Open `presentation.html` in a web browser
4. Use keyboard shortcuts or buttons to navigate

### File Structure
```
your-presentation/
├── presentation.html      ← Main file
├── slide1.html
├── slide2.html
├── slide3.html
...
└── slide45.html
```

---

## ⚙️ Configuration

There are two levels of configuration in `presentation.html`:

### User Options (top of file, lines 12–15)

The most commonly changed settings are at the very top of the file, clearly marked:

```javascript
const TOTAL_SLIDES  = 45;    // Total number of slide files
const ALLOW_UPSCALE = false; // true → scale up on displays larger than 1920×1080
```

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `TOTAL_SLIDES` | number | `45` | Number of slide files (slide1.html … slideN.html) |
| `ALLOW_UPSCALE` | boolean | `false` | When `true`, slides scale up to fill displays larger than 1920×1080 |

### Advanced Config (inside main script)

For advanced settings, find the `CONFIG` object further down in the `<script>` section:

```javascript
const CONFIG = {
    // ========== SLIDE SETTINGS ==========
    totalSlides: TOTAL_SLIDES,    // (set via User Options above)
    slideFilePrefix: 'slide',      // Prefix for slide files
    slideFileExtension: '.html',   // File extension
    slideWidth: 1920,             // Slide width in pixels
    slideHeight: 1080,            // Slide height in pixels (16:9 ratio)
    
    // ========== LOADING SETTINGS ==========
    eagerLoadCount: 3,            // Load first N slides immediately
    preloadAdjacent: true,        // Preload previous/next slides
    
    // ========== OVERVIEW MODE ==========
    overviewCols: 9,              // Columns in overview grid
    overviewScale: 0.12,          // Thumbnail scale (0.12 = 12%)
    overviewGapX: 20,             // Horizontal gap between thumbnails
    overviewGapY: 20,             // Vertical gap between thumbnails
    overviewPaddingTop: 50,       // Top padding of grid
    overviewPaddingBottom: 50,    // Bottom padding of grid
    
    // ========== UI SETTINGS ==========
    showLoadingScreen: true,      // Show loading screen on start
    showHintOnStart: true,        // Show keyboard hints on start
    hintDisplayTime: 5000,        // How long to show hints (ms)
    enableKeyboard: true,         // Enable keyboard shortcuts
    enableMouse: true,            // Enable mouse wheel navigation
    enableTouch: true,            // Enable touch/swipe gestures
    wheelThrottle: 600,           // Delay between wheel actions (ms)
    
    // ========== FEATURES ==========
    enableOverviewMode: true,     // Enable overview mode (O key)
    enableFullscreen: true,       // Enable fullscreen mode (F key)
    enableProgressBar: true,      // Show progress bar at top
    enableSlideCounter: true,     // Show slide counter
    enableNavigationButtons: true,// Show navigation buttons
    preventAccidentalExit: true,  // Warn before closing page
};
```

### Common Configuration Scenarios

#### For 10 Slides
```javascript
// User Options
const TOTAL_SLIDES = 10;

// CONFIG
overviewCols: 5,        // 2 rows of 5
```

#### For 100 Slides
```javascript
// User Options
const TOTAL_SLIDES = 100;

// CONFIG
eagerLoadCount: 5,      // Load more initially for large decks
overviewCols: 10,       // 10 rows of 10
overviewScale: 0.08,    // Smaller thumbnails
```

#### Different Slide Names (e.g., `page1.html`)
```javascript
slideFilePrefix: 'page',
slideFileExtension: '.html',
```

#### 4:3 Aspect Ratio Slides
```javascript
slideWidth: 1024,
slideHeight: 768,
```

#### Minimal UI (Presentation Mode)
```javascript
showLoadingScreen: false,
showHintOnStart: false,
enableProgressBar: false,
enableSlideCounter: false,
enableNavigationButtons: false,
```

---

## ✨ Features

### 1. Lazy Loading
- **Fast Initial Load**: Only loads first 3 slides immediately
- **Smart Preloading**: Loads adjacent slides for instant navigation
- **Overview Optimization**: Loads all slides when entering overview mode

### 2. Overview Mode
- **Grid Layout**: Shows all slides in a scrollable grid
- **Thumbnail Navigation**: Click any slide to jump to it
- **Visual Indicators**: Current slide highlighted, numbered thumbnails
- **Hover Effects**: Blue glow on hover for easy identification

### 3. Multiple Navigation Methods
- **Keyboard**: Arrow keys, Space, Home, End, number keys
- **Mouse**: Wheel up/down, button clicks
- **Touch**: Swipe left/right on mobile devices
- **Buttons**: On-screen navigation controls

### 4. Responsive Design
- **Dynamic Scaling**: Slides scale dynamically to fit any screen size, zoom level, or DPI setting
- **Optional Upscaling**: Set `ALLOW_UPSCALE = true` to fill displays larger than 1920×1080
- **Mobile Support**: Touch-optimized interface
- **Adaptive UI**: Buttons and counters resize on small screens

### 5. Progress Tracking
- **Progress Bar**: Visual indicator at top of screen
- **Slide Counter**: Shows current/total (e.g., "5 / 45")
- **Loading Progress**: Shows slide loading status

### 6. Modern UI
- **Glassmorphism**: Frosted glass effect on UI elements
- **Smooth Animations**: Hardware-accelerated transforms
- **Visual Feedback**: Button states, hover effects, transitions

---

## ⌨️ Keyboard Shortcuts

### Navigation
| Key | Action |
|-----|--------|
| `→` / `↓` / `Space` / `PgDn` | Next slide |
| `←` / `↑` / `PgUp` | Previous slide |
| `Home` | First slide |
| `End` | Last slide |
| `1`-`9` | Jump to slide 1-9 |

### Modes
| Key | Action |
|-----|--------|
| `O` / `Esc` | Toggle overview mode |
| `F` | Toggle fullscreen |
| `H` | Toggle keyboard hints |

### In Overview Mode
| Key | Action |
|-----|--------|
| `0`-`9` | Jump to slide 1-10 |
| Click | Jump to clicked slide |
| Scroll | Scroll through grid |
| `O` / `Esc` | Exit overview mode |

---

## 🎨 Customization

### Theme Colors

Edit the CSS `:root` section:

```css
:root {
    --primary-color: #667eea;      /* Main theme color */
    --secondary-color: #764ba2;    /* Gradient color */
    --accent-color: #fbbf24;       /* Accent color */
    --background-dark: #0f0f1e;    /* Background */
}
```

### Example: Red Theme
```css
:root {
    --primary-color: #ef4444;
    --secondary-color: #dc2626;
    --accent-color: #fbbf24;
}
```

### UI Transparency

```css
:root {
    --ui-glass-opacity: 0.1;       /* 0.0 = invisible, 1.0 = opaque */
    --ui-blur: 20px;               /* Blur amount */
}
```

### Animation Speed

```css
:root {
    --transition-fast: 0.3s;       /* Fast animations */
    --transition-medium: 0.6s;     /* Medium animations */
    --transition-slow: 0.8s;       /* Slow animations */
}
```

### Custom Fonts

Replace the Google Fonts link in `<head>`:

```html
<link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700&display=swap" rel="stylesheet">
```

Update body font:
```css
body {
    font-family: 'Roboto', sans-serif;
}
```

### Hide Specific UI Elements

```css
/* Hide progress bar */
.progress-bar { display: none; }

/* Hide slide counter */
.slide-counter { display: none; }

/* Hide navigation buttons */
.nav-controls { display: none; }

/* Hide top buttons */
.top-buttons { display: none; }
```

---

## 🔌 API Reference

The presentation system exposes a JavaScript API at `window.presentation`:

### Methods

#### `goToSlide(slideNum)`
Jump to a specific slide.
```javascript
window.presentation.goToSlide(10); // Go to slide 10
```

#### `nextSlide()`
Go to next slide.
```javascript
window.presentation.nextSlide();
```

#### `prevSlide()`
Go to previous slide.
```javascript
window.presentation.prevSlide();
```

#### `firstSlide()`
Go to first slide.
```javascript
window.presentation.firstSlide();
```

#### `lastSlide()`
Go to last slide.
```javascript
window.presentation.lastSlide();
```

#### `toggleOverviewMode()`
Toggle overview mode on/off.
```javascript
window.presentation.toggleOverviewMode();
```

#### `toggleFullscreen()`
Toggle fullscreen mode.
```javascript
window.presentation.toggleFullscreen();
```

#### `getCurrentSlide()`
Get current slide number.
```javascript
const current = window.presentation.getCurrentSlide();
console.log('Current slide:', current); // e.g., 5
```

#### `getTotalSlides()`
Get total number of slides.
```javascript
const total = window.presentation.getTotalSlides();
console.log('Total slides:', total); // e.g., 45
```

#### `getConfig()`
Get current configuration object.
```javascript
const config = window.presentation.getConfig();
console.log(config);
```

#### `getState()`
Get current state object.
```javascript
const state = window.presentation.getState();
console.log('Current slide:', state.currentSlide);
console.log('Overview mode:', state.isOverviewMode);
```

### Example Usage

#### Auto-advance slides every 5 seconds
```javascript
setInterval(() => {
    const current = window.presentation.getCurrentSlide();
    const total = window.presentation.getTotalSlides();
    if (current < total) {
        window.presentation.nextSlide();
    }
}, 5000);
```

#### Jump to slide from URL parameter
```javascript
// URL: presentation.html?slide=10
const urlParams = new URLSearchParams(window.location.search);
const slideNum = parseInt(urlParams.get('slide'));
if (slideNum) {
    window.presentation.goToSlide(slideNum);
}
```

#### Create custom navigation
```javascript
document.getElementById('myCustomBtn').addEventListener('click', () => {
    window.presentation.goToSlide(15);
});
```

---

## 🔧 Troubleshooting

### Problem: Slides don't load

**Symptoms**: White/blank screen, no slides visible

**Solutions**:
1. Check file names match configuration (`slide1.html`, `slide2.html`, etc.)
2. Ensure all files are in same directory
3. Check browser console (F12) for errors
4. Verify `TOTAL_SLIDES` (top of file) matches actual number of files

### Problem: Overview mode is slow

**Symptoms**: Takes 3-7 seconds to show thumbnails

**Solutions**:
1. This is normal for first overview (loading 42+ slides)
2. Second overview should be instant
3. Reduce `TOTAL_SLIDES` if you have fewer slides
4. Check network speed (affects remote slides)

### Problem: Thumbnails don't appear in overview

**Symptoms**: Grid shows empty rectangles

**Solutions**:
1. Wait 3-5 seconds for slides to load
2. Check browser console for 404 errors
3. Verify slide files exist and are accessible
4. Try clicking a thumbnail - if it navigates, slides are loading

### Problem: Keyboard shortcuts don't work

**Symptoms**: Keys don't navigate slides

**Solutions**:
1. Click on presentation area to focus it
2. Check `enableKeyboard: true` in config
3. Verify browser hasn't captured the keys
4. Check browser console for JavaScript errors

### Problem: Slides are cut off or misaligned

**Symptoms**: Slides don't fit screen, shifted to one side, or clipped

**Solutions**:
1. Verify `slideWidth: 1920` and `slideHeight: 1080` in CONFIG match your slides
2. Check slide files have correct dimensions
3. Try refreshing the page (responsive scale recalculates on load)
4. Test in fullscreen mode (`F` key) to rule out browser chrome interference
5. If slides are too small on a large display, set `ALLOW_UPSCALE = true` in User Options

### Problem: Navigation buttons missing

**Symptoms**: No UI controls visible

**Solutions**:
1. Check `enableNavigationButtons: true` in config
2. Verify CSS loaded correctly (check for 404 errors)
3. Check browser zoom level (should be 100%)
4. Inspect element (F12) to see if hidden by CSS

### Problem: Fullscreen doesn't work

**Symptoms**: F key or button doesn't enter fullscreen

**Solutions**:
1. Check `enableFullscreen: true` in config
2. Some browsers require user gesture (try clicking button)
3. Check browser fullscreen permissions
4. Try different browser (Safari has restrictions)

### Problem: Mobile/touch doesn't work

**Symptoms**: Can't swipe to navigate on mobile

**Solutions**:
1. Check `enableTouch: true` in config
2. Ensure swipe threshold is met (50px minimum)
3. Try swiping more deliberately
4. Use on-screen navigation buttons instead

---

## 📚 Best Practices

### File Organization

```
presentation/
├── presentation.html
├── assets/
│   ├── images/
│   ├── videos/
│   └── styles/
├── slides/
│   ├── slide1.html
│   ├── slide2.html
│   └── ...
└── README.md
```

If slides are in subfolder, update config:
```javascript
slideFilePrefix: 'slides/slide',
```

### Performance Optimization

#### For Large Presentations (100+ slides)
```javascript
eagerLoadCount: 5,          // Load more initially
overviewCols: 15,           // More columns
overviewScale: 0.06,        // Smaller thumbnails
preloadAdjacent: false,     // Disable preload to save memory
```

#### For Slow Networks
```javascript
eagerLoadCount: 1,          // Load minimum initially
preloadAdjacent: false,     // Don't preload adjacent
```

#### For Demo/Kiosk Mode
```javascript
showLoadingScreen: false,
showHintOnStart: false,
enableNavigationButtons: false,
preventAccidentalExit: false,
```

### Accessibility

1. **Keyboard Navigation**: Always enabled by default
2. **Focus Indicators**: Keep default focus styles
3. **Screen Readers**: Add ARIA labels to buttons
4. **High Contrast**: Test with OS high contrast mode

### Browser Compatibility

| Browser | Version | Support |
|---------|---------|---------|
| Chrome | 90+ | ✅ Full |
| Firefox | 88+ | ✅ Full |
| Safari | 14+ | ✅ Full |
| Edge | 90+ | ✅ Full |
| Mobile Safari | 14+ | ✅ Full |
| Mobile Chrome | 90+ | ✅ Full |

### Testing Checklist

Before presenting:
- [ ] All slides load correctly
- [ ] Navigation works (keyboard, mouse, touch)
- [ ] Overview mode shows all thumbnails
- [ ] Fullscreen works
- [ ] Progress bar updates
- [ ] Buttons respond correctly
- [ ] Test on actual presentation device
- [ ] Test with presentation remote (if using)
- [ ] Have backup (PDF export)

### Deployment

#### Local Presentation
1. Copy all files to USB drive
2. Test on presentation computer beforehand
3. Ensure browser doesn't require internet
4. Disable system notifications

#### Web Hosting
1. Upload all files to web server
2. Ensure MIME types correct (.html = text/html)
3. Test on different devices
4. Consider CDN for large files

#### Embedded iframe
```html
<iframe src="presentation.html?slide=1" 
        width="1920" height="1080" 
        allowfullscreen></iframe>
```

---

## 🎓 Advanced Topics

### Custom Loading Screen

Edit the loading screen HTML:
```html
<div class="loading-screen" id="loadingScreen">
    <img src="logo.png" alt="Logo" style="width: 200px;">
    <div class="loading-text">Loading Your Presentation...</div>
    <!-- ... -->
</div>
```

### Add Custom Buttons

```html
<button class="top-btn" id="customBtn" title="Custom Action">
    <i class="fas fa-star"></i>
</button>
```

```javascript
document.getElementById('customBtn').addEventListener('click', () => {
    alert('Custom button clicked!');
});
```

### Track Analytics

```javascript
// Override showSlide to track views
const originalShowSlide = showSlide;
function showSlide(slideNum) {
    // Send analytics
    if (typeof gtag !== 'undefined') {
        gtag('event', 'slide_view', {
            'slide_number': slideNum
        });
    }
    
    // Call original
    originalShowSlide(slideNum);
}
```

### Remote Control Support

Most presentation remotes send keyboard events (arrow keys), so they work automatically. For custom remotes:

```javascript
// Listen for custom remote events
document.addEventListener('remoteNext', () => {
    window.presentation.nextSlide();
});

document.addEventListener('remotePrev', () => {
    window.presentation.prevSlide();
});
```

---

## 📝 Quick Reference Card

Print this for presenters:

```
NAVIGATION
→ ↓ Space    Next slide
← ↑          Previous slide  
Home         First slide
End          Last slide
1-9          Jump to slide

MODES
O / Esc      Overview mode
F            Fullscreen
H            Show/hide hints

OVERVIEW MODE
Click        Jump to slide
Scroll       Navigate grid
0-9          Jump to slide 1-10
```

---

## 📞 Support

### Documentation
- Full source code in `presentation.html`
- Inline comments explain all functions
- User Options (slide count, upscale toggle) at the very top of the file
- Advanced CONFIG object inside the main `<script>` section

### Common Questions

**Q: Can I use PowerPoint/Keynote slides?**  
A: Export each slide as HTML or convert to images and embed in HTML.

**Q: Can I embed videos?**  
A: Yes, in individual slide HTML files using `<video>` tags.

**Q: Can I use this offline?**  
A: Yes, download Font Awesome icons and Google Fonts for fully offline use.

**Q: Can I customize the colors?**  
A: Yes, edit CSS variables in `:root` section.

**Q: Can I add speaker notes?**  
A: Add a second display or create a separate notes HTML file.

**Q: Can I export to PDF?**  
A: Use browser Print → Save as PDF (one slide per page).

---

## 🎉 You're Ready!

Your presentation system is now configured and ready to use. Press `F` for fullscreen, use arrow keys to navigate, and press `O` for overview mode.

**Enjoy your presentation!** 🚀

