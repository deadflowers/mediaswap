# Mediaswap

Quickly convert audio, image, and video files in the console or context menu.

Mediaswap is a wrapper designed to bring the power of **FFmpeg** and **ImageMagick** tools to your Ubuntu right-click menu, and provides its own minimal GUI through **Zenity** elements. This allows you to perform powerful tasks quickly and easily. No new programs to remember and open, **Mediaswap** integrates seamlessly into your environment.

With Mediaswap, you can:

* Convert high-efficiency, low-portability image formats like `.heic` to `.png`, `.webp`, or `.jpeg`.
* Convert images to fun ASCII art, apply beveled edges, or add hover-shadow effects.
* Convert **MPEG** videos to **VP8**-encoded **WebM** files, or even transcode **VP8** in a **WebM** container to **VP9**.
* Extract audio from videos, such as ripping high-quality audio from YouTube music videos, without unnecessary transcoding that degrades quality.
* Convert voice notes, like **WAV**, to **FLAC** or **Opus** formats.
* Generate all the necessary icon sizes for your Progressive Web App, Chrome Extension, or website from a single image.
* Batch process multiple files at once, right from your file manager, with just a few clicks.

Mediaswap makes all of this possible with minimal setup and ease of use.

---

### Dependencies

Mediaswap requires the following dependencies:

* **FFmpeg**
* **ImageMagick** (`imagemagick` package)
* **Zenity** (for GUI dialogs)
* **JP2A** or **Chafa** (for image-to-ASCII conversion)

Ensure these packages are installed for Mediaswap to function correctly.

---

### Installation

1. Clone this repository:

   ```bash
   git clone https://github.com/deadflowers/mediaswap.git
   cd mediaswap
   ```

2. Install the core script in `~/.local/bin` and create a symlink for easy execution:

   ```bash
   mv mediaswap ~/.local/bin/mediaswap
   ln -s ~/.local/bin/mediaswap ~/.local/bin/m
   ```

3. Make the wrapper scripts executable:

   ```bash
   chmod +x ~/.local/nautilus/scripts/*
   ```

4. The core script (`mediaswap`) is now available for execution via `m` in the terminal, and the three wrapper scripts (Convert Video, Convert Image, Convert Audio) will appear in your right-click context menu.

---

### Usage

#### Command Line

Mediaswap is primarily a command-line tool, but it integrates with Nautilus for quick access via the context menu.

To convert an **MP4** file to **VP9**:

```bash
mediaswap video vp9 [file]
```

Where `[file]` is the input file.

**Shortened version**:
You can also use the default shortcut `m`:

```bash
m v vp9 [file]
```

If you forget the `vp9` part and just type:

```bash
m v [file]
```

Mediaswap will prompt you with a Zenity dialog, allowing you to choose the desired format via a GUI. This provides a seamless console + GUI workflow.

---

### Mediaswap Structure

Mediaswap consists of:

* The core script (`mediaswap`) located in `~/.local/bin/`
* Three wrapper scripts for the right-click menu:

  * **Convert Video**
  * **Convert Image**
  * **Convert Audio**

These scripts are placed in the `~/.local/nautilus/scripts/` directory and are made executable with `chmod +x`.

---

### Image Commands

The image section of Mediaswap allows you to convert and manipulate images in various formats. In addition to converting to formats like **AVIF**, you can also apply special effects, generate icons, and remove metadata.

Here are the available image commands:

* **webp**: Convert to **WebP**
* **png**: Convert to **PNG**
* **jpg**: Convert to **JPG**
* **bevel**: Add transparent bevel to the image
* **rappleshot**: Add shadow (Rappleshot effect)
* **bgremove**: Remove background (select a color)
* **iconset**: Generate an **Iconset** folder with multiple sizes
* **ascii**: Convert to **ASCII** (using Chafa)
* **strip**: Scrub metadata (keeps the same format)

**Example command:**

```bash
m i webp example.jpg
```

This command would convert the `example.jpg` image into a `example.webp`.

---

### Audio Commands

Mediaswap offers flexible audio conversion options, allowing you to convert between several formats and even extract audio from video files. The `rip` command can be used to extract audio from video files without unnecessary transcoding.

Available audio formats and actions include:

* **mp3**: Convert to **MP3**
* **m4a**: Convert to **M4A**
* **flac**: Convert to **FLAC**
* **wav**: Convert to **WAV**
* **opus**: Convert to **Opus**
* **rip**: Extract audio from a video file (no re-encoding)

**Example command to rip audio from a video:**

```bash
m a rip example.mp4
```

This command would extract audio from the `example.mp4` file, saving it in its original format (without transcoding).

---

### Video Commands

Mediaswap supports video format conversion and provides some flexibility with **WebM** files as a container. By default, **WebM** will use **VP8** encoding, but you can specify other encodings (like **VP9** or **AV1**) when converting videos.

Available video formats and actions include:

* **vp8**: Convert to **VP8** (WebM)
* **vp9**: Convert to **VP9** (WebM)
* **av1**: Convert to **AV1** (WebM)
* **webm**: Convert to **WebM** (default format: VP8)
* **mp4**: Convert to **MP4**
* **prores**: Convert to **ProRes**
* **h264**: Convert to **H.264**
* **h265**: Convert to **H.265**
* **rip**: Extract audio from a video file (no re-encoding)
  
---

### Example Scenarios



* **Convert Video**:
  Convert an **MP4** file to **WebM (VP9)**:

  ```bash
  m v vp9 example.mp4
  ```

* **Convert Audio**:
  Convert an **WAV** file to **OPUS**:

  ```bash
  m a opus example.wav
  ```

* **Convert Image**:
  Convert an **HEIC** image to **WEBP**:

  ```bash
  m i webp example.heic
  ```

---

### Command Overview

| Type      | Command Format        | Example Command        | Output Format(s)                                                                                        |
| --------- | --------------------- | ---------------------- | ------------------------------------------------------------------------------------------------------- |
| **Audio** | `m a [format] [file]` | `m a mp3 example.wav`  | `.mp3`, `.m4a`, `.flac`, `.opus`, `.wav`, `rip` (extract audio)                                         |
| **Video** | `m v [format] [file]` | `m v vp9 example.mp4`  | `.vp8`, `.vp9`, `.av1`, `.webm`, `.mp4`, `.h264`, `.h265`, `.prores`, `webm` (container)                |
| **Image** | `m i [format] [file]` | `m i webp example.jpg` | `.png`, `.jpeg`, `.webp`, `.avif`, `.iconset`, `.bevel`, `.rappleshot`, `.bgremove`, `.ascii`, `.strip` |

---

### Demo Videos


<!-- looping WebP file -->

```html
<figure>
  <img src="https://github.com/deadflowers/mediaswap/blob/main/demo/example-animation.webp?raw=true" alt="Demo Animation" />
  <figcaption>Demo animation showing the conversion process.</figcaption>
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
