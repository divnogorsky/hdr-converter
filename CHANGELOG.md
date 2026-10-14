# Changelog

All notable changes to HDR Converter. Versions follow [semver](https://semver.org/); pre-releases are marked `-beta`.

## [0.2.0-beta] — 2026-10-14

HDR plus passes for compositing, from the same approved shot.

- New: **passes for compositing**: metric depth (`depth.Z`, metres, steady over the shot), camera-space normals
  (`N.x/y/z`), motion vectors (`forward.u/v`, `backward.u/v`), clip / synth masks. One choice on the main screen:
  *HDR*, *HDR + comp passes* or *Custom*. The models are added in Components when needed.
- New: **hero matte** (`matte.A`): a soft alpha of the shot's main subject - hair, glow, smoke included - from
  Lightricks' Alpha Gen IC-LoRA on the same LTX-2.5 model. The model picks the subject. Optional component
  (1.2 GB); the LTX-2.5 text encoder (14 GB) is needed once and can be removed afterwards.
- New: **recover crushed shadows** (on by default): where the source is crushed to black the detail comes from
  LTX at the source's local exposure; everything brighter than code 25 stays the source bit for bit.
- New: **8-bit clean-up**. For 8-bit sources the steps between codes are filled before the HDR, every value within
  half a code of the source (re-quantised it is the source exactly): the HDR's shadows come out about a third closer
  to a 10-bit original, motion vectors 15 % closer. 10-bit and higher sources are never touched. Advanced → on/off.
- New: **source check** when a video is added (bit depth, chroma, frame rate, colour tags, duplicates, soft or
  upscaled footage) and a **quality check** after the conversion (exposure, colour, seams, flicker) under the timeline.
- New: **output layout**: *One EXR* (every layer in one file a frame, as in 0.1) or *Folder per layer* (`hdr/`,
  `depth/`, `normals/`, `vectors/`, `matte/`, `clip/`, `synth/`, files `<name>_<layer>_1001.exr`, the same channel
  names).
- Weaker machines: HDR first, then passes and the hero matte, with progress for every long step; a busy video card
  (a browser on an 8 GB card) slows a step down instead of pausing it forever; the disk is checked before the GPU
  work starts; closing the window during a conversion stops it cleanly and gives the memory back.
- Re-runs are fast: finished steps (HDR chunks, passes, hero matte) are kept in the work folder next to the app and
  reused for the same source and settings; the status says what was reused. A change of seed, model or input
  transform computes the HDR again. Advanced → *Compute everything again* empties a shot's work folder first.
- New: EXR metadata (fps, colour ID, model, seed, source) readable in Nuke.
- With DWAA compression the data layers (depth, normals, vectors, mattes) are kept lossless: a second part of the
  same EXR, or ZIP in their own folders. DWA would otherwise change them.
- Fixed: choosing EXR compression *NONE* stopped the conversion at the write step.
- The source tree no longer looks for a Nuke installation (OpenColorIO's built-in ACES 1.3 config). No Nuke or
  other software is needed for any of it.

## [0.1.4-beta] — 2026-10-09

- Fixed: the app closed right after start with "Unable to load EGL library" on machines where other software had
  set `PYOPENGL_PLATFORM` or `XDG_SESSION_TYPE`. The app now ignores these settings for its own viewer; nothing in
  the system is changed.

## [0.1.3-beta] — 2026-10-09

First public beta.

- SDR → HDR EXR conversion of approved AI video with LTX-2.5 and the SDR→HDR IC-LoRA (Lightricks), locally.
- Native resolution up to 4K on a 10 GB GPU: overlapping chunks, exposure-matched seams.
- Outside the highlights the frame matches the source; resolution, fps, frame count and numbering unchanged.
- ACEScg / ACEScct / sRGB linear OpenEXR (half or float), numbered from 1001, JSON with every parameter, author and
  version in the EXR metadata.
- Viewer: before/after divider, exposure −6…+6 EV, ACES and Un-tone-mapped views, clipped-area overlay, playback.
- Queue for folders of videos; time estimate before starting; resumes after a crash; waits while the GPU or memory
  are busy with other programs.
- Setup wizard: install everything, reuse the models of an existing ComfyUI, or install into it; Hugging Face access
  check; resumable, sha256-verified downloads; self-test with progress; uninstall that keeps your own files.
- Runs on machines below the recommended RAM with a warning; starts on laptops with Intel/AMD graphics.
- Update notice: checks this repository for a newer version at startup, in the background — silent when offline;
  can be turned off in About, beta versions shown only to beta installs or on request.
