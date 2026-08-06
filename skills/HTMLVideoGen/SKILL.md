---
name: HTML Video Generator
nodeType: HTMLVideoGen
summary: >
  Generates seekable HTML/CSS/GSAP animations using AI based on user text prompts and optional reference media (Images, Videos, SVGs, Captions, and Lottie animations).
  Ideal for custom CSS animations, product demos, dynamic text slides, and interactive visual effects.
triggers:
  - html video generator
  - html animation
  - gsap video
  - code animation
  - web animation
  - generate html video
  - threejs animation
  - threejs video
  - webgl animation
  - chart animation
  - render chart
  - 3d chart animation
---

# HTML Video Generator

> [!IMPORTANT]
> If you have terminal/CLI access, you can update the underlying hyperframes skills dynamically:

> ```bash
> npx hyperframes skills update
> ```
> otherwise use existing tools to read skills.

The **HTML Video Generator** node generates seekable HTML/CSS/GSAP animations using AI based on user text prompts and optional reference media (Images, Videos, SVGs, Captions, and Lottie animations). The generated HTML content is stored as an asset and rendered into an MP4 video.

For voiceovers, connecting caption reference of the voice is highly recommended to ensure the animation is synchronized with the voiceover.

---

## 1. Features & Capability Summary

* **AI HTML Code Generation:** Constructs single-file HTML documents containing styled elements and GSAP timelines registered to `window.__timelines` for seekable rendering.
* **Dual Deliverables Output:** Produces both an HTML source file asset and a rendered MP4 video file asset.
* **Reference Guidance Support:** Accepts reference images, videos, SVGs, and captions to guide visual layout, timing, or animations.
* **Three.js & WebGL 3D Support:** Construct deterministic 3D scenes with lighting, depth, shadows, and camera movement, rendering frame-accurately via the seek frame adapter.
* **Canvas Nesting & Composition Workaround:** Support layering HTML-in-Canvas elements over a WebGL render canvas using a custom onpaint composition logic.
* **Chart Rendering & Data Visualization:** Supports rendering 2D and 3D charts, plots, and dynamic data visualizations using inline SVGs, CSS, CDN chart libraries (e.g. Chart.js, D3.js), or Three.js for real 3D charts synced to the animation timeline.

---

## 2. Config & Schema Properties

| Field | Type | Default | Description |
|---|---|---|---|
| `model` | Enum | `"openai/gpt-5.6-luna"` | LLM model used for code generation (GPT-5.6, Gemini, DeepSeek). |
| `width` | Number | `1280` | Canvas width in pixels (1 to 4096). |
| `height` | Number | `720` | Canvas height in pixels (1 to 4096). |
| `fps` | Number | `24` | Video frame rate (12 to 60 FPS). |
| `durationSeconds` | Number | `5` | Video duration in seconds (0.5 to 30). |

---

## 3. Handles (Inputs & Outputs)

### Inputs
* `Prompt` (`Text`, Required): Natural language prompt describing desired layout and animation.
* `Reference Media` (`Image`, `Video`, `SVG`, `Caption`, `Lottie`, Optional): Optional reference media files, captions, or Lottie JSON animations for layout, visual context, or timing guidance.

### Outputs
* `HTML Result` (`Text`): Source HTML code string.
* `Video Result` (`Video`): Pre-rendered MP4 video file asset.

---

## 4. Recommended UI & Visual Libraries (CDN Stack)

To build stunning animations, you can load these visual/styling libraries directly via CDN. Ensure that any dynamic animations remain seek-safe and compatible with HyperFrames' GSAP-driven rendering timeline.

### 1. Styling & Visual Foundations
* **Tailwind CSS (v4):** Load `<script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4.2.4"></script>`. Customize themes/utilities inside `<style type="text/tailwindcss">`.
* **DaisyUI:** Load `<link href="https://cdn.jsdelivr.net/npm/daisyui@4.12.10/dist/full.min.css" rel="stylesheet" type="text/css" />` for clean components (badges, stats, grids).
* **Glassmorphism:** Use native CSS backdrop filters (`backdrop-blur`) and layered box-shadows.

### 2. Kinetic Typography & Titles
* **Splitting.js:** Load `<script src="https://unpkg.com/splitting/dist/splitting.min.js"></script>` and `<link rel="stylesheet" href="https://unpkg.com/splitting/dist/splitting.css" />` to split text elements into words/chars, then animate them using GSAP staggers.
* **Baffle.js:** Load `<script src="https://cdn.jsdelivr.net/npm/baffle@0.3.6/dist/baffle.min.js"></script>`. Use a GSAP timeline proxy to drive text scramble (`onUpdate` calling `b.reveal()`) to ensure seek-safety.

### 3. Data Visualization & Motion Overlays
* **ECharts:** Load `<script src="https://cdn.jsdelivr.net/npm/echarts@5.5.1/dist/echarts.min.js"></script>`. Disable internal animations (`animation: false`), drive values via a GSAP proxy, and call `chart.setOption()` on GSAP `onUpdate`.
* **Chart.js:** Load `<script src="https://cdn.jsdelivr.net/npm/chart.js@4.4.3/dist/chart.umd.js"></script>`. Disable animations/responsive resizing, update via GSAP proxy and call `chart.update()` on `onUpdate`.
* **Lucide Icons:** Load `<script src="https://unpkg.com/lucide@latest"></script>` and call `lucide.createIcons();`, or use inline SVGs for stroke-drawing.

### 4. Canvas & Shader Effects
* **Curtains.js:** Load `<script src="https://cdn.jsdelivr.net/npm/curtainsjs@8.1.6/dist/curtains.umd.min.js"></script>`. Drive uniform parameters (e.g. `uTime`) via a GSAP proxy instead of the curtains requestAnimationFrame loop.
* **PixiJS:** Load `<script src="https://cdn.jsdelivr.net/npm/pixi.js@7.4.2/dist/pixi.min.js"></script>`. Stop the ticker (`app.ticker.stop()`) and advance ticker frames manually in the GSAP `onUpdate` callback.
* **Two.js / Paper.js:** Load Two.js/Paper.js CDN and trigger view/canvas updates manually inside the GSAP `onUpdate` callback.

