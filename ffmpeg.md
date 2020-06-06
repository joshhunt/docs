# ffmpeg

## Resolutions:
 - ultrawide resolution: 3440 x 1440
 - 16L9 res: 2560 x 1440
 - 720p 16:9 (for twitter): 1280 x  720


## Common commands:

**Crop video to 16:9:**

`ffmpeg -i input.mp4 -filter:v "crop=-1:1440:440:0" -c copy out.mp4`