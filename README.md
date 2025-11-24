# mediaswap
Quickly convert audio, image, and video files in console or context menu.

Mediaswap is a wrapper designed to bring the power of FFMpeg and ImageMagick tools to your Ubuntu right-click menu, and provides it's own minimal GUI through Zenity elements. Allowing you to do very powerful things, faster and with very little effort. No new programs to remember and open, it integrates into your environment. 

So you can take a high efficiency low portability image like an .heic and convert to .png, .webp, .jpeg. You can also convert it to a fun ascii style, give it a beveled edge, a hover over shadow effect. Or perhaps you want to take a mpeg video and convert to vp8 webm. Maybe you want to take a vp8 in a webm container and make it vp9. Maybe you want to take a high quality music video you snatched off youtube and rip the audio and further to do so without degrading quality with unecessary transcoding. Maybe you want to take a wav voice note and convert to a flac or opus. maybe you want to take a image you want to be an icon in your progressive web app or chrome extension or web site, and spit out all the needed copies as common expected sizes. Maybe you want to do any of the above or want to multiselect a batch of files to batch perform the above tasks and you want to do it all with a couple clicks right from your files and folder window. Well, this is what Mediaswap makes possible. 

Mediaswap consists of a core script and 3 wrapper scripts representing 3 menu hierarchies to your right-click menu: Convert Video, Convert Image, Convert Audio. These scripts in Nautilus would be placed in .local/share/Nautilus/scripts and made to be executable via a `chmod +x`. They will forward the currently selected file or files to mediaswap for the real processing. Mediaswap is a wrapper of sorts itself and will match up requested actions with appropriate FFMpeg or ImageMagick commands. 

"Will Mediaswap work in a terminal?" 
Yes! To convert a mp4 to a vp9 video, it's as easy as `mediaswap video vp9 [file]` where filename is the input file.

"That's too long." 
Ok, well Mediaswap can install a shortcut link 'm' by default. You can also run this as `m v vp9 [file]`

"That's short but what if I forget the `vp9` part and just type `m v [file]` ?"
Well, then Mediaswap will throw a Zenity box to ask what you want to do and you click on the format you want. A console + GUI workflow.

MediaSwap is a open source utility by Ray Kooyenga made in Ubuntu 25.04 with Gnome 48 and requires Zenity, Imagick Magick, FFMpeg.
