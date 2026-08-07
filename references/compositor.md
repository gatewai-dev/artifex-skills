---
name: compositor
description: "Composes multiple media layers (Text, Image, SVG, Audio, Caption, Video, GIF, and Lottie) into a single image or video file. Supports layer positioning, timing, opacity, blending, animations, volume, transitions, and timeline segments."
metadata:
  nodeType: Compositor
  triggers: "compositor, composite, layer, merge media, multi-layer, overlay, picture in picture, video layout"
---

# Compositor

## What It Does
Composes multiple media inputs into a single ordered stack of layers. It outputs a combined Image or Video based on the input layer types, configurations, and spatial or timing properties.

## When to Use
- **Overlays / Watermarks:** Overlay text, logos, captions, or SVGs onto video or image backgrounds.
- **Picture-in-Picture:** Render multiple videos or images simultaneously in a split-screen or overlay layout.
- **Timeline Composition:** Arrange audio tracks, voiceovers, Lottie animations, and video segments along a timeline.
- **Visual Styling:** Use CSS-like layout properties, borders, padding, shadows, blending modes, and transitions between media assets. Supports styling parameters for Text and Caption layers including font colors, sizes, background colors, custom border radius/padding, line-by-line rounded text boxes (via `borderRadius` or `strokeRadius` / `useRoundedTextBox`), high-quality text outline/stroke rendering (via `stroke` and `strokeWidth`), and multiple drop shadows.

## Inputs
This node uses **Variable Inputs**. You can add dynamically named input handles of the following types:
- `Text`
- `Image`
- `Video`
- `Audio`
- `Caption`
- `SVG`
- `GIF`
- `Lottie`

## Config
| Field | Type | Range | Default | Description |
|-------|------|-------|---------|-------------|
| width | number | ≥1 | 1080 | Canvas width in pixels. |
| height | number | ≥1 | 1080 | Canvas height in pixels. |
| backgroundColor | string | Hex/RGB CSS Color | undefined | Background color of the compositor canvas. |
| volume | number | 0–100 | undefined | Overall master audio volume scaling. |
| FPS | number | 1–120 | 24 | Frames per second for video output. |
| layerUpdates | array | Array of Layer Objects | `[]` | Ordered list of layer settings, mapped via `inputHandleId` to the dynamic inputs. |

### Layer Object Schema
Each layer in `layerUpdates` supports:
- **`id`** (string, required): A unique identifier for the layer.
- **`inputHandleId`** (string, required): Maps this layer configuration to a specific dynamic input handle.
- **`type`** (string, enum): The media type of this layer (e.g. `Video`, `Image`, etc.).
- **`x` / `y`** (number): X/Y offset from the canvas top-left.
- **`width` / `height`** (number): Explicit layer dimensions.
- **`scale` / `rotation` / `opacity`**: Scaling multiplier, rotation in degrees, and opacity percentage (0-1).
- **`blendMode`** (string): Standard HTML/Canvas blending or Porter-Duff composite operation. Supports blending modes (e.g., `multiply`, `screen`, `overlay`, `darken`, `lighten`) and compositing/masking operations (e.g., `source-over`, `destination-out` for text cutouts, `destination-in` for masking, `source-in`, `source-out`, `source-atop`, `destination-over`, `destination-atop`, `lighter`, `copy`, `xor`).
- **`startFrame` / `durationInMS`**: Timing configurations. Note that `startFrame` is measured in frames (seconds * FPS of the canvas), while `durationInMS` and other duration/transition/trim properties are measured in milliseconds (ms).
- **`trimStart` / `trimEnd`**: Trims the start/end duration of media layers (in ms).
- **`volume`**: Volume level for audio/video layers (0 to 100).
- **`hidden`** (boolean): Hides the layer visually during rendering.
- **`muted`** (boolean): Mutes the audio track of the layer.
- **`transition`** (object): Wipe or crossfade transitions between layers:
  - `type`: `crossfade`, `wipe-left`, `wipe-right`, `slide-up`, `slide-down`
  - `durationInMS`: transition duration in ms.
- **`animations`** (array): Keyframe-based animations such as `fade-in`, `fade-out`, `zoom-in`, `zoom-out`, etc.
- **`backgroundColor`** (string): CSS background color (e.g. Hex, RGB) for the layer.
- **`borderColor`** (string): CSS color for the layer border.
- **`borderWidth`** (number): Width of the layer border in pixels.
- **`strokeRadius`** (number): Corner radius of the layer background, content mask, and border in pixels.
- **`strokeAlign`** (string): Alignment of the border relative to the layer bounds (`inside`, `center`, `outside`).
- **`bottomPadding`** (number): Required for `Caption` type layers. Specifies the offset in pixels from the bottom of the container.
- **`zIndex`** (number): Specifies the stack order. Higher values render on top.

### Layering / Z-Index Order
- Layers are drawn in ascending order of their `zIndex` (defaulting to `0`).
- If `zIndex` values are equal or omitted, the **last** item in the `layerUpdates` array is drawn on top of the earlier ones.

## Output
| Handle | Type | Description |
|--------|------|-------------|
| Result | Image, Video | The final rendered composite media file. |

## Common Patterns
- **Watermarking a Video:** Connect a video to input `A` and a PNG to input `B`. Position `B` in the bottom-right corner, apply lower opacity, and render the output.
- **Subtitled Video:** Feed video into `Video` input and captions into `Caption` input. The compositor aligns and renders subtitles over the active frames. Always place the `Caption` layer at the end of the `layerUpdates` array (or with a higher `zIndex`) so subtitles render on top of the video content.
- **Audio Over Dubbing:** Connect a mute/low-volume video layer and a high-quality audio file, aligning the audio track's start frame.
- **Creating Video Ads:** Combine video, audio, text, and animations to create engaging video advertisements.
- **Creating Movie or Trailers:** Create movie or trailers by combining multiple video clips, audio tracks, and text animations.
- **Creating Reacts or Memes:** Combine video, audio, text, and animations to create funny reacts or memes.
- **Creating TikTok or Instagram Reels:** Combine video, audio, text, and animations to create engaging TikTok or Instagram Reels.


## Don't Forget
Connecting layers doesn't make them render, you should set the full layerUpdates config directly with proper handle IDs for all three layers.

## Limitations
- If any layer contains video, audio, captions, GIFs, Lottie, or text animation, the compositor outputs a `Video`. Otherwise, it outputs a static `Image`.
- Rendering performance depends on the complexity of layers, video durations, and active transitions or animations.
