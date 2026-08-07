---
name: node-catalog
description: Authoritative catalog of all supported workflow canvas nodes, with links to their respective skills.
metadata:
  triggers: list nodes, supported node types, node catalog
---

# Node Catalog

Authoritative capabilities of every registered node. Input/output handles and dynamic (variable) inputs/outputs are read directly from each node manifest at build time — the same data `artifex nodes --json` reports. Featured nodes (58).

### Media

#### Apply LUT (`ApplyLUT`)

Apply a color lookup table (.cube) to media

- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Input` | Image, SVG, Video, Lottie, GIF | yes |
| `Lut` | LUT | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Image, Video, GIF | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [ApplyLUT Skill](file:///packages/artifex-skills/skills/apply-lut/SKILL.md).

---

#### Audio Compressor (`Compressor`)

Smooth out dynamic range and prevent audio clipping/distortion

- **Category:** Audio
- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Input` | Audio, Video | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Audio, Video | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [Compressor Skill](file:///packages/artifex-skills/skills/compressor/SKILL.md).

---

#### Delay / Echo (`Delay`)

Add repeating echo effect for audio and video

- **Category:** Audio
- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Input` | Audio, Video | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Audio, Video | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [Delay Skill](file:///packages/artifex-skills/skills/delay/SKILL.md).

---

#### Fade In / Fade Out (`AudioFade`)

Applies a configurable gain envelope for audio and video.

- **Category:** Audio
- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Input` | Audio, Video | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Audio, Video | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [AudioFade Skill](file:///packages/artifex-skills/skills/audio-fade/SKILL.md).

---

#### Audio Noise Gate (`NoiseGate`)

Silence background noise and hum below a certain volume threshold

- **Category:** Audio
- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Input` | Audio, Video | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Audio, Video | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [NoiseGate Skill](file:///packages/artifex-skills/skills/noise-gate/SKILL.md).

---

#### Parametric EQ (`ParametricEq`)

Boost or cut specific frequency ranges using biquad IIR filters

- **Category:** Audio
- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Input` | Audio, Video | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Audio, Video | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [ParametricEq Skill](file:///packages/artifex-skills/skills/parametric-eq/SKILL.md).

---

#### Reverb (`Reverb`)

Add room ambience and space to audio

- **Category:** Audio
- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Input` | Audio, Video | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Audio, Video | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [Reverb Skill](file:///packages/artifex-skills/skills/reverb/SKILL.md).

---

#### Blur (`Blur`)

Apply blur to a media

- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Input` | Image, SVG, Video, Lottie, GIF | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Image, Video, GIF | no |
- **Dynamic inputs:** enabled (Signal, Number)
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [Blur Skill](file:///packages/artifex-skills/skills/blur/SKILL.md).

---

#### Canvas Generator (`CanvasGenerator`)

Create blank canvases or custom gradients from scratch

- **Inputs:**
_none_
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Image | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [CanvasGenerator Skill](file:///packages/artifex-skills/skills/canvas-generator/SKILL.md).

---

#### Color Key (`ColorKey`)

Key out a color (chroma key) with spill suppression

- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Input` | Image, SVG, Video, Lottie, GIF | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Image, Video, GIF | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [ColorKey Skill](file:///packages/artifex-skills/skills/color-key/SKILL.md).

---

#### Compositor (`Compositor`)

Compose media layers using renderable inputs.

- **Inputs:**
_none_
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Video, Image | no |
- **Dynamic inputs:** enabled (Text, Image, Video, Audio, Caption, SVG, GIF, Lottie)
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [Compositor Skill](file:///packages/artifex-skills/skills/compositor/SKILL.md).

---

#### Corner Pin (`CornerPin`)

Four-point perspective warp

- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Input` | Image, Video, SVG, GIF, Lottie | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Warped` | Image, Video, GIF | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [CornerPin Skill](file:///packages/artifex-skills/skills/corner-pin/SKILL.md).

---

#### Crop (`Crop`)

Crop media using rectangle, path, or ellipse

- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Input` | Image, Video, SVG, GIF, Lottie | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Cropped` | Image, Video, GIF | no |
| `Rest` | Image, Video, GIF | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [Crop Skill](file:///packages/artifex-skills/skills/crop/SKILL.md).

---

#### Color Curves (`Curves`)

Map tonal range and color balance using monotonic spline curves

- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Input` | Image, SVG, Video, GIF, Lottie | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Image, SVG, Video, GIF, Lottie | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [Curves Skill](file:///packages/artifex-skills/skills/curves/SKILL.md).

---

#### Displacement Map (`DisplacementMap`)

Distort media using a displacement map texture

- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Input` | Image, SVG, Video, Lottie, GIF | yes |
| `Map` | Image, Video | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Image, Video, GIF | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [DisplacementMap Skill](file:///packages/artifex-skills/skills/displacement-map/SKILL.md).

---

#### Extract Frame (`ExtractFrame`)

Extract a single frame from a video, Lottie or GIF

- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Media` | Video, Lottie, GIF | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Frame` | Image | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [ExtractFrame Skill](file:///packages/artifex-skills/skills/extract-frame/SKILL.md).

---

#### Extract LUT (`ExtractLUT`)

Extract a 3D LUT from two frames

- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Source Frame` | Image | yes |
| `Graded Frame` | Image | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `LUT` | LUT | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [ExtractLUT Skill](file:///packages/artifex-skills/skills/extract-lut/SKILL.md).

---

#### Film Grain (`FilmGrain`)

Apply organic, cinematic film grain texture to media

- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Input` | Image, SVG, Video, Lottie, GIF | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Image, Video, GIF | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [FilmGrain Skill](file:///packages/artifex-skills/skills/film-grain/SKILL.md).

---

#### Motion Renderer (`HTMLVideoRender`)

Render HTML, CSS, and GSAP animations to video

- **Category:** Video
- **Terminal node:** produces a final renderable output
- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `HTML` | Text | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Video Result` | Video | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [HTMLVideoRender Skill](file:///packages/artifex-skills/skills/htmlvideo-render/SKILL.md).

---

#### Ken Burns (`KenBurns`)

Create a video using Ken Burns effect

- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Input` | Image, Video, SVG, GIF, Lottie | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Video | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [KenBurns Skill](file:///packages/artifex-skills/skills/ken-burns/SKILL.md).

---

#### Levels (`Levels`)

Adjust tonal range and color balance with input/output levels

- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Input` | Image, SVG, Video, GIF, Lottie | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Image, Video, GIF | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [Levels Skill](file:///packages/artifex-skills/skills/levels/SKILL.md).

---

#### Cut (`MediaCut`)

Cut video, audio, lottie or gif by specifying start and end times.

- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Media` | Video, Audio, Lottie, GIF | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Video, Audio, Lottie, GIF | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [MediaCut Skill](file:///packages/artifex-skills/skills/media-cut/SKILL.md).

---

#### Mesh Warp (`MeshWarp`)

Warp media using a grid of control points

- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Input` | Image, Video, SVG, GIF, Lottie | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Warped` | Image, Video, GIF | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [MeshWarp Skill](file:///packages/artifex-skills/skills/mesh-warp/SKILL.md).

---

#### Modulate (`Modulate`)

Apply Modulate adjustments to an image

- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Input` | Image, SVG, Video, Lottie, GIF | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Image, Video, GIF | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [Modulate Skill](file:///packages/artifex-skills/skills/modulate/SKILL.md).

---

#### Noise Generator (`NoiseGenerator`)

Generate procedural Perlin, Simplex, and Voronoi noise.

- **Inputs:**
_none_
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Image, Video | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [NoiseGenerator Skill](file:///packages/artifex-skills/skills/noise-generator/SKILL.md).

---

#### Paint (`Paint`)

Draw / Fill Mask on an media

- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Background` | Image, SVG, Video, Lottie, GIF | no |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Image, Video, GIF | no |
| `Mask` | Image | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [Paint Skill](file:///packages/artifex-skills/skills/paint/SKILL.md).

---

#### Resizer / Scaler (`ResizerScaler`)

Adjust aspect ratios, scale resolution, crop, and pad image/video assets.

- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Input` | Image, Video, SVG, GIF, Lottie | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Image, Video, GIF | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [ResizerScaler Skill](file:///packages/artifex-skills/skills/resizer-scaler/SKILL.md).

---

#### Stereo Panning (`StereoPanning`)

Balance audio output between left and right channels

- **Category:** Audio
- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Input` | Audio, Video | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Audio, Video | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [StereoPanning Skill](file:///packages/artifex-skills/skills/stereo-panning/SKILL.md).

---

#### Video to Audio (`VideoToAudio`)

Converts a video input to an audio output.

- **Category:** Audio
- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Input` | Video | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Audio | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [VideoToAudio Skill](file:///packages/artifex-skills/skills/video-to-audio/SKILL.md).

---

#### Vignette (`Vignette`)

Apply a classic vignette effect with dark corners to visual media

- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Input` | Image, SVG, Video, Lottie, GIF | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Image, Video, GIF | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [Vignette Skill](file:///packages/artifex-skills/skills/vignette/SKILL.md).

---

### AI

#### Audio Generator (`AudioGenerator`)

Generate high-quality audio or speech using AI.

- **Category:** Audio
- **Terminal node:** produces a final renderable output
- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Prompt` | Text | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Audio | no |
- **Dynamic inputs:** enabled (Audio, Image)
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [AudioGenerator Skill](file:///packages/artifex-skills/skills/audio-generator/SKILL.md).

---

#### Caption Generator (`CaptionGenerator`)

Generate captions for audio or video using AI

- **Category:** Audio
- **Terminal node:** produces a final renderable output
- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Input` | Audio, Video | yes |
| `Prompt` | Text | no |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Caption | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [CaptionGenerator Skill](file:///packages/artifex-skills/skills/caption-generator/SKILL.md).

---

#### Depth Map (`DepthMap`)

Generate a depth map from an image using AI

- **Category:** Image
- **Terminal node:** produces a final renderable output
- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Input` | Image | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Image | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [DepthMap Skill](file:///packages/artifex-skills/skills/depth-map/SKILL.md).

---

#### AI Edit Video (`VideoEdit`)

Edit an existing video using AI.

- **Category:** Video
- **Terminal node:** produces a final renderable output
- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Video` | Video | yes |
| `Prompt` | Text | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Video | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [VideoEdit Skill](file:///packages/artifex-skills/skills/video-edit/SKILL.md).

---

#### Extract Object (`ExtractObject`)

Segment and extract an object from an image using a prompt

- **Category:** Image
- **Terminal node:** produces a final renderable output
- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Image` | Image | yes |
| `Prompt` | Text | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Image | no |
| `Mask` | Image | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [ExtractObject Skill](file:///packages/artifex-skills/skills/extract-object/SKILL.md).

---

#### Motion Video Generator (`HTMLVideoGen`)

Prompt Agent to create animated motion videos

- **Category:** Video
- **Terminal node:** produces a final renderable output
- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Prompt` | Text | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `HTML Result` | Text | no |
| `Video Result` | Video | no |
- **Dynamic inputs:** enabled (Image, Video, SVG, Caption, Lottie)
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [HTMLVideoGen Skill](file:///packages/artifex-skills/skills/htmlvideo-gen/SKILL.md).

---

#### Image Generator (`ImageGen`)

Generate or edit an image using AI

- **Category:** Image
- **Terminal node:** produces a final renderable output
- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Prompt` | Text | yes |
| `Reference Image` | Image | no |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Image | no |
- **Dynamic inputs:** enabled (Image)
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [ImageGen Skill](file:///packages/artifex-skills/skills/image-gen/SKILL.md).

---

#### Lip Sync (`LipSync`)

Turns any avatar image into a talking video

- **Category:** Video
- **Terminal node:** produces a final renderable output
- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Avatar Image` | Image | yes |
| `Audio` | Audio | yes |
| `Prompt` | Text | no |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Video | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [LipSync Skill](file:///packages/artifex-skills/skills/lip-sync/SKILL.md).

---

#### LLM (`LLM`)

Prompt a large language model

- **Category:** Text
- **Terminal node:** produces a final renderable output
- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Prompt` | Text | yes |
| `System Prompt` | Text | no |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Text | no |
- **Dynamic inputs:** enabled (Image)
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [LLM Skill](file:///packages/artifex-skills/skills/llm/SKILL.md).

---

#### Lottie Generator (`LottieGen`)

Generate or Edit After Effect animations using an AI Agent.

- **Category:** Vector
- **Terminal node:** produces a final renderable output
- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Prompt` | Text | yes |
| `Reference Image` | Image | no |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Lottie | no |
- **Dynamic inputs:** enabled (Image)
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [LottieGen Skill](file:///packages/artifex-skills/skills/lottie-gen/SKILL.md).

---

#### Remove Background (`RemoveBackground`)

Remove the background from an image using AI

- **Category:** Image
- **Terminal node:** produces a final renderable output
- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Media` | Image | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Image | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [RemoveBackground Skill](file:///packages/artifex-skills/skills/remove-background/SKILL.md).

---

#### Smart Cut (`SmartCut`)

Cuts media to keep the parts where speech is detected.

- **Category:** Audio
- **Terminal node:** produces a final renderable output
- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Media` | Video, Audio | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Video, Audio | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [SmartCut Skill](file:///packages/artifex-skills/skills/smart-cut/SKILL.md).

---

#### SVG Generator (`SvgGen`)

Generate SVG vector graphics

- **Category:** Vector
- **Terminal node:** produces a final renderable output
- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Prompt` | Text | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | SVG | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [SvgGen Skill](file:///packages/artifex-skills/skills/svg-gen/SKILL.md).

---

#### Text to Speech (`TextToSpeech`)

Create speech from text

- **Category:** Audio
- **Terminal node:** produces a final renderable output
- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Prompt` | Text | yes |
| `Style Instructions` | Text | no |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Audio | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [TextToSpeech Skill](file:///packages/artifex-skills/skills/text-to-speech/SKILL.md).

---

#### AI Upscaler (`Upscaler`)

Upscale and enhance image or video assets using AI.

- **Category:** Media Enhancement
- **Terminal node:** produces a final renderable output
- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Input` | Image, Video | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Image, Video | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [Upscaler Skill](file:///packages/artifex-skills/skills/upscaler/SKILL.md).

---

#### Video Generator (`VideoGen`)

A video generation node.

- **Category:** Video
- **Terminal node:** produces a final renderable output
- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Prompt` | Text | yes |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Video | no |
- **Dynamic inputs:** enabled (Image, Video, Audio)
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [VideoGen Skill](file:///packages/artifex-skills/skills/video-gen/SKILL.md).

---

#### First to last frame video (`VideoGenFirstLastFrame`)

Generate videos using first and last frame images

- **Category:** Video
- **Terminal node:** produces a final renderable output
- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Prompt` | Text | yes |
| `First Frame` | Image | yes |
| `Last Frame` | Image | no |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Video | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [VideoGenFirstLastFrame Skill](file:///packages/artifex-skills/skills/video-gen-first-last-frame/SKILL.md).

---

#### Video to Music (`VideoToMusic`)

Analyzes your video’s to generate a frame-synced soundtrack in seconds

- **Category:** Audio
- **Terminal node:** produces a final renderable output
- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Video` | Video | yes |
| `Prompt` | Text | no |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Audio | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [VideoToMusic Skill](file:///packages/artifex-skills/skills/video-to-music/SKILL.md).

---

### Input/Output

#### Caption Builder (`CaptionEditor`)

Create captions manually in SRT format

- **Inputs:**
_none_
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Caption | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [CaptionEditor Skill](file:///packages/artifex-skills/skills/caption-editor/SKILL.md).

---

#### Export (`Export`)

An UI download / API output node

- **Terminal node:** produces a final renderable output
- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Input` | Text, Image, Video, Audio, SVG, LUT, Caption, Lottie, GIF | yes |
- **Outputs:**
_none_
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [Export Skill](file:///packages/artifex-skills/skills/export/SKILL.md).

---

#### Import (`Import`)

Upload your files

- **Inputs:**
_none_
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Audio, Image, Video, SVG, Caption, Lottie, LUT, GIF | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [Import Skill](file:///packages/artifex-skills/skills/import/SKILL.md).

---

#### Number (`Number`)

Number input node

- **Inputs:**
_none_
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Number | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [Number Skill](file:///packages/artifex-skills/skills/number/SKILL.md).

---

#### Recorder (`Recorder`)

Record your screen, camera and microphone

- **Inputs:**
_none_
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Screen` | Video | no |
| `Camera` | Video | no |
| `Mic` | Audio | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [Recorder Skill](file:///packages/artifex-skills/skills/recorder/SKILL.md).

---

#### Text (`Text`)

Text (prompt) input node

- **Inputs:**
_none_
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Text | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [Text Skill](file:///packages/artifex-skills/skills/text/SKILL.md).

---

### Utilities

#### Sticky Note (`Note`)

A sticky note

- **Inputs:**
_none_
- **Outputs:**
_none_
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [Note Skill](file:///packages/artifex-skills/skills/note/SKILL.md).

---

#### Preview (`Preview`)

Preview the output of a connected node

- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Input` | Video, Image, Text, Audio, SVG, GIF, Lottie, Signal | yes |
- **Outputs:**
_none_
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [Preview Skill](file:///packages/artifex-skills/skills/preview/SKILL.md).

---

#### Text Merger (`TextMerger`)

Merges connected texts.

- **Inputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Text` | Text | no |
| `Text 2` | Text | no |
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Merged Text` | Text | no |
- **Dynamic inputs:** enabled (Text)
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [TextMerger Skill](file:///packages/artifex-skills/skills/text-merger/SKILL.md).

---

### Signal

#### Procedural Signal (`ProceduralSignal`)

Create procedural Signals.

- **Inputs:**
_none_
- **Outputs:**
| Handle | Types | Required |
|--------|-------|----------|
| `Result` | Signal | no |
- **Dynamic inputs:** no
- **Dynamic outputs:** no

For detailed usage rules, config parameters, and examples for this node, see [ProceduralSignal Skill](file:///packages/artifex-skills/skills/procedural-signal/SKILL.md).

---

