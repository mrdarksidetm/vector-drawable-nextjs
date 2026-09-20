<div align="center">
  <img width="80" height="80" src="public/apple-touch-icon.png" alt="VectorDrawable to SVG" />
  <h1>VectorDrawable to SVG Converter</h1>
  <p><b>Real-time side-by-side Android Vector Drawable XML editor & live SVG preview</b></p>
  <p>
    <a href="https://mrdarksidetm.github.io/vector-drawable-nextjs/"><img src="https://img.shields.io/badge/🚀_Live_Demo-GitHub_Pages-269bff?style=for-the-badge&logo=github" alt="Live Demo on GitHub Pages" /></a>
  </p>
  <p>
    <a href="https://github.com/mrdarksidetm/vector-drawable-nextjs/actions/workflows/deploy.yml"><img src="https://github.com/mrdarksidetm/vector-drawable-nextjs/actions/workflows/deploy.yml/badge.svg" alt="Deploy to GitHub Pages" /></a>
    <img src="https://img.shields.io/badge/Next.js-13.1.6-black?style=flat-square&logo=nextdotjs" alt="Next.js" />
    <img src="https://img.shields.io/badge/React-18.2.0-blue?style=flat-square&logo=react" alt="React" />
    <img src="https://img.shields.io/badge/CodeMirror-6-darkgreen?style=flat-square" alt="CodeMirror 6" />
    <a href="LICENSE"><img src="https://img.shields.io/badge/License-MIT-yellow.svg?style=flat-square" alt="License: MIT" /></a>
  </p>
</div>

---

## 🌟 Acknowledgement & Credits

This project is a fork of [**seanghay/vector-drawable-nextjs**](https://github.com/seanghay/vector-drawable-nextjs) and is powered by the core engine [**vector-drawable-svg**](https://github.com/seanghay/vector-drawable-svg).

- **Original Creator & Core Engine**: [@seanghay](https://github.com/seanghay)
- **Original App**: [vd.floo.app](https://vd.floo.app/)
- **Upstream Repository**: [seanghay/vector-drawable-nextjs](https://github.com/seanghay/vector-drawable-nextjs)

All credits for the core conversion parser and original sleek design language belong to [@seanghay](https://github.com/seanghay). Please support the original creator with a star! ⭐

---

## 🚀 Key Improvements in this Fork

### 1. ⚡ Side-by-Side Dual-Pane Workspace
* Real-time Android Vector Drawable `<vector ...>` XML editor on the left pane feeding live SVG preview on the right pane.
* Instant conversion on every keystroke with live syntax error feedback.

### 2. 📱 Adaptive Segmented Mobile View (≤ 768px)
* Seamless Material 3 segmented tab switcher (`XML Editor` | `Live Preview`) exclusively on mobile viewports.
* **Intelligent Auto-Switching**: Automatically flips to the `Live Preview` tab immediately whenever a sample is loaded or an XML file is dropped.
* Retains full desktop side-by-side dual-pane grid on laptops, tablets, and wide displays (`> 768px`).

### 3. 🛡️ Always-On Word Wrapping & Zero Layout Blowout
* CodeMirror `@codemirror/view` line wrapping enabled by default.
* Interactive `Wrap: ON / OFF` toggle button with active state badge in the XML toolbar.
* Strict CSS Grid `minmax(0, 1fr)` architecture and `word-break: break-all` prevent long `android:pathData` strings from pushing the preview off-screen.

### 4. 🧩 SSR-Decoupled Dynamic Architecture
* CodeMirror decoupled via `next/dynamic` with `ssr: false` and monospace placeholder loader, eliminating SSR/hydration mismatches during static export.
* Explicit `<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=5.0" />` meta tag for optimal mobile rendering.

### 5. 💻 Interactive Material 3 CLI Card Footer
* Compact terminal card featuring the companion CLI command:
  ```bash
  npx vector-drawable-svg my-drawable.xml out.svg
  ```
* 1-tap clipboard copy with animated visual confirmation.
* Normalized 24px GitHub vector logo with smooth hover scale and credits pills.

### 6. 📋 One-Click SVG Markup Copy & Download
* Instant "Copy SVG" button copies clean SVG code directly to your clipboard.
* "Download" button saves the transformed SVG file directly to your disk.

### 7. 🧪 One-Click Sample Loader & File Drag-and-Drop
* Built-in Android Vector Drawable sample loader for immediate testing.
* Full drag-and-drop and file picker support populates both the editor and the preview instantly.

### 8. 🎨 Enhanced Preview Background Modes
* Switch between **Dark**, **Grid / Checkerboard** (for transparent path inspection), and **Light** backgrounds to test vectors with any fill or stroke color.

### 9. 🏷️ Android Resource Overrides Support
* Expandable resource override editor allowing you to resolve Android resource references such as `@color/accent` and `@dimen/size`.

### 10. 🌐 Automated GitHub Pages CI/CD
* Zero-configuration deployment via GitHub Actions (`.github/workflows/deploy.yml`) building static exports and publishing to GitHub Pages on every push to `main`.

---

## 💻 CLI Usage

You can also run the conversion directly in your terminal via `npx`:

```shell
npx vector-drawable-svg my-drawable.xml out.svg
```

---

## 🛠️ Development & Deployment

### Local Development
```shell
npm install
npm run dev
```

### Static Export Build
```shell
npm run build
```
Static export bundle is output to `./out` ready for deployment to GitHub Pages, Cloudflare Pages, or Netlify.

### Docker Deployment
```shell
docker compose up -d
```

---

## 📄 License

MIT — See [LICENSE](LICENSE) for details.
