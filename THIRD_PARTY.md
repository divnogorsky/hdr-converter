# Third-party components

HDR Converter installs or uses the components below. Each stays under its own licence. Components marked
**downloaded** are fetched by the setup wizard from their original source at a pinned version (checked against
sha256); they are not redistributed by HDR Converter. Components marked **included** ship inside the installer.

> Licences as published by each project at the pinned version; check the links for the authoritative text.

## Models

| Component | What it is | Licence | How |
|---|---|---|---|
| [LTX-2.5](https://huggingface.co/Lightricks/LTX-2.5) (22B distilled transformer bf16 / int8, video and audio VAE) | the video model by Lightricks | [LTX-2 Community License](https://github.com/Lightricks/LTX-2/blob/main/LICENSE-2_x) | downloaded |
| [LTX-2.5 SDR→HDR IC-LoRA](https://huggingface.co/Lightricks/LTX-2.5-22b-IC-LoRA-SDR-To-HDR) (+ scene embeddings) | the SDR→HDR adapter by Lightricks | [LTX-2 Community License](https://github.com/Lightricks/LTX-2/blob/main/LICENSE-2_x) | downloaded |

The LTX-2 Community License is free for organisations with annual revenue under $10M; above that a commercial
licence from Lightricks is required. It is accepted on Hugging Face before the download.

## Runtime

| Component | What it is | Licence | How |
|---|---|---|---|
| [ComfyUI](https://github.com/Comfy-Org/ComfyUI) v0.35.0 portable (incl. its Python 3.13 and PyTorch) | runs the model | GPL-3.0 (PyTorch: BSD-3-Clause) | downloaded |
| [ComfyUI-LTXVideo](https://github.com/Lightricks/ComfyUI-LTXVideo) | LTX nodes for ComfyUI | as stated in its repository (LTX-2 Community License) | downloaded |
| HDR Converter ComfyUI nodes | 16-bit image sequence loader, EXR writer | GPL-3.0 — source code and licence text are included in the install folder, in the `custom_nodes` folder of the bundled ComfyUI | included |
| [Python](https://www.python.org/) 3.12 | runs the app and the setup wizard | PSF License | downloaded (app); included (setup wizard) |
| [Qt for Python / PySide6](https://doc.qt.io/qtforpython/) | user interface | LGPL-3.0 | downloaded (app); included (setup wizard) |
| [OpenColorIO](https://opencolorio.org/) | colour management | BSD-3-Clause | downloaded |
| [ACES studio config](https://github.com/AcademySoftwareFoundation/OpenColorIO-Config-ACES) v2.2.0 (ACES 1.3, OCIO 2.4) | colour config, exported from OpenColorIO's built-in copy | BSD-3-Clause | created at install |
| [OpenEXR](https://openexr.com/) | EXR files | BSD-3-Clause | downloaded |
| [OpenImageIO](https://openimageio.org/) | image I/O | Apache-2.0 | downloaded |
| [OpenCV](https://opencv.org/) (opencv-python) | image I/O | Apache-2.0 | downloaded |
| [NumPy](https://numpy.org/) | arrays | BSD-3-Clause | downloaded |
| [PyOpenGL](https://pyopengl.sourceforge.net/) | viewer | BSD-3-Clause | downloaded |
| [imageio-ffmpeg](https://github.com/imageio/imageio-ffmpeg) with its FFmpeg build | video decoding | BSD-2-Clause (wrapper); FFmpeg build GPL-3.0 | downloaded |
| [diffusers](https://github.com/huggingface/diffusers), [timm](https://github.com/huggingface/pytorch-image-models) | required by ComfyUI-LTXVideo | Apache-2.0 | downloaded |
| [colour-science](https://www.colour-science.org/) | colour primaries | BSD-3-Clause | downloaded |
| [ninja](https://ninja-build.org/) | build helper required by ComfyUI-LTXVideo | Apache-2.0 | downloaded |

## Installer

| Component | What it is | Licence | How |
|---|---|---|---|
| [Inno Setup](https://jrsoftware.org/isinfo.php) | the setup bootstrapper | Inno Setup License | included |
| [PyInstaller](https://pyinstaller.org/) bootloader | runs the setup wizard | GPL-2.0 with bootloader exception | included |
| [7-Zip](https://www.7-zip.org/) 7zr.exe | unpacks the ComfyUI archive | GNU LGPL | included |
