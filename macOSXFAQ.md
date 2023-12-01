# Mac OSX FAQ

## Q How can I right-click with a trackpad?

Use two fingers to click.

## Q What are the Mac Mail keyboard shortcuts?

See: https://support.apple.com/en-gb/guide/mail/mlhlb94f262b/mac
```
CTRL-CMD-A -- archive mails
```

## Q How to make hidden files visible?
```
CMD-SHIFT-.
```

## Q How to delete empty directories containing folders but no files?
```
find . -type d -empty -print -delete
```

https://unix.stackexchange.com/questions/531618/find-empty-directoris-or-directories-with-no-files-in-them-recursively

## Q I get “Operation not permitted” errors after running ssh to login to my machine.

Add `sshd-keygen-wrapper` to `Security & Privacy > Privacy > Full Disk Access`

https://superuser.com/questions/1615072/getting-an-operation-not-permitted-error-when-running-commands-after-to-sshing

## Q How to Restore from Time Machine?

First do a clean install; then start the mac, and run Migration Assistant (in `Applications>Utilities`).

## Q How to wipe a Mac (before giving it up)?

- sign out of iTunes (pre-Catalina) or iCloud (post-Catalina)
- go to `System Preferences > Apple Id` -- sign out, or turn off individual iCloud services
- sign out of Messages
- disconnect any extraneous Bluetooth devices
- Reset NVRAM (restart and hold `<OPT><CMD>PR`)
- Erase the HD and reinstall the OS
- Restart and hold `<CMD>R`
- Erase the drive with Disk Utility (select Volume)
- NB: you can also install the OS from a USB drive

https://support.apple.com/en-us/HT201065

https://support.apple.com/en-gb/HT208496

## Q How do I fix "Could not open a connection to your authentication agent"?

Add 
```
eval `ssh-agent`
```
to your login script, or
```
eval `ssh-agent -s`
```
in the case of bash or sh.

## Q How to temporarily turn off notifications?

Option-click on the date in the menu bar.

## Q How to change the Big Sur login screen?

Can only change the individual lock screens, not the global login one!

- System Preferences > Users & Groups
- Open lock to make changes
- Right click on user in left column `> Advanced Options`
- Copy UUID value
- Go to `/Library/Caches/Desktop Pictures`
- If it doesn’t exist create Desktop Pictures folder
- Inside Desktop Pictures create folder with UUID value as name
- Right-click on `folder > Get Info`
- Open lock to make changes.
- Grant permission to Read & Write to user, admin, everyone.
- Change desktop wallpaper.
- Restart computer.

## Q How to reinstall a given MacOS?

Download the installer and create a bootable drive.
Download the installer the usual way, but don't install it. Then run:
```
sudo /Applications/Install\ macOS.../Contents/Resources/createinstallmedia --volume /Volumes/MyVolume
```
Replacing ... by the right MacOS installer, and MyVolume by the USB drive
For example:
```
sudo /Applications/Install\ macOS\ Ventura.app/Contents/Resources/createinstallmedia \
  --volume /Volumes/InstallVentura
```
Detailed instructions here: https://support.apple.com/en-us/HT201372

Boot the mac to update with the drive connected, and hold `OPT` (power button on M1 machines) till you see the selection of drives to boot from.

## Q Why can't I boot from USB?

https://www.uubyte.com/boot-mac-from-usb.html

In certain cases where your Mac has the Apple T2 Security Chip (2018 and later devices), it may be your Startup Security Utility settings that are preventing you from booting from USB. In this situation, restart your Mac and hold down the Command + R keys when you see the Apple logo. This will put your Mac into Recovery mode. In macOS Utilities, go to `Utilities > Startup Security Utility` and sign in as admin. Under External Boot, select the second option: `Allow Booting from External Media`.

## Q How do I get rid of drop shadows when taking screen shots of windows?

Hold down the `<OPT>` key

https://www.macworld.com/article/3527415/how-to-get-rid-of-the-screenshot-drop-shadow-in-macos.html

## Q How to create a Windows compatible Disk Image?

- https://www.makeuseof.com/tag/how-to-create-windows-compatible-iso-disc-images-in-mac-os-x/
- Create a DVD/CD disk master
- Convert to iso image:
- `hdiutil makehybrid -iso -joliet -o [filename].iso [filename].cdr`

## Q Why does Disk Utility fail to copy a CD with “operation canceled”?

`System Preferences > Security & Privacy > Privacy tab > Full Disk Access (add Disk Utility)`

https://discussions.apple.com/thread/250912433

## Q How to properly use wget?

https://handyman.dulare.com/advanced-wget-website-mirroring/

Basic version:
```
wget --mirror --convert-links --adjust-extension --page-requisites  http://www.mywebsite.com/
```

Advanced:
```
wget --mirror --convert-links --adjust-extension \
  --page-requisites --span-hosts -U Mozilla -e robots=off --no-cookies -D \
  www.mywebsite.com,files.mywebsite.com,images.somewhere.com http://www.mywebsite.com/
```

## Q How to stop Catalina from re-verifying apps?

https://appletoolbox.com/why-is-macos-catalina-verifying-applications-before-i-can-open-them/

```
defaults write com.apple.LaunchServices LSQuarantine -bool NO
```

## Q How to take a screen video?

Use QuickTime: `File > New Screen Recording`

## Q How to hide/unhide desktop icons?

https://www.maketecheasier.com/hide-desktop-icons-mac/

```
defaults write com.apple.finder CreateDesktop false
killall Finder
```
or
```
defaults write com.apple.finder CreateDesktop true
killall Finder
```

## Q How do I create symbolic root-level directory?

https://derflounder.wordpress.com/2020/01/18/creating-root-level-directories-and-symbolic-links-on-macos-catalina/

```
sudo su root
cd /etc
touch synthetic.conf
chmod 0644 synthetic.conf 
echo "home	Users/oscar/home" >> synthetic.conf 
# NB: a TAB must separate "home" from the directory
shutdown -r now
```

## Q How to find my ip address?

```
ipconfig getifaddr en1
```
or if you are on wifi, `en0`


## Q How to bulk delete iphone photos?
Use the Image Capture app on the mac. (Select all and click the delete icon)

## Q How to get audio out through HDMI?
If the Sound Preferences don't work, try the VLC audio out control.
Ditto to force audio out through the headphone jack.

## Q How to change the default finder column width?
Hover over the column separator, and hold the `OPT` key while adjusting it

## Q How to make hidden files visible/hidden:

Keyboard shortcut: `CMD SHIFT .`

As default: `defaults write com.apple.finder AppleShowAllFiles true|false`

## Q How to force Safari to save an autopassword?
Edit the Keychain entry; or create an arbitrary Keychain entry and edit it to match the one you want.

## Q How to Reduce/mute startup chime?

Reduce/mute:
```
sudo nvram SystemAudioVolume="%20"
sudo nvram SystemAudioVolume="%00"
```
Reset to default:
```
sudo nvram -d SystemAudioVolume
```

## Q How to save an app store installer?

After downloading but before installer, find the installer in the Applications folder and save it.

## Q How to ignore updates?
```
sudo /usr/sbin/softwareupdate --ignore "macOS Catalina" 
```
Cancel:
```
sudo /usr/sbin/softwareupdate --reset-ignored	
```

## Q Why are my fonts missing?

Note to Mac users: Here's an odd problem with fonts that I just solved, but it took me 30 minutes or so.  Maybe you might find it helpful.

I've been configuring my new Macbook, and found that for some reason there were a number of fonts missing -- Keynote was complaining about missing fonts when I opened some presentations.  Some of these fonts were special fonts I knew I had to add myself (so I did), but others were not.

After some digging I realized the missing fonts were standard MS Office fonts, which in the past were automatically installed in the Mac font database.  But my new laptop came with Office 2016 installed, and apparently Office 2016 just stores its fonts inside the app and does not automatically install them in the central font repository for use by other Mac apps.

The solution is simple: Make a subdirectory Microsoft in `~/Library/Fonts`, and copy all the files in `/Applications/Microsoft Word.app/Contents/Resources/DFonts` over there.

## Q What to do if bluetooth becomes unavailable?

First try to reset the PRAM.
Alternatively: Shut down your Mac, disconnect all USB devices for two minutes, start up, and re-connect your USB devices once again.

http://www.igeeksblog.com/fix-bluetooth-not-available-error-mac/

## Q How to reset PRAM

Reboot while holding `<CMD><OPT>PR`


## What are the main Mac shortcuts?

```
Sleep:			ALT CMD EJECT
Shutdown:		SHIFT ALT CMD BOOT
Extensions off:		SHIFT during reboot
Rebuild Desktop File:	ALT CMD during reboot
Screen snapshot:	SHIFT CMD 3
Spin down hard disk:	CTRL SHIFT ALT 0
Empty locked trash:	ALT empty trash
```

## Q How to make hidden directories visible?
```
chflags nohidden ~/Library

defaults write com.apple.finder AppleShowAllFiles -boolean true
killall Finder
```

The reverse is
```
defaults delete com.apple.finder AppleShowAllFiles
killall Finder
```

## Q How do I change Leopard's ugly login splash screen?
A Replace /System/Library/CoreServices/DefaultDesktop.jpg

## Q How do I make Remote Desktop work through a firewall?
A Be sure to open ports 3283 and 5900. (RTFM)

## Q How to change scale factor for applications?
A See http://truckofnews.com/?p=22
Examples:
```
defaults write NSGlobalDomain AppleDisplayScaleFactor 1.5
defaults write com.apple.iTunes AppleDisplayScaleFactor .75
```
