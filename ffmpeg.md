# ffmpeg

## Resolutions:
 - ultrawide resolution: 3440 x 1440
 - 16L9 res: 2560 x 1440
 - 720p 16:9 (for twitter): 1280 x  720


## Common commands:

**Center crop (landscape) video to 16:9:**

`ffmpeg -i input.mp4 -filter:v "crop=(ih*(16/9)):ih:((iw*9-16*ih)/18):0" -c:a copy out.mp4`

**Center crop to 16:9, then resize to 720p:**

`ffmpeg -i input.mp4 -filter:v "crop=(ih*(16/9)):ih:((iw*9-16*ih)/18):0, scale=-1:720" -c:a copy out.mp4`
