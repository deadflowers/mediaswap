# Mediaswap

**Quickly convert audio, image, and video files via right-click menus or use the CLI.**

### Desktop non-app
Mediaswap is a robust wrapper designed to bring the power of **FFmpeg** and **ImageMagick** to your Ubuntu/GNOME desktop. The GUI is familiar because it's your shell and file manager. 

Essentially a **Zenity** powered non-app that attaches itself to your shell, integrating seamlessly into your environment, and organically into your workflow. 

---

  * **Images:** Convert `.heic` and `.raw` to `.png`, `.webp`, `.avif`, or `.jpg`. Create **icons** for your web app or site, apply **bevels**, add **drop-shadows**, **remove backgrounds**, or generate **ASCII** art.
  * **Video:** Convert proprietary formats to **VP9**, **AV1**, or **VP8**. Includes smart defaults for modern web standards.
  * **Audio:** **Rip audio** tracks from video files (bit-perfect copy) or transcode to **Opus**, **FLAC**, **AAC**, or **WAV**.
  * **Workflow:** Right click, batch process multiple files instantly, or use the CLI terminal version. Convert a directory of h264 MP4 video files to royalty free AV1 video in WebM containers? Easy as `m v av1 *mp4`.
-----

### Usage

#### 1\. Context Menu

Right-click any file in Nautilus:

1.  Go to **Scripts**.
2.  Select **Convert Image**, **Convert Audio**, or **Convert Video**.
3.  A dialog appears with interactive choices.

#### 2\. The Hybrid Workflow (GUI Fallback)

Launch Mediaswap interactive GUI from console.

```bash
m v video.mp4
# Opens a dialog asking: "Convert to: VP9, AV1, H264...?"
```

#### 3\. The Command Line (CLI)

The core command is `mediaswap`. The syntax follows a simple pattern: `mediaswap [category] [function] [input file]`.

**Examples:**

```bash
# Convert a video to WebM (VP9)
mediaswap video vp9 input.mp4

# Convert an image to JPG
mediaswap image jpg photo.png

# Convert audio to FLAC
mediaswap audio flac recording.wav
```

#### 4\. The Short CLI (`m`)
Faster and easier? We include a shorthand alias `m` mapped to the main script. The shortened CLI: 

```bash
# Convert video to VP9
m v vp9 [inputfile]

# Convert image to JPG
m i jpg [inputfile]

# Rip audio from video (no transcoding)
m a rip [inputfile]
```
The output file is the same or a variation of the input filename and the new extension. so you dont have to type things twice or have a confusing process for handling batches of files. In fact batches wold be this easy:

```
# Bulk convert a directory of wav files to opus
m a opus *.wav

# Rip audio streams in bulk
m a rip my-videos/*

# Shrink your website graphics
m i webp *png

# make a animated webp gif-style
m i animate travel-photos/*png

```

-----

### Features & Commands

#### 🖼️ Image (`m i`)

Handles conversion, effects, and web optimization.

  * **webp**: Convert to WebP (default quality 75).
  * **avif**: Convert to AVIF (high efficiency).
  * **png / jpg**: Standard conversions.
  * **animate*: Combine multiple selected images into an animated WebP.
  * **bevel**: Add a transparent 3D raised border.
  * **rappleshot**: Add a floating "glass" shadow effect (great for screenshots).
  * **bgremove**: Remove background (white/black detection with threshold slider).
  * **icons**: Generate a folder containing standard PWA/Favicon sizes + manifests.
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
  * **norm**: Normalize a voice recording for transcription (optimize for Whisper).
  * **rip**: Extract audio stream from video **without re-encoding** (copy stream). If the container format doesn't match, it prompts to transcode.

#### 🎥 Video (`m v`)

Focuses on modern web standards and editing formats. Convert and transcode with ease.

  * **rip**: extract audio track without transcode, attepts bit for bit copy.
  * **vp9**, **webm**: Convert to WebM VP9 (Best balance of size/quality, default foor webm mode).

#### 🎥 Video (`m v`)

Focuses on modern web standards 
and editing formats. Convert and transcode with ease.

  * **rip**: extract audio track without transcode, attepts bit for bit copy.
  * **vp9**, **webm**: Convert to WebM VP9 (Best balance of size/quality, default foor webm mode).
  * **vp8**: Convert to WebM VP8.
  * **av1**: Convert to WebM AV1 (High efficiency, slower encode).
  * **h264**: Convert to MP4 H.264 (Universal compatibility).
  * **h265**: Convert to MP4 HEVC.
  * **mov**: Convert to MOV (ProRes or high-bitrate H.264).
  * **webp**: Convert video clip to high-quality animated WebP.
 
-----

Not residing in memory and being only around 500 lines, it's like it's not even there. When functions are requested menus and dialogues are instantiated and close when task is complete. You are always a couple clicks away from converting 100s of movies to the latest video codec, web friendly formats, extracting bit perfect audio streams, converting the format of those tracks, optimizing all your web graphics, adding shadows, making GIF animations using WebP. Use mediaswap to handle bulk conversions or single file be it sound, videos, static or animated images.

### CLI experience
You can launch and interact with MediaSwap starting from the CLI, like a hybrid. Or you can never use the GUI or even know it exists as the console app has the same powers. And like mouse click based experience, MediaSwap on a terminal is fast, fun, intuitive. It had to be or you would just use FFMpeg directly! 

The objective is to give console users a simpler, faster way to call on the most common functions. The power of FFMpeg extended to all experience levels including novice user who should be able to rip bit perfect audio, migrate their videos to av1, while knowing almost nothing about ffmpeg. The commands should be
- too simple to confuse
- too sensible to forget
- too short to typo
- with a help guide you can figure out in under a minute

### What it does
Right click a media file or batch of files and convert PNG to WebP, or batch of MP4 to WebM, optimize a batch of voice notes for upload to transcription like Whisper AI by downsampling and normalizing or de-noise filtering. Select all your WebM music videos and extract the audio streams to Matroska containers. Drag select those and apply sound effects like clarity, or stereo widening.

Give your screenshots a nice 3d hover shadow effect Make your selfie an ascii text for fun. Generate all website and web app favicon icons fom a single starter image in a click. Resizing images is so easy it's absurd, by dimensions or percent. Convert movies to av1 video codec in a click and adjust slider for more compression control. 

Problematic meeting notes? Fix noisy ones and even repair those too quiet by boost certain ranges, before encode as 1 channel 16bit 16kHz PCM WAV; to the liking of Whisper for more ccurate transcription and subtitle generation. Want to see what your files soudn like so you know which ones need which kind of filter or cleanup? Try asking mediaswap for a PNG image spectrogram for each audio file.



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

### Command Reference Table

| Type | Command | Available Actions & Formats | Notes |
| :--- | :--- | :--- | :--- |
| **Image** | `m i` | `webp`, `avif`, `png`, `jpg`, `animate`, `icons`, `bevel`, `rappleshot`, `bgremove`, `ascii`, `strip` | `animate` creates an animated WebP from multiple selected images. `strip` removes metadata. |
| **Audio** | `m a` | `opus`, `m4a`, `mp3`, `flac`, `wav`, `ogg`, `norm`, `rip` | `rip` extracts the audio stream from a video file without re-encoding. `norm` optimize a recording for transcription |
| **Video** | `m v` | `vp9`, `vp8`, `av1`, `h264`, `h265`, `webm`, `mov`, `mp4`, `webp`, `rip` | `webp` converts video input to an animated WebP. `rip` is a shortcut to extract audio. Supports `--gpu`. |
 
-----

#### Favicon / Web Icon Generation

Running `m i icons logo.png` creates a folder structure ready for web deployment:

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
