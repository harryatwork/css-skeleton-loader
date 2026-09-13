<div align="center">

# 💀 CSS Skeleton Loader

**Pure CSS shimmer-loading placeholders — the Facebook/YouTube loading effect with zero JavaScript.**

[![CSS3](https://img.shields.io/badge/CSS3-pure-1572B6?style=flat-square&logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)
[![No JavaScript](https://img.shields.io/badge/JavaScript-zero-brightgreen?style=flat-square)](https://github.com/harryatwork/css-skeleton-loader)
[![Plug and play](https://img.shields.io/badge/setup-one--class-orange?style=flat-square)](https://github.com/harryatwork/css-skeleton-loader)
[![License](https://img.shields.io/badge/license-MIT-a855f7?style=flat-square)](LICENSE)

[Quick Start](#-quick-start) · [Variants](#-variants) · [Customisation](#-customisation)

</div>

---

## The Problem

Blank white screens while content loads feel broken. Spinner icons feel 2012. Modern apps (LinkedIn, YouTube, Facebook) show skeleton placeholders — grey shimmer shapes that mirror the actual layout. Building this from scratch every project is a waste of an hour. This is the one-file solution.

---

## ✨ Features

- 🚀 **Zero JavaScript** — 100% CSS animation, no scripting required
- 🎨 **Shimmer effect** — diagonal gradient sweep animation, left to right
- 📦 **Multiple variants** — card, list item, avatar, text lines, image placeholder
- 📱 **Responsive** — scales naturally inside any flex/grid container
- 🌑 **Dark mode ready** — CSS variables swap the palette automatically
- ⚡ **One class to activate** — add `.skeleton` to any element, done
- 🎛️ **Configurable speed** — CSS variable controls animation duration globally

---

## 🔧 How It Works

A `linear-gradient` with a sharp white/transparent transition is positioned off the left edge of the element. A `@keyframes` animation slides it from `-100%` to `+200%` on the X axis — this creates the shimmer sweep. The element background is a muted grey (`--skeleton-base`) and the moving gradient is a lighter highlight (`--skeleton-highlight`).

```css
/* The shimmer in 15 lines */
.skeleton {
  background: var(--skeleton-base);
  background-image: linear-gradient(
    90deg,
    var(--skeleton-base) 0%,
    var(--skeleton-highlight) 50%,
    var(--skeleton-base) 100%
  );
  background-size: 200% 100%;
  animation: skeleton-shimmer 1.4s ease-in-out infinite;
  border-radius: var(--skeleton-radius);
}

@keyframes skeleton-shimmer {
  0%   { background-position: 200% 0; }
  100% { background-position: -200% 0; }
}
```

---

## 🚀 Quick Start

### 1 — Include the stylesheet

```html
<link rel="stylesheet" href="skeleton.css">
```

### 2 — Build your skeleton layout

```html
<!-- Card skeleton -->
<div class="skeleton-card">
  <div class="skeleton skeleton-image"></div>
  <div class="skeleton-body">
    <div class="skeleton skeleton-line skeleton-line--full"></div>
    <div class="skeleton skeleton-line skeleton-line--75"></div>
    <div class="skeleton skeleton-line skeleton-line--50"></div>
  </div>
</div>
```

### 3 — Remove it once data loads

```javascript
fetch('/api/posts').then(res => res.json()).then(data => {
  document.querySelector('.skeleton-card').remove();
  renderPost(data);
});
```

---

## 📦 Variants

| Class | Shape | Use case |
|---|---|---|
| `.skeleton-line` | Full-width bar, 16px tall | Text line replacement |
| `.skeleton-line--75` | 75% width bar | Shorter sentence line |
| `.skeleton-line--50` | 50% width bar | Short last line |
| `.skeleton-avatar` | 48×48 circle | Profile photo |
| `.skeleton-avatar--lg` | 72×72 circle | Large profile photo |
| `.skeleton-image` | 100% wide, 200px tall | Card image placeholder |
| `.skeleton-button` | 120×40px rounded | CTA button placeholder |
| `.skeleton-badge` | 80×24px pill | Tag/badge placeholder |

---

## 🎨 Customisation

All values are CSS custom properties — override in `:root` or any parent selector:

```css
:root {
  --skeleton-base:      #e2e8f0;   /* Base grey */
  --skeleton-highlight: #f8fafc;   /* Shimmer highlight colour */
  --skeleton-radius:    6px;        /* Border radius on all skeletons */
  --skeleton-speed:     1.4s;       /* Animation duration */
}

/* Dark mode */
@media (prefers-color-scheme: dark) {
  :root {
    --skeleton-base:      #1e293b;
    --skeleton-highlight: #334155;
  }
}
```

---

## 📁 Project Structure

```
css-skeleton-loader/
├── skeleton.css          # Core stylesheet — all variants and animation
├── demo/
│   ├── index.html        # Interactive demo with toggle
│   └── demo.css          # Demo layout styles
└── README.md
```

---

<details>
<summary><strong>Common issues and fixes</strong></summary>

| Issue | Fix |
|---|---|
| Shimmer not visible | Check that `skeleton.css` is loaded and `.skeleton` class is applied |
| Animation looks choppy | Ensure `will-change: background-position` is set on `.skeleton` |
| Dark mode not switching | Define both light and dark `--skeleton-base` and `--skeleton-highlight` in your `:root` |
| Skeleton doesn't fill container | Parent must have a defined width; `display: block` or `flex` on parent |

</details>

---

<div align="center">

Built by [Harish K](https://github.com/harryatwork)

</div>