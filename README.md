**The fastest way to transform your audio, video, and image files**

### Desktop non-app[](#desktop-non-app)

[MediaSwap](https://deadflowers.github.io/mediaswap/) is a robust wrapper designed to bring the power of **FFmpeg** and **ImageMagick** to your desktop. The GUI is familiar because it’s yours: the shell and file manager you are already using. If you can copy, cut, paste with your mouse, you already know how to use MediaSwap to bulk transform your media files.

---

* **Images:** Convert `.heic` and `.raw` to `.png`, `.webp`, `.avif`, or `.jpg`. Create **icons** for your web app, apply **bevels**, **drop-shadows**, **remove backgrounds**, animate and more.
* **Video:** Convert proprietary formats to **VP9**, **AV1**, **VP8**. Smart defaults for current best practice.
* **Audio:** Convert **WAV** to **FLAC**, or **AAC**, **Opus**, **MP3**. Remix, remaster, rip bit perfect audio from video files create spectrogram charts, normalize voice notes for Whisper AI.
* **Workflow:** Right click on or more files in your file manager, choose what you want ot do. Or use the CLI. Convert a directory of MP4 video files to royalty free AV1 WebM? Easy as `m v av1 *mp4`.

---

Essentially a **Zenity** powered non-app, there’s no big programs to load or learn. MediaSwap attaches to your shell, integrating seamlessly into your environment, and organically into your workflow.

So natural and intuitive your great grandfather could figure out remastering his Glenn Miller Orchestra records in 3 minutes. The shell extension is composed of wrapper scripts in your GTK system you interact with via normal menus plus some new dialogues and slider elements that extend functionality with a native feel.

These components pass commands back to a master CLI app. That’s right, MediaSwap has a smart terminal mode. And yes you can absolutely use on your remote server with no desktop. Or even the console on your Android phone.

shut up ray! 🤬

no joke i do it all the time 😂

---

### Usage[](#usage)

#### 1\. Context Menu[](#1-context-menu)

Right-click any file in Nautilus:

1. Go to **Scripts**.
2. Select **Convert Image**, **Convert Audio**, or **Convert Video**.
3. A dialog appears with interactive choices.

#### 2\. The Hybrid Workflow (GUI Fallback)[](#2-the-hybrid-workflow-gui-fallback)

Launch Mediaswap interactive GUI from console.

```
m v video.mp4
# Opens a dialog asking: "Convert to: VP9, AV1, H264...?"
```

#### 3\. The Command Line (CLI)[](#3-the-command-line-cli)

The core command is `mediaswap`. The syntax follows a simple pattern: `mediaswap [category] [function] [input file]`.

**Examples:**

```
# Convert a video to WebM (VP9)
mediaswap video vp9 input.mp4

# Convert an image to JPG
mediaswap image jpg photo.png

# Convert audio to FLAC
mediaswap audio flac recording.wav
```

#### 4\. The Short CLI (`m`)[](#4-the-short-cli-m)

Faster and easier? We include a shorthand alias `m` mapped to the main script. The shortened CLI:

```
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

---

### Features & Commands[](#features--commands)

#### 🖼️ Image (`m i`)[](#️-image-m-i)

Handles conversion, effects, and web optimization.

* **webp**: Convert to WebP (default quality 75).
* **avif**: Convert to AVIF (high efficiency).
* **png / jpg**: Standard conversions.
* *\*animate*: Combine multiple selected images into an animated WebP.
* **bevel**: Add a transparent 3D raised border.
* **shadow**: Add a floating “glass” shadow effect (great for screenshots).
* **bg**: Remove background (white/black detection with threshold slider).
* **icons**: Generate a folder containing standard PWA/Favicon sizes + manifests.
* **ascii**: Generate a text file with ASCII art representation.
* **strip**: Remove EXIF/Metadata without re-encoding.

#### 🎧 Audio (`m a`)[](#-audio-m-a)

Convert audio with smarter transcoding and ripping.

* **opus**: Convert to Opus (Default: 256k).
* **ogg**: Convert to Ogg (Default: 256k).
* **m4a**: Convert to AAC/M4A (Default: 320k).
* **mp3**: Convert to MP3 (Default: 320k).
* **flac**: Lossless conversion.
* **wav**: Convert to PCM WAV (16-bit).
* **norm**: Normalize a voice recording for transcription (optimize for Whisper).
* **rip**: Extract audio stream from video **without re-encoding** (copy stream). If the container format doesn’t match, it prompts to transcode.

#### 🎥 Video (`m v`)[](#-video-m-v)

Focuses on modern web standards and editing formats. Convert and transcode with ease.

* **rip**: extract audio track without transcode, attepts bit for bit copy.
* **vp9**, **webm**: Convert to WebM VP9 (Best balance of size/quality, default foor webm mode).

#### 🎥 Video (`m v`)[](#-video-m-v-1)

Focuses on modern web standards and editing formats. Convert and transcode with ease.

* **rip**: extract audio track without transcode, attepts bit for bit copy.
* **vp9**, **webm**: Convert to WebM VP9 (Best balance of size/quality, default foor webm mode).
* **vp8**: Convert to WebM VP8.
* **av1**: Convert to WebM AV1 (High efficiency, slower encode).
* **h264**: Convert to MP4 H.264 (Universal compatibility).
* **h265**: Convert to MP4 HEVC.
* **mov**: Convert to MOV (ProRes or high-bitrate H.264).
* **webp**: Convert video clip to high-quality animated WebP.

---

Not residing in memory and being only around 500 lines, it’s like it’s not even there. When functions are requested menus and dialogues are instantiated and close when task is complete. You are always a couple clicks away from converting 100s of movies to the latest video codec, web friendly formats, extracting bit perfect audio streams, converting the format of those tracks, optimizing all your web graphics, adding shadows, making GIF animations using WebP. Use mediaswap to handle bulk conversions or single file be it sound, videos, static or animated images.

### CLI experience[](#cli-experience)

You can launch and interact with MediaSwap starting from the CLI, like a hybrid. Or you can never use the GUI or even know it exists as the console app has the same powers. And like mouse click based experience, MediaSwap on a terminal is fast, fun, intuitive. It had to be or you would just use FFMpeg directly!

The objective is to give console users a simpler, faster way to call on the most common functions. The power of FFMpeg extended to all experience levels including novice user who should be able to rip bit perfect audio, migrate their videos to av1, while knowing almost nothing about ffmpeg. The commands should be

* too simple to confuse
* too sensible to forget
* too short to typo
* with a help guide you can figure out in under a minute

### Use Cases[](#use-cases)

Right click a media file or batch of files and convert PNG to WebP, or batch of MP4 to WebM, optimize a batch of voice notes for upload to transcription like Whisper AI by downsampling and normalizing or de-noise filtering. Select all your WebM music videos and extract the audio streams to Matroska containers. Drag select those and apply sound effects like clarity, or stereo widening.

Give your screenshots a nice 3d hover shadow effect Make your selfie an ascii text for fun. Generate all website and web app favicon icons fom a single starter image in a click. Resizing images is so easy it’s absurd, by dimensions or percent. Convert movies to av1 video codec in a click and adjust slider for more compression control.

Problematic meeting notes? Fix noisy ones and even repair those too quiet by boost certain ranges, before encode as 1 channel 16bit 16kHz PCM WAV; to the liking of Whisper for more ccurate transcription and subtitle generation. Want to see what your files soudn like so you know which ones need which kind of filter or cleanup? Try asking mediaswap for a PNG image spectrogram for each audio file.

---

### Dependencies[](#dependencies)

Mediaswap relies on standard, powerful Linux tools:

* `ffmpeg`
* `imagemagick`
* `zenity` (for GUI dialogs)
* `file`
* `chafa` (optional, for ASCII art)
* `exiftool` (optional, for metadata scrubbing)
* `zip` (optional, for iconset packing)

Install them on Ubuntu/Debian:

```
sudo apt install ffmpeg imagemagick zenity file chafa jp2a exiftool zip
```

---

### Installation[](#installation)

1. **Clone the repository:**
   
   ```
   git clone https://github.com/deadflowers/mediaswap.git
   cd mediaswap
   ```

2. **Install the core script:** Move the master script to your binary path and create the short alias `m`.
   
   ```
   mkdir -p ~/.local/bin
   mv mediaswap ~/.local/bin/
   chmod +x ~/.local/bin/mediaswap
   ln -s ~/.local/bin/mediaswap ~/.local/bin/m
   ```

3. **Install Nautilus/Nemo integration:** Move the wrapper scripts to the file manager scripts folder.
   
   ```
   mkdir -p ~/.local/share/nautilus/scripts/
   mv "Convert Image" "Convert Audio" "Convert Video" ~/.local/share/nautilus/scripts/
   chmod +x ~/.local/share/nautilus/scripts/*
   ```

4. **Restart Nautilus** (optional, if scripts don’t appear immediately):
   
   ```
   nautilus -q
   ```

---


### Command Reference Table

| Type | Command | Available Actions & Formats | Notes |
| :--- | :--- | :--- | :--- |
| **Image** | `m i` | `webp`, `avif`, `png`, `jpg`, `animate`, `icons`, `bevel`, `rappleshot`, `bgremove`, `ascii`, `strip` | `animate` creates an animated WebP from multiple selected images. `strip` removes metadata. |
| **Audio** | `m a` | `opus`, `m4a`, `mp3`, `flac`, `wav`, `ogg`, `norm`, `rip` | `rip` extracts the audio stream from a video file without re-encoding. `norm` optimize a recording for transcription |
| **Video** | `m v` | `vp9`, `vp8`, `av1`, `h264`, `h265`, `webm`, `mov`, `mp4`, `webp`, `rip` | `webp` converts video input to an animated WebP. `rip` is a shortcut to extract audio. Supports `--gpu`. |
 
---

#### Favicon / Web Icon Generation[](#favicon--web-icon-generation)

Running `m i icons logo.png` creates a folder structure ready for web deployment:

```
logo_iconset/
├── 16.png
├── 32.png
...
├── favicon.ico
├── manifest.json
└── meta.html
```

---

### Demo Videos[](#demo-videos)

```
<figure>
  <img src="https://github.com/deadflowers/mediaswap/blob/main/demo/example-animation.webp?raw=true" alt="Demo Animation" />
  <figcaption>Demo animation </figcaption>
</figure>
```

#### YouTube Video Preview[](#youtube-video-preview)

```
<figure>
  <iframe width="560" height="315" src="https://www.youtube.com/embed/xyz" frameborder="0" allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
  <figcaption>Video demo on YouTube by @raykooyenga</figcaption>
</figure>
```

---

### Credits[](#credits)

Mediaswap is an open-source utility created by **Ray Kooyenga**. 
<!-- **Ubuntu 25.04** with **GNOME 48** -->.
