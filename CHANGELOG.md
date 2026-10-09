# Changelog

All notable changes to HDR Converter. Versions follow [semver](https://semver.org/); pre-releases are marked `-beta`.

## [0.1.3-beta] — unreleased

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
