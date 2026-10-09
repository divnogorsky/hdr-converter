# Installing HDR Converter

## 1. Download and check the file

Download `HDRConverterSetup-<version>.exe` from [Releases](https://github.com/divnogorsky/hdr-converter/releases).
Each release lists the file's sha256. Check that your download matches it (PowerShell, in the download folder):

```powershell
Get-FileHash .\HDRConverterSetup-0.1.3.exe -Algorithm SHA256
```

The `Hash` it prints must equal the sha256 on the release page. If it does not, delete the file and download it again.

## 2. Windows SmartScreen and antivirus

The installer is not code-signed yet, so on first run Windows SmartScreen may say *"Windows protected your PC"*.
Click **More info** → **Run anyway**.

Some antivirus programs flag new, unsigned installers by heuristics (a "generic" verdict, not a specific virus) —
mostly because the file is new and unknown to them. Check the sha256 as above; if it matches the release, the file is
the one published here. You can also upload it to [VirusTotal](https://www.virustotal.com/) and report a false
positive to your antivirus vendor. No administrator rights are needed, and the setup does not change system settings.

## 3. Choose how to install

The wizard offers three options:

- **Install everything** — recommended if you don't have ComfyUI. Installs its own ComfyUI, the nodes, the models and
  the app into one folder (about 49 GB; +20 GB with the optional fast model).
- **Use the models from my ComfyUI** — recommended if you already have ComfyUI with the LTX-2.5 models. Installs its
  own small, separate ComfyUI (about 5 GB) and reads your models where they are — nothing is copied or changed. Only
  missing models are downloaded, into the HDR Converter folder or your models folder (your choice).
- **Use my ComfyUI** — for experienced users. Adds the HDR Converter nodes and packages to your ComfyUI after a
  compatibility check (ComfyUI ≥ 0.32, Python 3.13, CUDA 13 build, the tested ComfyUI-LTXVideo version). Each change
  needs your consent; if anything doesn't fit, the wizard offers the option above instead.

Pick a folder with Latin letters and no spaces (default `C:\HDRConverter`). The wizard then checks the GPU, driver,
memory and disk space before anything is downloaded.

## 4. Access to the models on Hugging Face

The LTX models are free but gated: Hugging Face asks you to accept the licence once and to use a token.

1. Sign in to [Hugging Face](https://huggingface.co/) (or create a free account).
2. Open both model pages and click **"Agree and access repository"** on each (access is granted right away):
   - https://huggingface.co/Lightricks/LTX-2.5
   - https://huggingface.co/Lightricks/LTX-2.5-22b-IC-LoRA-SDR-To-HDR
3. Create a token: https://huggingface.co/settings/tokens/new?tokenType=read — type **Read**, any name. Copy it.
4. Paste it into the wizard and press **Check access** — every model should show "access granted".

The token is used only for this installation; it is not saved and not written to any log. If all models are already
on the machine, no token is needed.

## 5. Install, self-test, start

Press **Install**. About 45 GB of models download and verify themselves (sha256); if the connection drops, run the
installer again — it continues where it stopped and does not download finished files again.

When it is done, run the **self-test** on the last screen: it converts a tiny built-in clip with the real pipeline and
checks the EXR. Then start HDR Converter from the Start menu or the desktop shortcut.

## If something goes wrong

- Installation log: `install.log` in the install folder (e.g. `C:\HDRConverter\install.log`).
- If the app does not start: `app\logs\crash.log` in the install folder.

Open an [issue](https://github.com/divnogorsky/hdr-converter/issues) and attach the relevant part of the log. The
logs do not contain your Hugging Face token; still check that nothing private is in what you paste (e.g. folder names
of your projects).

## Uninstall

Windows Settings → Apps → **HDR Converter** → Uninstall (or Start menu → HDR Converter → Uninstall HDR Converter).
It removes only what the installer put there. You decide whether to keep the downloaded models; your own ComfyUI and
your own models are never touched.
