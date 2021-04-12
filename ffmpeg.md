# ffmpeg

## Resolutions:
 - ultrawide resolution: 3440 x 1440
 - 16L9 res: 2560 x 1440
 - 720p 16:9 (for twitter): 1280 x  720


## Common commands:

### Center crop (landscape) video to 16:9

```
ffmpeg -i input.mp4 -filter:v "crop=(ih*(16/9)):ih:((iw*9-16*ih)/18):0" -c:a copy out.mp4
```

### Crop just the left half of video

```
-filter:v "crop=iw/2:ih:0:0"
```

### Center crop to 16:9, then resize to 720p

```
ffmpeg -i input.mp4 -filter:v "crop=(ih*(16/9)):ih:((iw*9-16*ih)/18):0, scale=-1:720" -c:a copy out.mp
```

### Convert gif to mp4

```
ffmpeg.exe -i input.gif -movflags faststart -pix_fmt yuv420p -vf "scale=trunc(iw/2)*2:trunc(ih/2)*2" output.mp4
```

### Merge two audio streams from the same video 

```
 -filter_complex amix=inputs=2:duration=longest
 ```
 
 See also https://stackoverflow.com/questions/14498539/how-to-overlay-downmix-two-audio-files-using-ffmpeg


### Convert to gif

```
ffmpeg -i input.mp4 -vf "fps=30,scale=830:-1:flags=lanczos,split[s0][s1];[s0]palettegen[p];[s1][p]paletteuse" -loop 0 output.gif
```

 - fps filter sets the frame rate. A rate of 10 frames per second is used in the example.
 - scale filter will resize the output to 830 pixels wide and automatically determine the height while preserving the aspect ratio. The lanczos scaling algorithm is used in this example.
 - palettegen and paletteuse filters will generate and use a custom palette generated from your input. These filters have many options, so refer to the links for a list of all available options and values. Also see the Advanced options section below.
 - split filter will allow everything to be done in one command and avoids having to create a temporary PNG file of the palette.
 - Control looping with -loop output option but the values are confusing. A value of 0 is infinite looping, -1 is no looping, and 1 will loop once meaning it will play twice. So a value of 10 will cause the GIF to play 11 times.
