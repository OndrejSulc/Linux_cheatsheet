# FFMPEG

Get photo from web camera
```
fswebcam test1.jpg
```


Get photo from RTSP stream
```
ffmpeg -y -rtsp_transport tcp -i rtsp://admin:admin@192.168.10.113:554/live -frames:v 1 do.jpg
```

## Summary
```
file name as last param     Output file/url
-i file/url                 Input file/url
-c:v h264                   Set videocodec of output to H.264
-c:a copy                   Copy audio without any changes
-b:v 1M                     Set video bitrate to 1M/s
-b:a 1M                     Set audio bitrate to 1M/s
-r 30                       Limit framerate to 30FPS
-t 10 (before -i)           Listen on input for 10 seconds
-t 10 (after -i)            Listen on input until output file has 10 seconds
-ss 00:01:00                Start after 1 minute
-s  hd720                   Set video resolution of output      
-vn                         Ignore video stream
-an                         Ignore audio stream
-sn                         Ignore subtitles stream
-y                          Overwrite output files without asking
-n                          Never overwrite existing output files
```

## Codecs and containers

>|Codec|FFMPEG encoder|FFMPEG decoder|Audio/Video|Description|
>|-|-|-|-|-|
>|H.264 / AVC|libx264|h264|Video|(Advanced Video Coding) - Great compatibility, loseless compression|
>|H.265 / HEVC|libx265|hevc|Video|(The High Efficiency Video Coding) lossy compression, less compatibility|
>|VP8 VP9| libvpx, libvpx-vp9 | libvpx, libvpx-vp9 |Video|Webm format codecs. Usable for web|
>|MP3| libmp3lame | mp3 | Audio |MP3 uses lossy compression and offers high compression rates, resulting in small files practical for online streaming and internet download|
>|FLAC| flac |flac|Audio|One of the best free lossless audio codecs. FLAC is an open-source codec|

<br/>

>|Container|Codecs|Description|
>|-|-|-|
>|.mp4|H.264, H.265, MP3|(Advanced Video Coding) - Great compatibility, loseless compression|
>|.webm|VP8, VP9|Great compatiblity with browsers|
>|.mkv| any | Matroska, allows to use any codec|


## Examples

Get info about RTSP stream
```
ffprobe rtsp://user:password@192.168.50.x:554/live1.sdp
```

Disable rtsp buffer - This format flag reduces the latency introduced by buffering during initial input streams analysis. This command will reduce noticeable the delay and will not introduce audio glitches.
```
ffplay -fflags nobuffer -rtsp_transport tcp rtsp://<host>:<port>
```

We can combine the previous -fflags nobuffer format flag with other generic options `-flags low_delay` (this codec generic flag will force low delay.) `-framedrop` (to drop video frames if video is out of sync. Enabled by default if the master clock is not set to video. Use this option to enable frame dropping for all master clock sources)
```
ffplay -fflags nobuffer -flags low_delay -framedrop -strict experimental -rtsp_transport tcp rtsp://<host>:<port>
```
Full help
>ffmpeg -h full

Available codecs
>ffmpeg -codecs

Basic conversion with autodetect (requires well-defined formats)
>ffmpeg -i input.mp3 output.ogg  
>ffmpeg -i input.mp4 output.webm

Create MKV (Matroska) container with a VP9 video stream and a Vorbis audio stream
>ffmpeg -i input.mp4 -c:v vp9 -c:a libvorbis output.mkv

Copy the audio (-c:a copy) from input.webm and convert the video to a VP9 codec (-c:v vp9) with a bit rate of 1M/s (-b:v), all bundled up in a Matroska container (output.mkv).
>ffmpeg -i input.webm -c:a copy -c:v vp9 -b:v 1M output.mkv

Creates a new Matroska with the audio stream copied over and the video stream's frame rate forced to 30 frames per second, instead of using the frame rate from the input (-r 30).
>ffmpeg -i input.webm -c:a copy -c:v vp9 -r 30 output.mkv

Change the video resolution to 1280x720 in the output.
>ffmpeg -i input.mkv -c:a copy -s hd720 output.mkv  
ffmpeg -i input.mkv -c:a copy -s 1280x720 output.mkv

Copy the video and audio streams (-c:av copy) but trim the video. The -t option sets the cut duration to be 10 seconds and the -ss option sets the start point of the video for trimming, in this case at one minute (00:01:00).
>ffmpeg -i input.mkv -c:av copy -ss 00:01:00 -t 10 output.mkv

Extract video (ignore audio and subtitles stream)
>ffmpeg -i input.mkv -an -sn audio_only.ogg

Copy the audio (-c:a copy) from input.webm and convert the video to a VP9 codec (-c:v vp9) with a bit rate of 1M/s (-b:v), all bundled up in a Matroska container (output.mkv).
>ffmpeg -i input.webm -c:a copy -c:v vp9 -b:v 1M output.mkv
