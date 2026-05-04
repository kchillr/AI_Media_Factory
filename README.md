# AI_Media_Factory
Pollination API driven media creator
# ⚡ AI Media Factory – Pollinations AI Powered

A Windows desktop application for generating **text**, **images**, **videos**, and **audio** using the [Pollinations AI](https://pollinations.ai/) API. Built with Python and [CustomTkinter](https://github.com/TomSchimansky/CustomTkinter) for a modern, rounded-corner dark UI.

---

## Features

- **Text generation** – Chat/completion responses from OpenAI, Claude, Gemini, Grok, Mistral, Deepseek, and more
- **Image generation** – Flux, GPT Image, Seedream, Kontext, NanoBanana, Grok Imagine, and more
- **Video generation** – Seedance, Veo, Wan, Grok Video, LTX-2, Nova Reel, and more
- **Audio generation** – Text-to-speech (ElevenLabs), music (ElevenMusic, ACE-Step), and transcription (Whisper, Scribe)
- **Built-in media player** – Images and text display inline; video and audio play via embedded VLC
- **Modern rounded UI** – Sleek dark theme with rounded corners powered by CustomTkinter
- **Conditional Voice control** – The Voice dropdown only appears when an audio TTS model is selected
- **Clipboard support** – Copy images as bitmap, text as plain text, or file paths for video/audio
- **Persistent settings** – API key, last-used model, size, voice, and save directory are remembered across sessions

---

## Standalone EXE (Recommended)

The easiest way to use AI Media Factory is the pre-built standalone executable.

### Requirements

- Windows 10 or later (64-bit)
- A [Pollinations API key](https://enter.pollinations.ai)

### Getting Started

1. Run **`AIMediaFactory.exe`**
2. On first launch, the display area will show a warning that no API key is configured
3. Go to **File ▾ → Settings** and paste your Pollinations API key
4. Click **Save**
5. Select a model from the **Model** dropdown, choose a **Size** (for image/video), type a prompt, and click **Generate**

> The EXE bundles all dependencies including VLC — no additional software is required.

---

## Running from Source

### Prerequisites

| Dependency | Purpose |
|---|---|
| **Python 3.10+** | Runtime |
| **VLC Media Player** | Video/audio playback (installed to `C:\Program Files\VideoLAN\VLC`) |

### Python Packages

Install all dependencies:

```
pip install -r requirements.txt
```

| Package | Purpose |
|---|---|
| `requests` | HTTP calls to the Pollinations API |
| `Pillow` | Image loading, resizing, and clipboard conversion |
| `python-vlc` | VLC bindings for video/audio playback |
| `pywin32` | Windows clipboard access (`win32clipboard`) |
| `customtkinter` | Modern rounded-corner dark UI widgets |
| `pyinstaller` | Building the standalone EXE (development only) |

> **Note:** `tkinter` ships with the standard Windows Python installer. If you used a minimal install, you may need to add it.

### Run

```
cd PictureFactory
python PictureFactory.py
```

> **Note:** The UI uses `customtkinter` — no C# or WinForms overlay is required. All rounded corners and modern styling are provided natively by the `customtkinter` library.

---

## Building the EXE

A `PictureFactory.spec` is included that bundles VLC DLLs and plugins into a single-file executable:

```
pyinstaller PictureFactory.spec --distpath dist --workpath build --noconfirm
```

The output is written to `dist\AIMediaFactory.exe`.

---

## Configuration

Settings are stored in **`config.json`** next to the executable (or next to `PictureFactory.py` when running from source). The file is created automatically on first run.

| Key | Description |
|---|---|
| `api_key` | Your Pollinations API key |
| `last_save_path` | Last used directory for Save As |
| `model` | Last selected model name |
| `size` | Last selected image/video resolution |
| `voice` | Last selected voice for TTS audio models |

---

## Usage Guide

### Generating Text

1. Select any **TEXT MODELS** entry from the **Model** dropdown (e.g. *OpenAI*, *Claude*, *Gemini*, *Grok*)
2. Type your prompt or question in the text box at the bottom
3. Click **Generate**
4. The response appears in a scrollable text area in the preview pane
5. Use **📋 Copy** to copy the full response to clipboard, or **File → Save As** to save as a `.txt` file

### Generating Images

1. Select an **IMAGE MODELS** entry (e.g. *Flux*, *GPT Image*, *Seedream*, *Kontext*)
2. Choose a resolution from the **Size** dropdown — 480p (854×480), 720p (1280×720), or 1080p (1920×1080)
3. Type your prompt and click **Generate**
4. The image appears in the preview area
5. Use **📋 Copy** to copy the image as bitmap (paste directly into any app), or **File → Save As** to save as JPG/PNG/BMP

### Generating Videos

1. Select a **VIDEO MODELS** entry (e.g. *Seedance*, *Veo*, *Wan*, *Grok Video Pro*)
2. Choose a resolution and type your prompt
3. Click **Generate** — video generation can take 30 seconds to several minutes
4. The video loops automatically; use **⏸ Pause / ▶ Play** to control playback
5. **File → Save As** saves as `.mp4`

### Generating Audio

1. Select an **AUDIO MODELS** entry:
   - **ElevenLabs TTS** – natural speech from text; the **Voice** dropdown automatically appears when this model is selected
   - **ElevenMusic** – studio-grade music from a text description
   - **ACE-Step** – open-source music generation with optional lyrics
   - **Whisper** / **Scribe** – speech-to-text transcription (provide audio description in prompt)
2. For TTS, select a **Voice** from the Voice dropdown (only visible when ElevenLabs TTS is selected)
3. Type your text or music description and click **Generate**
4. Audio plays automatically; **File → Save As** saves as `.mp3`

### Saving Output

**File → Save As** saves the current output with the correct file type:

| Content Type | Formats |
|---|---|
| Text | `.txt` |
| Image | `.jpg`, `.png`, `.bmp` |
| Video | `.mp4` |
| Audio | `.mp3` |

### Copying to Clipboard

Click **📋 Copy**:

| Content Type | What is copied |
|---|---|
| Text | Full response text |
| Image | Bitmap data (paste directly into any application) |
| Video | Temporary file path |
| Audio | Temporary file path |

---

## Available Models

### ✍️ Text Models

| Display Name | API ID |
|---|---|
| OpenAI | `openai` |
| OpenAI Fast | `openai-fast` |
| OpenAI Large | `openai-large` |
| Claude | `claude` |
| Claude Fast | `claude-fast` |
| Claude Large | `claude-large` |
| Claude Legacy | `claude-legacy` |
| Gemini | `gemini` |
| Gemini Fast | `gemini-fast` |
| Gemini Large | `gemini-large` |
| Gemini Legacy | `gemini-legacy` |
| Gemini Flash Lite 3.1 | `gemini-flash-lite-3.1` |
| Gemini Search | `gemini-search` |
| Grok | `grok` |
| Grok Large | `grok-large` |
| Mistral | `mistral` |
| Mistral Large | `mistral-large` |
| Qwen Coder | `qwen-coder` |
| Qwen Coder Large | `qwen-coder-large` |
| Qwen Large | `qwen-large` |
| Qwen Vision | `qwen-vision` |
| Qwen Safety | `qwen-safety` |
| Perplexity Fast | `perplexity-fast` |
| Perplexity Reasoning | `perplexity-reasoning` |
| Deepseek | `deepseek` |
| Kimi | `kimi` |
| Nova | `nova` |
| Nova Fast | `nova-fast` |
| GLM | `glm` |
| MiniMax | `minimax` |
| Polly | `polly` |
| OpenAI Audio | `openai-audio` |
| OpenAI Audio Large | `openai-audio-large` |
| Midijourney | `midijourney` |
| Midijourney Large | `midijourney-large` |

### 🖼️ Image Models

| Display Name | API ID |
|---|---|
| Flux | `flux` |
| Z-Image | `zimage` |
| GPT Image | `gptimage` |
| GPT Image Large | `gptimage-large` |
| NanoBanana | `nanobanana` |
| NanoBanana 2 | `nanobanana-2` |
| NanoBanana Pro | `nanobanana-pro` |
| Seedream | `seedream` |
| Seedream 5 | `seedream5` |
| Seedream Pro | `seedream-pro` |
| Wan Image | `wan-image` |
| Wan Image Pro | `wan-image-pro` |
| Grok Imagine | `grok-imagine` |
| Grok Imagine Pro | `grok-imagine-pro` |
| P-Image | `p-image` |
| P-Image Edit | `p-image-edit` |
| Kontext | `kontext` |
| Klein | `klein` |
| Qwen Image | `qwen-image` |
| Nova Canvas | `nova-canvas` |

### 🎬 Video Models

| Display Name | API ID |
|---|---|
| Veo | `veo` |
| Seedance | `seedance` |
| Seedance Pro | `seedance-pro` |
| Wan | `wan` |
| Wan Fast | `wan-fast` |
| Grok Video Pro | `grok-video-pro` |
| Nova Reel | `nova-reel` |
| LTX-2 | `ltx-2` |
| P-Video | `p-video` |

### 🔊 Audio Models

| Display Name | API ID | Type |
|---|---|---|
| ElevenLabs TTS | `elevenlabs` | Text-to-speech |
| ElevenMusic | `elevenmusic` | Music generation |
| ACE-Step | `acestep` | Music generation |
| Whisper | `whisper` | Transcription |
| Scribe | `scribe` | Transcription |

### 🎙️ Voices (TTS)

Alloy · Echo · Fable · Onyx · Nova · Shimmer · Ash · Ballad · Coral · Sage · Verse · Rachel · Domi · Bella · Elli · Charlotte · Dorothy · Sarah · Emily · Lily · Matilda · Adam · Antoni · Arnold · Josh · Sam · Daniel · Charlie · James · Fin · Callum · Liam · George · Brian · Bill

---

## License

This project is provided as-is for personal use.
