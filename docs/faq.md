# FAQ

**Does anything leave my machine?**
No. Conversion runs locally. The installer downloads ComfyUI, Python packages and the models from their original
sources; the app may check this repository for a newer version (it can be turned off). Your footage is never uploaded.

**Will it change my approved shot?**
Outside the highlights the frame matches the source; resolution, fps, frame count and frame numbering stay the same.
Only clipped and near-white areas (fire, lamps, sky) are rebuilt, so they keep shape and colour when you pull the
exposure down in grading. Because those areas are rebuilt, they can look slightly different from the source at 0 EV.

**What does it output?**
OpenEXR frames (16-bit half float, ZIP), ACEScg by default (ACEScct or sRGB linear optionally), numbered from 1001 and
named after the source, plus a JSON with every parameter. The app and author are written into the EXR metadata.

**Which inputs work?**
SDR video (8- or 10-bit, Rec.709) as .mp4, .mov, .mxf, .mkv or .m4v, at its native resolution up to 4K. A folder of
videos can be queued.

**Why so big a download?**
The full LTX-2.5 22B model is about 42 GB. If you already have it in ComfyUI, choose *Use the models from my ComfyUI*
and nothing is downloaded twice.

**Full or Fast model?**
Full (bf16) is the default and gives the best quality. Fast (int8, optional) needs less memory and is quicker on 4K.

**Can I use my existing ComfyUI?**
Yes — either read its models (nothing in it changes) or, for experienced users, install into it after a compatibility
check. See [install.md](install.md).

**Why does my antivirus or SmartScreen warn about the installer?**
It is new and not code-signed yet. Check the sha256 against the release page — see
[install.md](install.md#2-windows-smartscreen-and-antivirus).

**Is it free? What about the LTX licence?**
The app is free for personal and commercial use ([LICENSE.md](../LICENSE.md)). The LTX models are under the
LTX-2 Community License — free for organisations under $10M annual revenue, otherwise a commercial licence from
Lightricks is needed. See [THIRD_PARTY.md](../THIRD_PARTY.md).
