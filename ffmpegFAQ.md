# ffmpeg FAQ

## Q How do I join two mp4 files into one?

If you have two mp4 files of the same format, you can create a list file that looks like this:

```
    $ cat fileList.txt
    file '/home/file1.mp4'
    file '/home/file1.mp4'
```

Now run:
```
    ffmpeg -f concat -safe 0 -i fileList.txt -c copy mergedVideo.mp4
```

## Q How long does it take to burn in subtitles?

Roughly 10 minutes per hour of film.

## Q How should I prepare a video to watch on the LG TV?

Use mpeg4 video and mpeg3 audio

```
  CRF=20
	time ffmpeg -i "${IN}" \
		-c:v libx264 \
    -crf ${CRF} \
    -c:a aac \
		"${BASE}-LG-CRF${CRF}.mkv"
```
Works for both USB sticks and casting from VLC to chromecast.

mp4 is also ok, but when copying files to the iPad they will automaticaaly end up in the Photos app instead of the Files app.

## Q Where should I install ffmpeg?

/usr/local/bin looks good

## Q How can I keep the subtitle tracks?

Use option: `-c:s copy`

https://askubuntu.com/questions/214199/how-do-i-add-and-or-keep-subtitles-when-converting-video

This will keep just the first subtitle.
To keep all subtitles use: `-map 0`

To keep selected subtitles use:
```
	ffmpeg -i input.mkv -map 0 -c copy -c:s mov_text -metadata:s:s:0 language=eng -metadata:s:s:1 language=ita output.mp4
```

## Q How to convert mkv to mp4?

```
	ffmpeg -i input.mkv output.mp4
```


## Q How do I trim/sample a video?

```
-ss startime
-t duration
```
```
	ffmpeg -i Planet.Earth.S01E01.avi \
		-vcodec copy -acodec copy \
		-ss 00:48:13.000 \
		-t 00:12:00.000 \
		Planet.Earth.Diaries.S01E01.avi
```
## Q How do I downsample a video?

Sample script:
```
	ffmpeg -i "IN" \
		-c:a copy \
		-crf 23 \
		-vf scale="720:-1" \
		"OUT"
```
For fixed width and height -
```
	ffmpeg -i input.avi -c:a copy -vf scale="720:480" output.avi
```
and if you want to retain aspect ratio just give height as -1 and it will automatically resize based on the width -
```
	ffmpeg -i input.avi -c:a copy -vf scale="720:-1" output.avi
```
If you want to scale based on input size e.g. lets say reduce the width/height to half you can do -
```
	ffmpeg -i input.avi -c:a copy -vf scale="iw/2:ih/2" output.avi
```
Set the CRF quality
```
	ffmpeg -i input.avi -c:a copy -crf 23 output.avi
```
## Q What is a good CRF level to set?

0 is lossless. 18-23 is usually good. “higher” values can be rather poor.
A good idea is to test a sample at 23 and then adjust.

## Q How do I burn in an internal subtitle track?
```
	ffmpeg -i video.mkv -vf subtitles=video.mkv out.avi
	
	ffmpeg -i video.mkv -vf "subtitles='video.mkv':si=0" out.mp4
```
https://trac.ffmpeg.org/wiki/HowToBurnSubtitlesIntoVideo

## Q How do I burn in a subtitle from an srt file?
```
	time ffmpeg -i "${IN}" \
		-c:a copy \
		-vf "subtitles=${base}.srt" \
		"${OUT}"
```

## Q How can I select a specific audio track?

This works to select everything and then remove the first track:
```
  	time ffmpeg -i "${IN}" \
    	-c:s copy \
    	-c:a copy \
    	-map 0 \
      -map -0:a:0 \
  			-ss ${START} \
  			-t ${TIME} \
  		"${OUT}"
```

Did not succeed to select a particular track. All the advice pages seem to give wrong instructions!

Alternatively use Handbrake!

## Q ffmpeg chokes on an .m4v file. How do I process it?

Just change the suffix to `.mp4`

## Useful guides

https://opensource.com/article/17/6/ffmpeg-convert-media-file-formats


