---
name: blur
description: "Applies various types of blurs (Gaussian, Box, Median, Motion, Bilateral, Edge-preserving, Radial, Zoom) to images, videos, GIFs, SVGs, and Lottie animations. Use this for depth-of-field effects, focus pull transitions, speed/movement effects, or visual styling."
metadata:
  nodeType: Blur
  triggers: "blur, defocus, soft focus, motion blur, radial blur, zoom blur, gaussian blur, box blur, median blur, bilateral blur, edge-preserving blur"
---

# Blur

## What It Does
Applies a digital blur effect to input visual media (Image, SVG, Video, Lottie, GIF). It supports multiple blur algorithms (such as Gaussian, Box, Median, Motion, Bilateral, Radial, Zoom, Edge-preserving) to achieve different styles and processing goals.

## When to Use
- **Visual Focus / Depth of Field:** Emphasize foreground elements by blurring the background.
- **Stylistic Transitions:** Animate the blur strength over time to transition between scenes.
- **Motion Effects:** Apply motion blur, radial blur, or zoom blur to simulate movement, speed, or action.
- **Privacy Masking / Obfuscation:** Blur faces, text, license plates, or specific areas of the media.
- **Artistic / Soft Looks:** Smooth skin tones, create dreamlike glow effects, or stylize visuals.

## Inputs
| Handle | Type | Required | Description |
|--------|------|----------|-------------|
| Input | Image, SVG, Video, Lottie, GIF | ✅ | The media to apply the blur effect to |
| Strength Signal | Number, Signal | ❌ | Optional signal or number to dynamically modulate the blur strength |

## Config
| Field | Type | Range | Default | Description |
|-------|------|-------|---------|-------------|
| blurType | string (enum) | Gaussian, Box, Median, Motion, Bilateral, Edge-preserving, Radial, Zoom | "Gaussian" | The algorithm used to calculate the blur. |
| strength | number | 0–100 | 5 | The intensity of the blur. 0 = no blur. Bindable to Signal/Number for animated transitions. |
| angle | number | 0–360 | 0 | The angle of direction for Motion blur (in degrees). |
| sigmaColor | number | 0.01–1.0 | 0.1 | Sigma value for color space in Bilateral / Edge-preserving blurs. High values mix farther colors. |
| centerX | number | 0–1.0 | 0.5 | Normalized horizontal center coordinate (0 to 1) for Radial and Zoom blurs. |
| centerY | number | 0–1.0 | 0.5 | Normalized vertical center coordinate (0 to 1) for Radial and Zoom blurs. |

## Output
| Handle | Type | Description |
|--------|------|-------------|
| Result | Image, Video, GIF | The visual media with the blur effect applied. |

## Common Patterns
- **Animated Transition Pipeline:** `Signal → Blur (strength bound to signal) → Export`
- **Background Defocus / Layering:** `Import (image) → Resize/Crop → Blur (high strength) → Compositor (background)`
- **Action/Speed Effect:** `Import (video) → Blur (blurType: Motion, strength: 15, angle: 90) → Export`
- **Vignette/Focus Pull:** `Import (image) → Blur (blurType: Zoom/Radial, centerX: 0.5, centerY: 0.5) → Export`

## Limitations
- Strength values are capped at 100.
- Radial and Zoom blurs calculate their center relative to the width and height using normalized `centerX`/`centerY` coordinates.
- Bilateral and Edge-preserving blurs are computationally more expensive and may impact rendering performance.
