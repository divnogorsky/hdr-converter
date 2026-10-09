# Requirements

HDR Converter is in beta and has been tested on two machines so far. Everything below is measured on them; what
has not been measured yet is marked as such.

## Tested machines

| | Desktop | Laptop |
|---|---|---|
| GPU | NVIDIA GeForce RTX 3080, 10 GB VRAM | NVIDIA GPU with 8 GB VRAM (plus built-in graphics) |
| RAM | 95 GB | 32 GB |
| Windows | 11, 64-bit | 11, 64-bit |
| NVIDIA driver | 610.88 | not recorded |
| Result | everything below | installation, self-test, app start and a video conversion: OK (see below) |

## Measured on the desktop (RTX 3080 10 GB, 95 GB RAM)

| Shot | Model | Time |
|---|---|---|
| 1920×1080, 121 frames (5 s at 24 fps) | Full (bf16) | 28 min (2 chunks of 65 frames) |
| 3840×2160, 145 frames (6 s at 24 fps) | Full (bf16) | 5 h 6 min (12 chunks of 17 frames, 19–39 min each, 25 min on average) |
| 3840×2160, 145 frames | Fast (int8) | 2 h 36 min |
| Self-test (9 frames, 384×216) | Full (bf16) | 159 s the first time, 54–70 s when the model is already in the disk cache |

Peak video memory on 4K: 9.5–10 GB of the 10 GB card. Memory used by the app while the Full model is loaded:
about 52 GB.

## Measured on the laptop (8 GB VRAM, 32 GB RAM)

- Self-test (9 frames, 384×216) with the **Full (bf16)** model: **passed in 91 s**, with the low-memory warning.
- The app installs and starts, and a video converted successfully.
- Not measured yet: processing times, the Fast (int8) model.

On machines below the tested desktop (less VRAM or RAM) conversion works but takes longer than the times above.

## What you need

| | Tested and working | Notes |
|---|---|---|
| Windows | 10 / 11, 64-bit | tested on 11 |
| GPU | NVIDIA, 10 GB VRAM (desktop); 8 GB VRAM (laptop) | with less than 10 GB conversion takes longer; times not measured yet |
| NVIDIA driver | with CUDA 13.0 support (R580 or newer) | the bundled PyTorch is a CUDA 13.0 build |
| RAM | 95 GB (desktop); 32 GB (laptop) | the Full model wants about 52 GB of free memory to load without paging; with less RAM the app warns and still runs, slower — how much slower on real shots is not measured yet |
| Disk — install everything | about 48 GB, +20 GB with the optional Fast model | plus about 2 GB temporarily during installation |
| Disk — work space | a 4K, 145-frame shot: about 19 GB of temporary files + 3.1 GB of EXR output | temporary files stay in the app's cache folder |
| Internet | for installation only (about 45 GB of models) | the update check at startup is optional |

## Notes

- **Less RAM than recommended:** the app warns and still runs; it can be much slower or run out of memory on long
  or 4K shots. The Fast model needs less memory.
- **Other GPU work:** while converting, the app waits if another ComfyUI or other programs hold the GPU or memory,
  and continues by itself when they are free.
- **Laptops with two GPUs:** the app's window can run on the built-in graphics; the conversion itself runs on the
  NVIDIA GPU.
