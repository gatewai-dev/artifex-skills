---
name: Ken Burns
nodeType: KenBurns
summary: >
  Applies smooth pan, zoom, and translation animations over time to convert static or dynamic media into a video.
  Perfect for creating slideshows, dramatic photo showcases, document reviews, and cinematic visual tours.
triggers:
  - ken burns
  - pan and zoom
  - slideshow animation
  - image movement
  - zoom effect
  - camera animation
  - keyframe motion
---

# Ken Burns

## What It Does
Generates a Video from visual inputs (Image, Video, SVG, GIF, Lottie) by animating the camera position and scale using a list of custom keyframes. It translates, zooms, and holds on regions of the media, optionally adding motion blur.

## When to Use
- **Photo Showcases / Slideshows:** Animate high-resolution static images to make them feel active and cinematic.
- **Visual Tours:** Glide across large panoramic photos, maps, documents, or digital art to showcase detailed segments.
- **Focus Transitions:** Zoom in on a specific face or object in a photo, hold on it, and then slide/pan to another target area.

## Inputs
| Handle | Type | Required | Description |
|--------|------|----------|-------------|
| Media | Image, Video, SVG, GIF, Lottie | ✅ | The media content to apply the camera pan/zoom animations to |

## Config
| Field | Type | Range | Default | Description |
|-------|------|-------|---------|-------------|
| keyframes | array | Array of Keyframe objects | `[]` | Ordered list of camera positions, scales, durations, and easing styles. |
| motionBlurSize | number | ≥0 | 1.5 | Subpixel blur multiplier added to fast camera movements to smooth transition frames. Set to 0 to disable. |
| movementStyle | string (enum) | `spline`, `direct` | `"spline"` | Interpolation style between keyframes. Spline creates a curved, organic path; direct uses straight lines. |
| aspectRatio | string (enum) | `input`, `16:9`, `9:16`, `21:9`, `9:21`, `1:1`, `4:3`, `3:2`, `2:3`, `4:5`, `5:4` | `"input"` | Aspect ratio of the output video. `"input"` preserves the source media aspect ratio. |

### Keyframe Object Schema
Each keyframe inside `keyframes` specifies:
- **`x` / `y`** (number, required): The target focus coordinates (0 to 100 percentage range).
- **`scale`** (number, required): The zoom factor. `1` is default size, `2` is twice as close, etc.
- **`durationMs`** (number, required): Transition duration in milliseconds *to get to* this keyframe's position and scale from the previous one. If this is the first keyframe, it represents the starting state.
- **`holdMs`** (number): Duration to remain static at this position and scale before moving to the next keyframe.
- **`easing`** (string, enum): Timing function for the transition. Options: `linear`, `ease-in`, `ease-out`, `ease-in-out`, `spring`.

## Output
| Handle | Type | Description |
|--------|------|-------------|
| Result | Video | The output video with the camera movement path rendered. |

## Common Patterns
- **Slow Zoom-in Showcase:** Keyframe 0 starting at center `(50, 50)`, scale `1`. Keyframe 1 at center `(50, 50)`, scale `1.5`, with `durationMs: 3000` (transitioning over 3 seconds) and `holdMs: 1000`.
- **A to B Pan:** Keyframe 0 starting at top-left `(20, 20)`, scale `2`. Keyframe 1 moving to bottom-right `(80, 80)`, scale `2`, with `durationMs: 4000` (gliding across in 4 seconds).
- **Keyframe Location:** When prompting an image or video for AI processing, make sure you specify the keyframe locations in the prompt. For example, "4 rectangular keyframes on each corner as grid no grid corners" or "3 keyframes on left, middle and right vertically with 9:16 aspect ratio"
- **Duration:** Duration defines how long it takes to get to the final state of the node.

## Limitations
- Output is always a `Video` because the effect dynamically animates spatial properties over a timeline.
- High zoom scales (e.g., scale > 4) might pixelate low-resolution source images.
