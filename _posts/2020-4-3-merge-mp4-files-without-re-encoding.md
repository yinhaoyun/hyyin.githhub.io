The mp4 files should have the same resolutions and codecs.

Bash Command
==================

```
ls *.mp4 | xargs -i echo file {} > list.txt
ffmpeg -f concat -safe 0 -i mylist.txt -c copy output.mp4
```

Reference
==================
https://stackoverflow.com/questions/7333232/how-to-concatenate-two-mp4-files-using-ffmpeg
