# Plex FAQ

* Q How to fix an incorrectly identified movie?

Go to “...” > Fix Match

https://support.plex.tv/articles/201018497-fix-match-match/

* Q How do I fix the "transcoder failed" error with subtitles?

Try to play the movie first from the browser, then add the subs there.
If this works, then you can continue on chromecast.

If the transcoder failed error occurs also in the browser, try to kill and restart Plex. (Work for Rabbit-Proof fence and Lost City after restarting Plex.)

Of course the last reosrt is to burn in subs with ffmpeg.

* Q How should subtitles be encoded?

- UTF-8

https://forums.plex.tv/t/get-subtitles-working-from-folder-of-external-srt-files/309855/4


* Q How to name movie files with parts?

The Dark Knight (2008) - part1.mp4

https://support.plex.tv/articles/naming-and-organizing-your-movie-media-files/

See also: How to join multi-part movies

https://forums.plex.tv/t/howto-joining-multi-part-movies-files-with-mkvtoolnix-gui/113211

* Q How to name TV shows?

- ShowName – s02e17 – Optional_Info.ext
- ShowName – 2011-11-15 – Optional_Info.ext

https://support.plex.tv/articles/naming-and-organizing-your-tv-show-files/

* Q How to name cartoons?

Looney Tunes/Season 1950/Looney Tunes s1950e06 - The Scarlet Pumpernickel [ENG,FRE] [Commentary].mkv

* Q When I try to play Yojimbo, I get an H4 codec error. How do I fix it?

The problem seems to be with the phone app. Try to cast from the computer use Google Chrome. Afterwards you can control the playback from the phone or iPad.

Try to convert the video with handbrake:
Video H264 - MPEG-4 AVC
Audio MPEG AAC (mp4a)

If that does not work, try to cast from VLC.

