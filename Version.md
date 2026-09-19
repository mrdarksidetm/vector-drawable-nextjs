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
