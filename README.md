<div align="center">
  <img width="80" height="80" src="public/apple-touch-icon.png" alt="VectorDrawable to SVG" />
  <h1>VectorDrawable to SVG Converter</h1>
  <p><b>Real-time side-by-side Android Vector Drawable XML editor & live SVG preview</b></p>
  <p>
    <a href="https://mrdarksidetm.github.io/vector-drawable-nextjs/"><strong>🚀 Live Demo on GitHub Pages</strong></a>
  </p>
</div>

---

## 🌟 Acknowledgement & Credits

This project is a fork of [**seanghay/vector-drawable-nextjs**](https://github.com/seanghay/vector-drawable-nextjs) and is powered by [**vector-drawable-svg**](https://github.com/seanghay/vector-drawable-svg).

- **Original Creator & Core Engine**: [@seanghay](https://github.com/seanghay)
- **Original App**: [vd.floo.app](https://vd.floo.app/)
- **Upstream Repository**: [seanghay/vector-drawable-nextjs](https://github.com/seanghay/vector-drawable-nextjs)

All credits for the core conversion engine, parsing logic, and original sleek design language belong to [@seanghay](https://github.com/seanghay). Please support the original creator with a star! ⭐

---

## 🚀 Key Improvements in this Fork

1. **Side-by-Side Live XML Editor**:
   - Instead of strictly requiring a `.xml` file to be uploaded from disk, you can now directly type or paste `<vector ...>` XML on the left pane.
   - Live real-time conversion: see your SVG render as you type with instant feedback.
2. **Copy SVG Markup with One Click**:
   - Instant "Copy SVG Code" button to grab the transformed SVG directly to your clipboard.
3. **One-Click Sample Loader**:
   - Test the converter immediately with built-in Android Vector Drawable samples.
4. **Enhanced Preview Backgrounds**:
   - Switch between **Dark**, **Grid/Checkerboard** (for transparent vectors), and **Light** background modes to inspect vectors with any fill color.
5. **Preserved File Drag & Drop**:
   - Full drag-and-drop and file picking support remains intact — dropping a file populates both the editor and the preview.
6. **Resource Overrides Supported**:
   - Retains full support for Android resource overrides like `@color/accent` and `@dimen/size`.
7. **Automated GitHub Pages Hosting**:
   - Zero-configuration deployment using GitHub Actions (`.github/workflows/deploy.yml`).

---

## 💻 CLI Usage

You can also run the conversion directly in your terminal via `npx`:

```shell
npx vector-drawable-svg my-drawable.xml out.svg
```

---

## 🛠️ Development & Deployment

### GitHub Pages (Automated CI/CD)
The repository includes a GitHub Actions workflow (`.github/workflows/deploy.yml`) that builds and deploys static exports directly to GitHub Pages on every push to `main`.

### Hosting with Docker
```shell
docker compose up -d
```

---

## 📄 License

MIT — See [LICENSE](LICENSE) for details.
