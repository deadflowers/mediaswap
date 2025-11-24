# Mediaswap

**Quickly convert audio, image, and video files via terminal or right-click menu.**

Mediaswap is a robust wrapper designed to bring the power of **FFmpeg** and **ImageMagick** to your Ubuntu/GNOME environment. It operates as a single master CLI tool with optional **Zenity** GUI dialogs.

There are no new heavy programs to open or learn. **Mediaswap** integrates seamlessly into your existing workflow.

### What it does

  * **Images:** Convert `.heic` and `.raw` to `.png`, `.webp`, `.avif`, or `.jpg`. Create **iconsets**, apply **bevels**, add **drop-shadows**, **remove backgrounds**, or generate **ASCII** art.
  * **Video:** Convert proprietary formats to **VP9**, **AV1**, or **H.264**. Includes smart defaults for modern web standards.
  * **Audio:** **Rip audio** tracks from video files (bit-perfect copy) or transcode to **Opus**, **FLAC**, **AAC**, or **WAV** without upsampling.
  * **Workflow:** Batch process multiple files instantly. If you forget a flag, the GUI pops up to help you.

-----

### Dependencies

Mediaswap relies on standard, powerful Linux tools:

  * `ffmpeg`
  * `imagemagick`
  * `zenity` (for GUI dialogs)
  * `file`
  * `chafa` (optional, for ASCII art)
  * `exiftool` (optional, for metadata scrubbing)
  * `zip` (optional, for iconset packing)

Install them on Ubuntu/Debian:

```bash
sudo apt install ffmpeg imagemagick zenity file chafa jp2a exiftool zip
```

-----

### Installation

1.  **Clone the repository:**

    ```bash
    git clone https://github.com/deadflowers/mediaswap.git
    cd mediaswap
    ```

2.  **Install the core script:**
    Move the master script to your binary path and create the short alias `m`.

    ```bash
    mkdir -p ~/.local/bin
    mv mediaswap ~/.local/bin/
    chmod +x ~/.local/bin/mediaswap
    ln -s ~/.local/bin/mediaswap ~/.local/bin/m
    ```

3.  **Install Nautilus/Nemo integration:**
    Move the wrapper scripts to the file manager scripts folder.

    ```bash
    mkdir -p ~/.local/share/nautilus/scripts/
    mv "Convert Image" "Convert Audio" "Convert Video" ~/.local/share/nautilus/scripts/
    chmod +x ~/.local/share/nautilus/scripts/*
    ```

4.  **Restart Nautilus** (optional, if scripts don't appear immediately):

    ```bash
    nautilus -q
    ```

-----

### Usage

#### 1\. The Command Line (CLI)

The core command is `mediaswap`. The syntax follows a simple pattern: `mediaswap [category] [format] [file]`.

**Examples:**

```bash
# Convert a video to WebM (VP9)
mediaswap video vp9 input.mp4

# Convert an image to JPG
mediaswap image jpg photo.png

# Convert audio to FLAC
mediaswap audio flac recording.wav
```

#### 2\. The Short CLI (`m`)
Faster and easier? We include a shorthand alias `m` mapped to the main script. The shortened CLI: 

```bash
# Convert video to VP9
m v vp9 [inputfile]

# Convert image to JPG
m i jpg [inputfile]

# Rip audio from video (no transcoding)
m a rip [inputfile]
```

#### 3\. The Hybrid Workflow (GUI Fallback)

If you forget the specific action argument, just type the category. Mediaswap will launch a **Zenity GUI** to let you select the format interactively.

```bash
m v video.mp4
# Opens a dialog asking: "Convert to: VP9, AV1, H264...?"
```

#### 4\. Context Menu

Right-click any file in Nautilus:

1.  Go to **Scripts**.
2.  Select **Convert Image**, **Convert Audio**, or **Convert Video**.
3.  A dialog appears with options.

-----

### Features & Commands

#### 🖼️ Image (`m i`)

Handles conversion, effects, and web optimization.

  * **webp**: Convert to WebP (default quality 75).
  * **avif**: Convert to AVIF (high efficiency).
  * **png / jpg**: Standard conversions.
  * **animwebp**: Combine multiple selected images into an animated WebP.
  * **bevel**: Add a transparent 3D raised border.
  * **rappleshot**: Add a floating "glass" shadow effect (great for screenshots).
  * **bgremove**: Remove background (white/black detection with threshold slider).
  * **iconset**: Generate a folder containing standard PWA/Favicon sizes + manifests.
  * **ascii**: Generate a text file with ASCII art representation.
  * **strip**: Remove EXIF/Metadata without re-encoding.

#### 🎧 Audio (`m a`)

Convert audio with smarter transcoding and ripping.

  * **opus**: Convert to Opus (Default: 256k).
  * **ogg**: Convert to Ogg (Default: 256k).
  * **m4a**: Convert to AAC/M4A (Default: 320k).
  * **mp3**: Convert to MP3 (Default: 320k).
  * **flac**: Lossless conversion.
  * **wav**: Convert to PCM WAV (16-bit).
  * **rip**: Extract audio stream from video **without re-encoding** (copy stream). If the container format doesn't match, it prompts to transcode.

#### 🎥 Video (`m v`)

Focuses on modern web standards and editing formats. Convert and transcode with ease.

  * **rip**: extract audio track without transcode, attepts bit for bit copy.
  * **lossless**: Convert to Lossless VP9.
  * **vp9**: Convert to WebM VP9 (Best balance of size/quality).
  * **vp8**, **webm**: Convert to WebM VP8 (default for webm mode).
  * **av1**: Convert to WebM AV1 (High efficiency, slower encode).
  * **h264**: Convert to MP4 H.264 (Universal compatibility).
  * **h265**: Convert to MP4 HEVC.
  * **mov**: Convert to MOV (ProRes or high-bitrate H.264).
  * **vid2webp**: Convert video clip to high-quality animated WebP.
 

-----

### Command Reference Table

| Type | Command | Available Actions & Formats | Notes |
| :--- | :--- | :--- | :--- |
| **Image** | `m i` | `webp`, `avif`, `png`, `jpg`, `animwebp`, `iconset`, `bevel`, `rappleshot`, `bgremove`, `ascii`, `strip` | `animwebp` creates an animated WebP from multiple selected images. `strip` removes metadata. |
| **Audio** | `m a` | `opus`, `m4a`, `mp3`, `flac`, `wav`, `ogg`, `rip` | `rip` extracts the audio stream from a video file without re-encoding. `wav` defaults to PCM 16-bit. |
| **Video** | `m v` | `vp9`, `vp8`, `av1`, `h264`, `h265`, `webm`, `mov`, `lossless`, `vid2webp`, `rip` | `vid2webp` converts video input to an animated WebP. `rip` is a shortcut to extract audio. Supports `--gpu`. |
 
-----

#### Iconset Generation

Running `m i iconset logo.png` creates a folder structure ready for web deployment:

```text
logo_iconset/
├── 16.png
├── 32.png
...
├── favicon.ico
├── manifest.json
└── meta.html
```

---

### Demo Videos


<!-- looping WebP file -->

```html
<figure>
  <img src="https://github.com/deadflowers/mediaswap/blob/main/demo/example-animation.webp?raw=true" alt="Demo Animation" />
  <figcaption>Demo animation </figcaption>
</figure>
```


#### YouTube Video Preview

<!-- YouTube video preview and in-page playback -->

```html
<figure>
  <iframe width="560" height="315" src="https://www.youtube.com/embed/xyz" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  <figcaption>Video demo on YouTube by @raykooyenga</figcaption>
</figure>
```

---

### Credits

Mediaswap is an open-source utility created by **Ray Kooyenga**. It was developed on **Ubuntu 25.04** with **GNOME 48**.
