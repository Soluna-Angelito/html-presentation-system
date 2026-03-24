# ⚡ Quick Start Guide

## 📦 Setup (2 minutes)

1. **Place files together**:
   ```
   your-folder/
   ├── presentation.html
   ├── slide1.html
   ├── slide2.html
   └── ... (all your slides)
   ```

2. **Configure** (open `presentation.html`, edit the **User Options** at the top):
   ```javascript
   const TOTAL_SLIDES  = 45;    // ← Change this to your slide count
   const ALLOW_UPSCALE = false; // ← true to scale up on large displays
   ```

3. **Open** `presentation.html` in browser

4. **Done!** ✨

---

## ⌨️ Essential Shortcuts

| What | Key |
|------|-----|
| **Next** | `→` `Space` |
| **Previous** | `←` |
| **Overview** | `O` |
| **Fullscreen** | `F` |

---

## ⚙️ Common Configurations

### Change Total Slides
```javascript
const TOTAL_SLIDES = 20;  // If you have 20 slides
```

### Scale Up on Large Displays
```javascript
const ALLOW_UPSCALE = true;  // Fills 2K/4K screens
```

### Different Slide Names (e.g., `page1.html`)
```javascript
slideFilePrefix: 'page',
```

### Adjust Overview Grid (in CONFIG)
```javascript
overviewCols: 5,      // 5 columns instead of 9
overviewScale: 0.15,  // Larger thumbnails
```

### Hide UI Elements (in CONFIG)
```javascript
showLoadingScreen: false,
enableProgressBar: false,
enableSlideCounter: false,
enableNavigationButtons: false,
```

---

## 🎨 Quick Theme Change

Find this in the CSS:
```css
:root {
    --primary-color: #667eea;  /* Your color here */
    --secondary-color: #764ba2;
    --accent-color: #fbbf24;
}
```

---

## 🚨 Troubleshooting

### Slides not loading?
- ✅ Check file names: `slide1.html`, `slide2.html`, etc.
- ✅ All files in same folder
- ✅ Count matches `TOTAL_SLIDES` at top of file

### Overview mode slow?
- ✅ Normal for first time (3-5 seconds)
- ✅ Second time should be instant

### Keyboard not working?
- ✅ Click on presentation area first
- ✅ Check `enableKeyboard: true` in config

---

## 📱 Works On

- ✅ Desktop (keyboard, mouse)
- ✅ Mobile (touch, swipe)
- ✅ Tablets (touch)
- ✅ Presentation remotes

---

## 🎯 Best Practices

1. **Test before presenting**
   - Load on actual presentation computer
   - Try all navigation methods
   - Enter fullscreen mode

2. **Backup plan**
   - Export to PDF (Print → Save as PDF)
   - Have files on USB drive

3. **For 100+ slides**
   ```javascript
   eagerLoadCount: 5,
   overviewCols: 10,
   ```

---

## 🔌 Developer API

```javascript
// Available at window.presentation
window.presentation.goToSlide(10);    // Jump to slide
window.presentation.nextSlide();       // Next
window.presentation.prevSlide();       // Previous
window.presentation.getCurrentSlide(); // Get current
```

---

## 📖 Full Documentation

See `USER_GUIDE.md` for:
- Complete configuration options
- Customization guide
- API reference
- Advanced features
- Troubleshooting

---

## ✅ Pre-Flight Checklist

Before presenting:
- [ ] All slides load
- [ ] Navigation works
- [ ] Overview mode works
- [ ] Fullscreen works
- [ ] Tested on presentation device
- [ ] Backup PDF ready

---

**You're all set! Press `F` for fullscreen and start presenting!** 🚀

