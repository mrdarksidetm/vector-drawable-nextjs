# Version & Changelog — VectorDrawable to SVG (Next.js)

The absolute source of truth for the project's evolution and changelog history.
Strict Append Pattern: All updates are permanently appended to the bottom.

---

## Libraries & Tools
- Next.js: `13.1.6`
- React: `18.2.0`
- React DOM: `18.2.0`
- vector-drawable-svg: `^1.1.4`
- @uiw/react-codemirror: `^4.21.7`
- @codemirror/lang-xml: `^6.0.2`
- @codemirror/view: `^6.15.0`
- @uiw/codemirror-theme-vscode: `^4.21.7`
- react-inlinesvg: `^3.0.2`
- react-sage: `^0.3.16`
- react-svg: `^16.1.6`
- @vercel/analytics: `^0.1.11`
- react-github-btn: `^1.4.0`

---

## Log Entries

### [2026-09-19 22:36:00 IST] - Project Initialization & Fork
- **Author**: mrdarksidetm
- **Repository**: `https://github.com/mrdarksidetm/vector-drawable-nextjs`
- **Upstream**: `https://github.com/seanghay/vector-drawable-nextjs`
- **Engine**: `vector-drawable-svg` by @seanghay
- **Status**: Forked upstream repository via GitHub CLI.
- **Objective**: Improve the app by introducing a side-by-side XML editor feeding Android Vector Drawable XML into real-time SVG live preview, while preserving 100% of the original design language and giving full credits to the original author.
- **Deployment Target**: GitHub Pages with automated CI/CD via GitHub Actions.

### [2026-09-19 22:38:00 IST] - Dual-Pane Live XML Editor & GitHub Pages Integration
- **Author**: mrdarksidetm
- **Status**: Completed feature implementation and GitHub Pages workflow setup.
- **Files Modified**:
  - `pages/index.js`: Replaced single-dropzone layout with responsive dual-pane workspace. Left pane features CodeMirror XML editor with live feedback, sample loader, file picker, and copy XML actions, alongside expandable resource overrides. Right pane features live SVG preview, background mode switcher (dark, grid, light), Copy SVG button, and Download button. Maintained drag-and-drop compatibility.
  - `styles/globals.css`: Added CSS rules for `.vd-workspace`, `.vd-pane`, `.vd-toolbar`, `.vd-btn-ghost`, `.vd-editor-wrapper`, `.vd-preview-box` background variations (dark/checkerboard/light), and responsive mobile stack while preserving the exact Material dark aesthetic and color scheme. Expanded `.container` width to 1260px for comfortable desktop side-by-side editing.
  - `pages/_document.js`: Replaced root-relative asset URLs with relative paths to ensure static asset resolution on GitHub Pages under repository subpaths.
  - `next.config.js`: Added support for GitHub Pages `basePath` and `assetPrefix` during static export.
  - `.github/workflows/deploy.yml`: Created automated GitHub Actions workflow to build and deploy static export to GitHub Pages on pushes to `main`.
  - `README.md`: Documented key improvements, live GitHub Pages URL, and prominent credits to @seanghay for engine and original design.
- **Remote Verification**: Remote CI/CD pipeline configured for GitHub Pages deployment. Zero local builds executed.

### [2026-09-19 22:41:00 IST] - Local Cleanup, Branch Audit & Pages Enablement
- **Author**: mrdarksidetm
- **Status**: Cleaned up all local downloaded modules; enabled GitHub Pages on repository; audited upstream branches.
- **Actions**:
  - Removed all locally downloaded packages (`node_modules`, `.next`, cache) to guarantee zero disk clutter.
  - Inspected upstream branch `renovate/configure` (confirmed to be an abandoned 2022 Renovate configuration branch, unmerged into `main`).
  - Enabled GitHub Pages build type `workflow` via GitHub CLI API on `mrdarksidetm/vector-drawable-nextjs`.
  - Updated `.github/workflows/deploy.yml` with `node-version: 22` and `enablement: true`.
  - Removed legacy upstream `docker_build.yml` which required upstream secrets.

### [2026-09-19 22:42:30 IST] - Next.js Static Export Configuration
- **Author**: mrdarksidetm
- **Status**: Configured `package.json` build script to `next build && next export`.
- **Reason**: Next.js 13.1.6 requires `next export` to output the static HTML bundle to `./out` for GitHub Pages artifact upload.
- **Verification**: Will verify via remote GitHub Actions CI/CD.

### [2026-09-20 09:10:00 IST] - CodeMirror Word-Wrapping & Universal Responsive Adaptation
- **Author**: mrdarksidetm
- **Status**: Completed word-wrapping integration and responsive screen adaptation for all device displays (phones, tablets, PCs).
- **Files Modified**:
  - `pages/index.js`:
    - Imported `EditorView` from `@codemirror/view`.
    - Added `wordWrap` state defaulting to `true` ("always word wrap is on") and memoized `editorExtensions` containing `EditorView.lineWrapping`.
    - Added interactive `Wrap: ON / OFF` toggle in the XML editor toolbar with active state styling.
    - Attached `editorExtensions` to both the primary XML editor and the Android Resource Overrides editor.
    - Updated rendered `<SVG>` component to fluid `width="100%"` and `height="100%"` scaling.
  - `styles/globals.css`:
    - Updated `.vd-workspace` grid to `grid-template-columns: minmax(0, 1fr) minmax(0, 1fr)` to prevent grid blowout caused by long XML lines or unwrapped path data.
    - Added `min-width: 0`, `max-width: 100%`, and `width: 100%` across `.vd-pane`, `.vd-editor-wrapper`, `.vd-preview-box`, and `.cm-editor` to ensure panes strictly respect column boundaries.
    - Added `.cm-content` and `.cm-line` rules enforcing `white-space: pre-wrap`, `word-break: break-all`, and `overflow-wrap: anywhere`.
    - Enhanced `.vd-title` and `.vd-subtitle` typography with fluid `clamp(...)` scaling.
    - Removed rigid `min-width: 400px` and `min-width: 300px` constraints from global `button` and `.vd-dropzone`.
    - Added comprehensive `@media (max-width: 960px)` and `@media (max-width: 600px)` rules for phones and tablets, including full-width toolbar wrap, stacked action buttons, and touch-optimized editor/preview heights.
  - `package.json`: Added `@codemirror/view` to `dependencies`.
  - `package-lock.json`: Synchronized `@codemirror/view` in root package dependencies for clean `npm ci` execution on GitHub Actions.
- **Verification**: Verified via git status, syntax check, and remote CI/CD deployment pipeline.

### [2026-09-20 10:15:00 IST] - SSR Hydration Fix, Dynamic CodeMirror & Architectural Viewport Standardization
- **Author**: mrdarksidetm
- **Status**: Completed SSR dynamic import decoupling, viewport standardization, and idiomatic Next.js root layout hierarchy.
- **Files Modified**:
  - `pages/index.js`:
    - Converted `@uiw/react-codemirror` import to `next/dynamic` with `ssr: false` and monospace placeholder loader, eliminating potential SSR/hydration mismatches and browser API access errors during static export.
    - Added explicit `<meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=5.0" />` to `<Head>`.
    - Wrapped page content in semantic `<main className="container">`.
  - `pages/_document.js`:
    - Removed extraneous `.container` div wrapping `<Main />` to prevent flexbox root shrinkage and ensure `<div id="__next">` receives unobstructed full-screen dimensions.
  - `styles/globals.css`:
    - Styled `html, body` and `#__next` with `width: 100%`, `min-height: 100vh`, and `overflow-x: hidden`.
    - Set `.container` to `display: flex; flex-direction: column; align-items: center; justify-content: flex-start; width: 100%; box-sizing: border-box;` for rock-solid centering across laptop and phone displays.
- **Verification**: Verified syntax and bracket matching across modified files.

### [2026-09-20 10:38:00 IST] - Adaptive Segmented Mobile View & Interactive CLI Card Footer
- **Author**: mrdarksidetm
- **Status**: Completed responsive segmented tab switcher for mobile devices and unified Material 3 card footer with 1-tap clipboard copy.
- **Files Modified**:
  - `pages/index.js`:
    - Introduced `activeTab` state (`'editor' | 'preview'`) and added `.vd-mobile-segmented-control` tab bar that appears exclusively on screens `<= 768px`.
    - Added auto-switch trigger to activate the preview tab immediately upon file drop or sample load.
    - Updated left pane with `.vd-pane-editor` and right pane with `.vd-pane-preview`, applying conditional `.vd-mobile-active` class for mobile tab toggling while keeping desktop dual-pane grid active.
    - Added `copyCliCommand` with feedback state and refactored footer to embed an interactive `.vd-cli-card` with 1-tap copy and responsive credit pills.
  - `styles/globals.css`:
    - Added CSS rules for `.vd-mobile-segmented-control`, `.vd-segment-btn` (with active blue accent glow and green live SVG indicator dot).
    - Configured `@media (max-width: 768px)` to hide inactive panes on mobile, while ensuring `@media (min-width: 769px)` preserves full side-by-side dual-pane view on desktops, laptops, and tablets.
    - Designed Material 3 `.vd-cli-card`, interactive `.vd-code-snippet` with hover effects, and rounded `.vd-credit-pill` tags.
    - Reduced mobile footer margin-bottom to 32px to eliminate excessive dead scroll.
- **Verification**: Verified via git status, bracket integrity check, and remote CI/CD deployment pipeline.
