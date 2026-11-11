# AutoClips

**Turn long videos into ready-to-post 9:16 shorts, on your own computer.**

[繁體中文](README.zh-TW.md) · [Download the latest version](https://github.com/acer1456/AutoClips/releases/latest)

AutoClips is a desktop app for macOS and Windows. Give it a long interview, podcast, talk or livestream and it finds the best moments, reframes each one to vertical around the speaker's face, adds styled captions, and exports finished clips for Shorts, Reels and TikTok.

Your videos never leave your computer. Decoding, face detection, transcription and export all run locally. The only data sent out is the **subtitle text**, and only when you use the AI features (highlight picking and translation).

> The interface is currently in Traditional Chinese.

```
Import  →  AI picks highlights  →  Edit  →  Export 1080×1920
```

## Features

- **Import** a local video (mp4, mov, mkv, webm). A subtitle file with the same name (.srt / .vtt) is picked up automatically. You can also paste a video link.
- **AI highlight picking.** An AI model reads the subtitles and picks the strongest moments. Four built-in styles (all-round, knowledge, emotion & story, quotable lines), or write your own instructions. Cut points snap to shot changes and pauses, so clips don't start mid-word.
- **Manual picking.** Prefer to choose yourself? Drag ranges on the full-video timeline, or search the subtitles for a keyword and mark in / out points.
- **Automatic vertical framing.** Faces are detected shot by shot: one speaker is centred, two speakers can be stacked top and bottom. Every crop can be dragged and resized in the editor.
- **A real video editor.** Phone-sized preview (with an optional Instagram Reels overlay), multi-track timeline, split, trim, ripple delete, undo / redo.
- **Captions that look exactly like the export.** Built-in caption styles plus your own presets, line-by-line or word-by-word highlighting, keyword colouring, per-line overrides. What you see in the preview is what gets burned in.
- **No subtitles? No problem.** Videos without captions are transcribed on your computer with whisper.cpp, using the GPU where available (Metal on Apple Silicon, Vulkan on Windows). Choose a model size from tiny to large-v3.
- **Re-break and realign captions.** Rewrite or paste your own transcript; every character is re-aligned to the audio for the narrow 9:16 layout.
- **Translation.** Translate captions into any language and show the original, the translation, or both.
- **Overlays.** Title cards, images, animated name and text cards, and an end-card video.
- **Export** at 1080×1920 with hardware encoding when available, loudness normalisation, burned-in captions and an `.srt` file. Export several clips at once.
- **Updates itself.** AutoClips checks for new versions at launch and installs them with one click. Every update is signed.

## Download

Get the newest version from the **[Releases page](https://github.com/acer1456/AutoClips/releases/latest)**:

| Your computer | File to download |
|---|---|
| Mac with Apple Silicon (M1 or newer) | `AutoClips_<version>_aarch64.dmg` |
| Mac with an Intel processor | `AutoClips_<version>_x64.dmg` |
| Windows 10 / 11 (64-bit) | `AutoClips_<version>_x64-setup.exe` |

Not sure which Mac you have? Apple menu › About This Mac: "Chip: Apple M…" means Apple Silicon.

The `.tar.gz`, `.sig` and `latest.json` files are used by the built-in updater. You don't need to download them.

### First launch

AutoClips is not yet signed with an Apple or Microsoft developer certificate, so the system warns you the first time:

- **macOS:** open the `.dmg` and drag AutoClips into **Applications**. If macOS refuses to open it, go to **System Settings › Privacy & Security**, scroll down and click **Open Anyway** (on macOS 14 or earlier you can also right-click the app › **Open**). If it says the app "is damaged", run this once in Terminal: `xattr -cr /Applications/AutoClips.app`
- **Windows:** if SmartScreen appears, click **More info › Run anyway**.

You only need to do this once.

## Getting started

1. Open **設定與更新 (Settings & Updates)** and paste your [OpenRouter](https://openrouter.ai/keys) API key. It is stored in the system keychain. OpenRouter is pay-as-you-go, and the cost depends on the model you pick.
2. To import from a link, click **檢查環境 (Check environment)** once. It downloads the yt-dlp tool.
3. Click **新專案 (New project)** and drop in a video or paste a link.
4. Choose a highlight style and how many clips you want, then start the AI analysis (or pick the moments yourself).
5. Open a clip in the editor to fine-tune framing, captions and overlays.
6. Export. Clips are saved to your Downloads folder by default.

Manual picking, editing, transcription and export work without an API key.

## Requirements

| | macOS | Windows |
|---|---|---|
| System | macOS 12.3 or later, Apple Silicon or Intel | Windows 10 (1803+) or 11, 64-bit |
| Disk | about 300 MB for the app, plus space for your projects | same |
| AI features | OpenRouter API key | same |
| Internet | AI features, link import, model downloads and updates | same |

ffmpeg and whisper.cpp come with the app, so there is nothing else to install.

## Privacy

- Video and audio are never uploaded.
- Subtitle text goes to the OpenRouter model you choose, only when you run AI analysis or translation.
- Other network use: update checks (this GitHub repository), downloading yt-dlp (its GitHub releases), downloading whisper models (Hugging Face), and the video sites you import from.
- No accounts, no analytics.

## Content rights

You are responsible for having the rights to the videos you import and the clips you publish. Downloading from some websites may be against their terms of service.

## Third-party software

AutoClips includes or downloads the following open-source software:

- [FFmpeg](https://ffmpeg.org) (GPL), shipped as separate executables. Static builds by [Martin Riedl](https://ffmpeg.martin-riedl.de) (macOS) and [BtbN](https://github.com/BtbN/FFmpeg-Builds) (Windows). Source code: <https://ffmpeg.org/download.html>
- [whisper.cpp](https://github.com/ggml-org/whisper.cpp) (MIT) for speech recognition
- [yt-dlp](https://github.com/yt-dlp/yt-dlp) (Unlicense), downloaded on demand
- [YuNet](https://github.com/opencv/opencv_zoo/tree/main/models/face_detection_yunet) face detection model (MIT), run with [ONNX Runtime Web](https://onnxruntime.ai) (MIT)
- [Noto Sans TC](https://fonts.google.com/noto/specimen/Noto+Sans+TC) (SIL Open Font License)
- [Tauri](https://tauri.app) (MIT / Apache-2.0)
