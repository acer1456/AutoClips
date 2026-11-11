# AutoClips

**在自己的電腦上，把長影片變成可以直接發布的 9:16 短影音。**

[English](README.md) · [下載最新版](https://github.com/acer1456/AutoClips/releases/latest)

AutoClips 是 macOS 與 Windows 的桌面軟體。丟進一支長的訪談、Podcast、演講或直播，它會挑出最精彩的段落，依講者的臉自動轉成直式構圖、加上有設計感的字幕，輸出成可以直接上傳 Shorts、Reels、TikTok 的短片。

影片不會離開你的電腦。解碼、人臉偵測、語音轉錄、匯出全部在本機完成。唯一會送出去的是**字幕文字**，而且只在你使用 AI 功能（挑精華、翻譯）時才會送。

```
匯入  →  AI 挑精華  →  編輯  →  匯出 1080×1920
```

## 功能

- **匯入**本機影片（mp4、mov、mkv、webm），同名的字幕檔（.srt / .vtt）會自動帶入；也可以直接貼影片連結。
- **AI 挑精華**：AI 讀字幕，挑出最有看點的段落。內建四種風格（全類型、知識乾貨、情緒與故事、金句），也能寫自己的指示。切點會自動對齊分鏡與停頓，不會切在話講到一半。
- **手動挑選**：想自己決定也可以。在整支影片的時間軸上拖出範圍，或搜尋字幕關鍵字，按 I / O 標記進出點。
- **自動直式構圖**：逐個鏡頭偵測人臉，單人置中、兩人可上下分割。每個裁切框都能在編輯器裡拖曳、縮放。
- **真正的剪輯器**：手機尺寸預覽（可疊上 IG Reels 介面確認版面）、多軌時間軸、分割、修剪、漣漪刪除、復原 / 重做。
- **預覽什麼樣，輸出就什麼樣的字幕**：內建多種字幕樣式，也能存自己的預設；整句或逐字高亮、重點字上色、單句個別調整。
- **沒有字幕也能用**：沒字幕的影片會在你的電腦上用 whisper.cpp 轉成逐字稿，有 GPU 就用 GPU（Apple Silicon 用 Metal、Windows 用 Vulkan）。模型從 tiny 到 large-v3 自己選。
- **重新斷句與對齊**：改寫或貼上自己的逐字稿，每個字都會重新對齊聲音，適合 9:16 的窄版面。
- **字幕翻譯**：把字幕翻成任何語言，可以只顯示原文、只顯示譯文，或雙語並列。
- **疊層**：標題卡、圖片、有進出場動畫的名牌與字卡、片尾影片。
- **匯出** 1080×1920，能用硬體編碼就用，自動調整音量、燒錄字幕並附上 `.srt` 檔，可一次匯出多支。
- **自動更新**：每次啟動會檢查新版，一鍵安裝。每個更新都有數位簽章。

## 下載

到 **[Releases 頁面](https://github.com/acer1456/AutoClips/releases/latest)** 下載最新版：

| 你的電腦 | 要下載的檔案 |
|---|---|
| Apple Silicon 的 Mac（M1 以後） | `AutoClips_<版本>_aarch64.dmg` |
| Intel 處理器的 Mac | `AutoClips_<版本>_x64.dmg` |
| Windows 10 / 11（64 位元） | `AutoClips_<版本>_x64-setup.exe` |

不確定是哪種 Mac？點左上角蘋果選單 › 關於這台 Mac，「晶片：Apple M…」就是 Apple Silicon。

`.tar.gz`、`.sig`、`latest.json` 是給軟體內建更新用的，不用下載。

### 第一次開啟

AutoClips 目前還沒有 Apple 與 Microsoft 的開發者憑證，所以第一次開啟時系統會跳出警告：

- **macOS**：打開 `.dmg`，把 AutoClips 拖進「應用程式」。如果 macOS 不讓你打開，到 **系統設定 › 隱私權與安全性**，往下捲按 **強制打開**（macOS 14 以前也可以對 App 按右鍵 › **打開**）。如果顯示「已損毀」，在「終端機」執行一次：`xattr -cr /Applications/AutoClips.app`
- **Windows**：如果出現 SmartScreen，按 **其他資訊 › 仍要執行**。

這個步驟只需要做一次。

## 開始使用

1. 打開 **設定與更新**，貼上你的 [OpenRouter](https://openrouter.ai/keys) API Key（存在系統金鑰鏈裡）。OpenRouter 用多少付多少，費用依你選的模型而定。
2. 要用連結匯入的話，先按一次 **檢查環境**，它會下載 yt-dlp。
3. 按 **新專案**，把影片拖進來或貼上連結。
4. 選好挑精華的風格和片段數量，開始 AI 分析（或自己手動挑）。
5. 打開片段進編輯器，微調構圖、字幕和疊層。
6. 匯出。預設存到「下載」資料夾。

手動挑選、編輯、轉錄、匯出都不需要 API Key。

## 系統需求

| | macOS | Windows |
|---|---|---|
| 作業系統 | macOS 12.3 以上，Apple Silicon 或 Intel | Windows 10（1803 以上）或 11，64 位元 |
| 硬碟空間 | 軟體約 300 MB，另需專案空間 | 同左 |
| AI 功能 | OpenRouter API Key | 同左 |
| 網路 | AI 功能、連結匯入、下載模型與更新時需要 | 同左 |

ffmpeg 與 whisper.cpp 都已包在軟體裡，不用另外安裝任何東西。

## 隱私

- 影片和聲音永遠不會上傳。
- 字幕文字只在你執行 AI 分析或翻譯時，送到你選的 OpenRouter 模型。
- 其他網路連線：檢查更新（本 GitHub 頁面）、下載 yt-dlp（它的 GitHub Release）、下載 whisper 模型（Hugging Face），以及你匯入影片的網站。
- 不用註冊帳號，也不收集使用數據。

## 內容權利

你匯入的影片與發布的片段，請確認你有使用權利。從部分網站下載影片可能違反該網站的服務條款。

## 第三方軟體

AutoClips 內含或會下載以下開源軟體：

- [FFmpeg](https://ffmpeg.org)（GPL），以獨立執行檔形式附上。macOS 版由 [Martin Riedl](https://ffmpeg.martin-riedl.de) 編譯，Windows 版由 [BtbN](https://github.com/BtbN/FFmpeg-Builds) 編譯。原始碼：<https://ffmpeg.org/download.html>
- [whisper.cpp](https://github.com/ggml-org/whisper.cpp)（MIT），語音辨識
- [yt-dlp](https://github.com/yt-dlp/yt-dlp)（Unlicense），需要時才下載
- [YuNet](https://github.com/opencv/opencv_zoo/tree/main/models/face_detection_yunet) 人臉偵測模型（MIT），以 [ONNX Runtime Web](https://onnxruntime.ai)（MIT）執行
- [Noto Sans TC](https://fonts.google.com/noto/specimen/Noto+Sans+TC)（SIL Open Font License）
- [Tauri](https://tauri.app)（MIT / Apache-2.0）
