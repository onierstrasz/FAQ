# Camtasia FAQ

## Q What to set up when recording?

- Test the audio levels.
- Test the screen resolution. (Screen resolution should be high, but for GT, increase the scaling to 1.2 or even 1.5.)
- Install Cursorcerer to make the mouse cursor disappear.
- Possibly run `GtShortSlideshow disableHomeSections.`


## Q How to increase the output resolution?

Optimize for download?

## Q What is the right size for a screen recording?

You have to both set the *canvas size* for the project as well as the scale for the recording. Change this in the *Project settings*.
To get hi res recording, the canvas dimensions should be 1920x1080, or possibly 1920x1040 after cropping of the Mac toolbar and the GT toolbar. The scale of the screen recording should then be 75%. 

## Q How to rotate a video 90°?

Grab the rotate handle at the center of the video. Afterward scale it to fir.

## Q How to hide the cursor?

Use [Cursorcerer](http://doomlaser.com/cursorcerer-hide-your-cursor-at-will/).
Set the activation key to CTL-SHIFT-X.

## Q How best to set the lights and colors?

A This works well:
- Lights 40% 5300K
- Color adjustment: Brightness -10, Contrast +30, Saturation -50

## Q How to replace the green screen?

A Add `visual effects > Remove a Color`
- Drag to the relevant clip.
- Show properties.
- Pick the green screen color.

https://www.techsmith.com/tutorial-camtasia-how-to-remove-a-color.html

## Q How to reduce the file size?

NB: SwitchTube produces a more compact file size for download automatically

- Reduce size by 50%: 1280x720, 3000 Kbits/s
- NB: 640x480 is too small
- Handbrake RF22 reduces significantly

See also: 
https://support.techsmith.com/hc/en-us/articles/203727328-Camtasia-Mac-How-to-Make-the-File-Size-of-Videos-Smaller

## Q How can I change the aspect ratio to 4x3?

- You can record 16x9 and then crop after the fact. NB: Only crop after you have finished all recording and editing.
- Changing the project settings to use a custom canvas won't work because Camtasia records the whole screen

## Q How to I zoom out to see the whole recording?

A Command+Shift+0

## Q Where do I find the right shortcuts?

A 

https://www.techsmith.com/learn/tutorials/camtasia/camtasia-shortcuts/

## Q How to step forward and backward?

A 
- Forward: `.`
- Back: `,`
- Forward x 15: `Control-Shift-.`
- Back x 5: `Control-Shift-,`
- Next marker: `Control+]`
- Previous marker: `Control+[`
- Next edit: `Control+.`
- Previous edit: `Control+,`

https://assets.techsmith.com/Downloads/ua-tutorials-camtasiaMac-02/Camtasia-2.8-Keyboard-Shortcuts.pdf

## Q How to stop Camtasia from animating the move of the talking head?

## Q How to zoom and animate to focus on parts of the screen?

https://www.techsmith.com/learn/tutorials/camtasia/animations/

---
# Tips and tricks (for wiki page)

## Setup
- Use a green screen with two flood lights on the screen, plus separate lights on your face, if possible. (eg Elgarto green screen and Elgato Key Light Air)
- Invest in a decent webcam (eg Logitech Brio)
- Be sure the screen is evenly lit.
- Close shutters and doors to avoid changes in ambient light.

## Resolution
- If you plan to do demos, set the screen resolution to the lowest setting. This will make it easier to see details in the video.

## Annotation
- You can use a tool like Ink2Go to highlight or draw on any part of the screen

## Recording
- If possible, record in a single take, to simplify editing.
- You can pause the recording rather than stopping and starting a new one.

## Fixing mistakes
- If you make a mistake, a good trick is to leave a few seconds pause in the recording; when editing you will see where the sound disappears, and where you will have to edit.
- Another trick is to leave a short instruction to yourself about what to edit, with several second pauses both before and after.

## Green screen elimination
- The idea is to overlay your image on the edited slides, so the green screen becomes transparent. You will want to crop the track with your image, match the green screen, and adjust the colour. First crop, then use the “Visual Effects” tools “Green Screen” and “Color Adjustment”.
- If you have recorded everything in a single media file, you only have to do this operation once. After matching the green screen background, scroll through the entire video to check that the green screen does not become visible at points. If it does, you may have to split the video into parts, and separately match the parts with a different color value. (That's why it's important to uniformly light the screen, and avoid changes in ambient lighting.)
- After verifying the green screen matching, adjust the brightness, contrast and saturation of your face with the “Color Adjustment” tool.

## Positioning your image
- The trick now is to place your image in a suitable location with every transition to a new slide or demo. Camtasia will automatically generate markers for every transition.
- Use the keyboard shortcuts Control+] and Control+[ to move to the next or previous marker. Use . and , to move forward or backward a single frame. (NB: The markers are not always placed on exactly the right frame, so you may have to move them.)

## Editing
- Most of the work consist in (1) editing out mistakes and dead zones, and (2) creating transitions so your floating image moves to new area of the screen that doesn't cover important content.
- To edit out mistakes, zoom in to locate the points to start and stop the cut. Use “ripple delete” to remove a section. It can be useful to set markers at the points to more easily select the region to cut. Tip: avoid awkward jumps in your image, so try to keep your head and face in roughly the same position while recording.
- To make transitions, find the exact position where the background changes (eg new slide or switch to or from a demo). Split,, the track with your image at that point, and then reposition your image to a free spot.
- Tip: locate both the start and end of a sequence with the same background, and cut both. Then when you reposition your image, it will stay in the old spot after the second cut. This is useful when you transition from a slide to a demo and back again.


---
