---
name: HTML Video Renderer
nodeType: HTMLVideoRender
summary: >
  Renders raw HTML/CSS/GSAP/ThreeJS compositions to high-quality MP4 videos using hyperframes.
  Includes input-level validations for structure, dependency loading, and animation compatibility.
triggers:
  - html video renderer
  - html renderer
  - render html to video
  - render code to video
  - render web page to video
---

# HTML Video Renderer

The **HTML Video Renderer** node takes raw HTML content as input, validates it for basic compatibility and script correctness, and renders it into a high-quality seek-safe MP4 video asset using hyperframes. If you have terminal/CLI access, you can update the underlying hyperframes skills dynamically:
```bash
npx hyperframes skills update
```
otherwise use existing tools to read skills.

It is completely configuration-less. The renderer automatically extracts design properties (viewport width/height, framerate, and duration) directly from the HTML elements/metadata at runtime or uses the probed video properties of the completed render.

---

## 1. Features & Capability Summary

* **HTML to MP4 Video Compilation:** Launches a headless browser container to capture, compile, and merge frames into an MP4 video file.
* **Probed Property Discovery:** Automatically checks final physical dimensions, duration, and frame rate of the rendered video utilizing `ffprobe` to ensure downstream canvas nodes have accurate metadata parameters.
* **Fingerprint Cache Support:** Automatically caches renders based on SHA256 fingerprints of the raw HTML content, avoiding redundant render execution time when HTML code has not changed.
* **Pre-Execution Lint Validation:** Validates the input HTML string before triggering the queue to make sure it contains valid elements, libraries, and animations.

---

## 2. Config & Schema Properties

The Motion Renderer is completely **configuration-less**. Viewport and duration properties are determined directly from:
1. Target attributes in the HTML container (e.g. `data-width`, `data-height`, `data-duration`).
2. Downstream `ffprobe` media inspection of the rendered output file.

---

## 3. Handles (Inputs & Outputs)

### Inputs
* `HTML` (`Text`, Required): The raw single-file HTML code containing elements, styles, scripts, and timelines to be rendered.

### Outputs
* `Video Result` (`Video`): The pre-rendered MP4 video file asset.

---

## 4. Pre-Execution Validation (Lint Checks)

The node validates inputs synchronously inside the node graph before allowing rendering to run. This prevents rendering queue timeouts or black frames due to coding errors:

1. **HTML5 Document Structure:** The HTML content must start with a proper document declaration (`<!DOCTYPE html>`) and contain `<html>`, `<head>`, and `<body>` tags. Fragments or bare tags are rejected.
2. **GSAP Script Verification:** If the HTML includes references to `gsap` animations, it must explicitly load the GSAP script in the document (e.g. from the CDN: `cdn.jsdelivr.net`).
3. **GSAP Opacity Conflict Protection:** Warns if an element has CSS `opacity: 0` static styling combined with a `gsap.from()` animation targeting `opacity: 0` (which causes the element to animate from 0 to 0 and remain invisible).

---

## 5. Technical Requirements for Compositions

When authoring or generating HTML animations for the Motion Renderer, compositions must adhere to these technical rules to pass linting and render correctly:

### 1. Document Wrappers & Tags
Every composition must be a fully formed HTML5 document:
* Must start with `<!DOCTYPE html>`.
* Must contain `<html>`, `<head>`, and `<body>` tags. 
* Do not submit partial fragments or styling blocks without full page enclosures.

### 2. Dependency Script CDNs
All script files and animation libraries (like GSAP or Three.js) must be loaded explicitly via a CDN in the `<head>` of the document.
* For **GSAP**: Load `<script src="https://cdn.jsdelivr.net/npm/gsap@3.12.2/dist/gsap.min.js" defer></script>`.
* Include the `defer` attribute on all external script tags to prevent blocking warnings.

### 3. Opacity Animations and CSS Styles
Avoid combining static CSS declarations of `opacity: 0` with `gsap.from()` animations animating to opacity `0`. Because `gsap.from()` animates *from* the specified parameters to the current CSS values, this results in an animation from `0` to `0`, making the target element permanently invisible.
* **Correction A:** Set the static CSS style to `opacity: 1` and run `gsap.from(element, { opacity: 0 })`.
* **Correction B:** Keep the CSS style at `opacity: 0` and animate using `gsap.to(element, { opacity: 1 })`.

---

## 6. Recommended UI & Visual Libraries (CDN Stack & Seekability Rules)

To build robust, seekable, and beautiful animations that compile frame-accurately in the headless renderer, utilize the following CDN stack and integration rules:

### 1. Styling & Visual Foundations
* **Tailwind CSS (v4):** Load `<script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4.2.4" defer></script>`. Customize themes/utilities inside `<style type="text/tailwindcss">`.
* **DaisyUI:** Load `<link href="https://cdn.jsdelivr.net/npm/daisyui@4.12.10/dist/full.min.css" rel="stylesheet" type="text/css" />` for pre-built components (badges, stats, tables, cards).
* **Glassmorphism:** Implement native CSS backdrop filters (`backdrop-blur`) and layered border/box shadows.

### 2. Kinetic Typography & Titles
* **Splitting.js:** Load `<script src="https://unpkg.com/splitting/dist/splitting.min.js" defer></script>` and `<link rel="stylesheet" href="https://unpkg.com/splitting/dist/splitting.css" />` to split text elements into words or characters, then animate them using GSAP staggers.
* **Baffle.js:** Load `<script src="https://cdn.jsdelivr.net/npm/baffle@0.3.6/dist/baffle.min.js" defer></script>`. Use a GSAP timeline proxy to drive text scramble (`onUpdate` calling `b.reveal()`) to ensure seek-safety.

### 3. Data Visualization & Motion Overlays
* **ECharts:** Load `<script src="https://cdn.jsdelivr.net/npm/echarts@5.5.1/dist/echarts.min.js" defer></script>`. Disable internal animations (`animation: false`), drive values via a GSAP proxy, and call `chart.setOption()` on GSAP `onUpdate`.
* **Chart.js:** Load `<script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.3/dist/chart.umd.js" defer></script>`. Disable animations/responsive resizing, update values via a GSAP proxy, and call `chart.update()` on GSAP `onUpdate`.
* **Lucide Icons:** Load `<script src="https://unpkg.com/lucide@latest" defer></script>` and call `lucide.createIcons();`, or use inline SVGs for stroke-drawing.

### 4. Canvas & Shader Effects
* **Curtains.js:** Load `<script src="https://cdn.jsdelivr.net/npm/curtainsjs@8.1.6/dist/curtains.umd.min.js" defer></script>`. Seekability Rule: Drive WebGL custom uniform variables (e.g. `uTime`, `uProgress`) via a GSAP proxy instead of the curtains auto-draw loop.
* **PixiJS:** Load `<script src="https://cdn.jsdelivr.net/npm/pixi.js@7.4.2/dist/pixi.min.js" defer></script>`. Seekability Rule: Turn off Pixi's auto-ticker (`app.ticker.stop()`). Control updates and rendering manually using a GSAP proxy to advance ticker time and call render on GSAP `onUpdate`:
  ```javascript
  app.ticker.stop();
  const pixiProxy = { time: 0 };
  tl.to(pixiProxy, {
    time: duration,
    duration: duration,
    ease: "none",
    onUpdate: () => {
      app.ticker.update(pixiProxy.time * 1000);
      app.renderer.render(app.stage);
    }
  }, 0);
  ```
* **Two.js / Paper.js:** 
  * Two.js CDN: `<script src="https://cdn.jsdelivr.net/npm/two.js@0.8.10/build/two.min.js" defer></script>`
  * Paper.js CDN: `<script src="https://cdn.jsdelivr.net/npm/paper@0.12.17/dist/paper-full.min.js" defer></script>`
  * Seekability Rule: Manually call `two.update()` or `paper.view.draw()` in the GSAP `onUpdate` callback.
