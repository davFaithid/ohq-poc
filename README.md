# OHQ (Overly High Quality) Proof of Concept

The following are my minimum specifications for OHQ 

```
Audio:
    FLAC/WAVE:
    24bit FLAC, -sample_fmt s32 -ar 99990 -b 17M
    64bit WAVE, -c:a pcm_f64le -ar 99000 -ac 5
                                   ^ 99900 as well

Video:
    Format doesn't really matter, h264/h265/vp9 probably best
    Bitrate: 17M
             ^ If file size is an issue, try dividing 1,073,741,274 by the video's length in seconds
               ie for a one minute video 17895687.9 or rather round to 17895688 or 17900000 (18M)
               For more rounding, try 1000000000 / # of secs                       16666666 (17M)
    Preset:  fast medium slow (superfast okay though)
    Tuning:  (Depends)

Example:
    ffmpeg -i "in.mkv" -b:v 17M -c:a pcm_f64le -ar 99900 -ac 5 -preset fast -tune animation "D:/out.mkv"
    ffmpeg -i in.flac -b 17M -sample_fmt s32 -ar 99990 out.flac
```
