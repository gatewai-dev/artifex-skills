---
name: compositor
description: "Composes multiple media layers (Text, Image, SVG, Audio, Caption, Video, GIF, and Lottie) into a single image or video file. Supports layer positioning, timing, opacity, blending, keyframe animations, volume, and timeline segments."
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
- **Visual Styling:** Use CSS-like layout properties, borders, padding, shadows, blending modes, and keyframe animations. Supports styling parameters for Text and Caption layers including font colors, sizes, background colors, custom border radius/padding, line-by-line rounded text boxes (via `borderRadius` or `strokeRadius` / `useRoundedTextBox`), high-quality text outline/stroke rendering, and multiple drop shadows.

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
| width | number | 1–4096 | 1080 | Canvas width in pixels. |
| height | number | 1–4096 | 1080 | Canvas height in pixels. |
| backgroundColor | string | Hex/RGB CSS Color | undefined | Background color of the compositor canvas. |
| volume | number | 0–1 | 1 | Overall master audio volume scaling. |
| fps | number | 1–120 | 24 | Frames per second for video output. |
| mode | string | `"Video"` or `"Image"` | `"Video"` | Explicitly configures compositor rendering/output mode. |
| layers | array | Array of Layer Objects | `[]` | Ordered list of layer settings, mapped via `inputHandleId`. |

---

### Layer Object Schema
Each layer in `layers` supports:
- **`id`** (string, required): A unique identifier for the layer.
- **`inputHandleId`** (string, required): Maps this layer configuration to a specific dynamic input handle.
- **`type`** (string, enum): The media type of this layer (e.g. `Video`, `Image`, etc.).
- **`x` / `y`** (number): X/Y offset from the canvas top-left.
- **`width` / `height`** (number): Explicit layer dimensions (optional).
- **`scale` / `rotation` / `opacity`**: Scaling multiplier (default 1), rotation in degrees (default 0), and opacity percentage (0-1, default 1).
- **`blendMode`** (string): Standard HTML/Canvas blending or Porter-Duff composite operation.
- **`startFrame` / `durationFrames`** (integer, required): Timing configurations. `startFrame` and `durationFrames` are both measured in integer frames relative to the master timeline.
- **`trimStartFrames` / `trimEndFrames`** (integer): Trims the start/end duration of media layers (in frames).
- **`volume`**: Volume level for audio/video layers (0 to 1).
- **`hidden`** (boolean): Hides the layer visually during rendering.
- **`muted`** (boolean): Mutes the audio track of the layer.
- **`backgroundColor`** (string): CSS background color (e.g. Hex, RGB) for the layer.
- **`borderColor`** (string): CSS color for the layer border.
- **`borderWidth`** (number): Width of the layer border in pixels.
- **`strokeRadius`** (number): Corner radius of the layer background, content mask, and border in pixels.
- **`strokeAlign`** (string): Alignment of the border relative to the layer bounds (`inside`, `center`, `outside`).
- **`bottomPadding`** (number): Required for `Caption` type layers. Specifies the offset in pixels from the bottom of the container.
- **`zIndex`** (number): Specifies the stack order. Higher values render on top.
- **`animation`** (object): Timed, track-based keyframe configurations (§ Layer Animation Schema).

---

### Layer Animation Schema
- **`tracks`** (array): Up to 24 animation tracks.
Each track represents animatable property modifications:
  - **`id`** (string, required): Unique identifier for the track.
  - **`prop`** (string, enum, required): The property being animated: `x`, `y`, `scale`, `rotation`, `opacity`, `width`, `height`, `volume`, `hidden`, `muted`.
  - **`keyframes`** (array, required): Chronologically sorted keyframe points.
  - **`repeat`** (number, optional): GSAP loop count (e.g., -1 for infinite loops).
  - **`yoyo`** (boolean, optional): If true, animates back and forth.
  - **`durationFrames`** (number, optional): Explicit duration window.

#### Keyframe Schema:
  - **`id`** (string, required): Unique keyframe identifier.
  - **`frame`** (number, required): Clip-relative frame number where this keyframe is reached (`0` = layer start).
  - **`value`** (number or boolean, required): Target value at this keyframe.
  - **`ease`** (object, optional): Segment easing parameters.
    - **`name`**: `none`, `power1`, `power2`, `power3`, `sine`, `circ`, `expo`, `back`, `elastic`, `bounce`, `spring`.
    - **`dir`**: `in`, `out`, `inOut`.
    - **`params`** (array of numbers): Optional easing parameter overrides (e.g. `back.out(1.7)`).
  - **`presetGroupId`** (string, optional): Links to a Canva-style preset animation group.

---

### Layering / Z-Index Order
- Layers are drawn in ascending order of their `zIndex` (defaulting to `0`).
- If `zIndex` values are equal or omitted, the **last** item in the `layers` array is drawn on top of the earlier ones.

## Output
| Handle | Type | Description |
|--------|------|-------------|
| Result | Image, Video | The final rendered composite media file. |

## Common Patterns
- **Watermarking a Video:** Connect a video to input `A` and a PNG to input `B`. Position `B` in the bottom-right corner, apply lower opacity, and render the output.
- **Subtitled Video:** Feed video into `Video` input and captions into `Caption` input. The compositor aligns and renders subtitles over the active frames. Always place the `Caption` layer at the end of the `layers` array (or with a higher `zIndex`) so subtitles render on top of the video content.
- **Audio Over Dubbing:** Connect a mute/low-volume video layer and a high-quality audio file, aligning the audio track's start frame.

## Don't Forget
Connecting layers doesn't make them render, you should set the full layers config directly with proper handle IDs for all connected inputs.

## Example JSON Configuration
```json
{
  "width": 1920,
  "height": 1080,
  "backgroundColor": "#000000",
  "fps": 24,
  "mode": "Video",
  "layers": [
    {
      "id": "bg-layer",
      "inputHandleId": "background",
      "type": "Video",
      "x": 0,
      "y": 0,
      "startFrame": 0,
      "durationFrames": 72
    },
    {
      "id": "overlay-text",
      "inputHandleId": "text-title",
      "type": "Text",
      "x": 960,
      "y": 540,
      "startFrame": 12,
      "durationFrames": 48,
      "animation": {
        "tracks": [
          {
            "id": "fade-track",
            "prop": "opacity",
            "keyframes": [
              { "id": "kf0", "frame": 0, "value": 0, "ease": { "name": "power2", "dir": "out" } },
              { "id": "kf1", "frame": 12, "value": 1 }
            ]
          }
        ]
      }
    }
  ]
}
```
