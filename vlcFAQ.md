# VLC FAQ

## Q How do I frame forward or backward?

See Hot Keys.
E = frame forward

## Q How do I control VLC from the iPhone?

The Remote 4 VLC app seems to be broken (https://vlcmobileremote.com).

Use the VLC Remote app instead:

https://iphone-tricks.com/tutorial/3421-how-to-control-vlc-from-an-iphone-vlc-remote-guide

https://apps.apple.com/ch/app/vlc-remote/id299344206?l=en

Instructions and helper setup app:

https://hobbyistsoftware.com/vlc


Caveat: Does not seem to work on M1 MB-Pro (macau) on eduroam.

## Q How do I cast a video to Chromecast without getting the warning “this video requires conversion”?

Use Handbrake to convert video and audio as follows:
- MKV container (possibly others)
- Video H264 - MPEG-4 AVC
- Audio MPEG AAC (mp4a)
- Video RF of 20 should be ok (18-23).

## Q How do I test a sample before converting an entire movie?

Use the Preview button

## Q How do I display subtitles when casting to chromecast?

It seems you need to burn in subtitles (with Handbrake or ffmpeg).
