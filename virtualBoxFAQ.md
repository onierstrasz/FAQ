# Virtual Box FAQ

Below follow various failed attempts to install Mojave in VB.
(April 2021)

---
# Installing Mojave image in VirtualBox

Steps

# Install VB

Download [latest VB](https://www.virtualbox.org/wiki/Downloads)

https://download.virtualbox.org/virtualbox/6.1.18/VirtualBox-6.1.18-142142-OSX.dmg

Install Extension package (same page).

https://download.virtualbox.org/virtualbox/6.1.18/Oracle_VM_VirtualBox_Extension_Pack-6.1.18.vbox-extpack


---
# Prepare installer

First part is ok. Installing in VB gets stuck ...


Follow [instructions](https://en.wikibooks.org/wiki/VirtualBox/Setting_up_a_Virtual_Machine/Mac_OS_X)

Opened Install macOS Mojave 10.14.dmg
Show Package Contents of installer
Convert InstallESD.dmg with Disk  Utility to a DVD/CD master: MojaveInstaller.cdr
Convert to ISO

	hdiutil convert -format UDTO -o MojaveInstaller.iso MojaveInstaller.cdr

Also try with High Sierra

	hdiutil convert -format UDTO -o HighSierraInstaller.iso HighSierraInstaller.cdr

---
# Download VB High Sierra image

Trying this one: 
https://techvatan.com/download-macos-high-sierra-virtualbox-and-vmware-image/


NB: reuse the HighSierraInstaller.iso created separately.


Create VB image
RAM 8192 MB
Create VDMK HD
100 GB

Settings>System>Enable EFI (already on)
Settings>System>Processor -> 4 , Enable PAE/NX
OK

Settings>Storage>Empty>Disk icon at right>Select the iso installer file





---

Not sure where this was from ...

macOS High Sierra Final by Geekrar.rar
From this google drive: https://drive.google.com/drive/folders/1aam0rHHgqzpCP0dyPP_1SNgvn5zSjs-i


---
# Download VB Mojave image

This part is ok. But I cannot get the image to run in VB

## macOS Mojave 10.14 by wikigain.rar.download (6 GB?)

https://clickitornot.com/macos-mojave-virtual-image/

Points to [Google drive mojave image](https://drive.google.com/file/d/1OJ-Owi_0IkqVhdWJ37GjlVVFa2QulSJe/view)

Stops with dead grey screen.

## Another one:

macOS Mojave Final APFS by Geekrar.rar.download (6.44 GB)

https://isoriver.com/macos-mojave-10-14-virtual-box-vmware/

Stops with Shell prompts.

## How to install


Create new VB Mojave image
Configure: Mac OSX 64 bit, default settings
Storage > Sata > add hard disk -- add the .vmdk file
Boot!


---
# Convert KVM to VB

qemu-img info macOS-Simple-KVM/BaseSystem.img

qemu-img convert -f raw -O vmdk macOS-Simple-KVM/BaseSystem.img BaseSystem.vmdk
qemu-img convert -f qcow2 -O vmdk macOS-Simple-KVM/MyDisk.qcow2 MyDisk.vmdk

Install these in a new image and boot.

Broken, but lets me reinstall Mojave ...

---
# Install in VB

Create new VB Mojave image
Configure: Mac OSX 64 bit, Memory 2048 MB, virtual HD, VDI, Dynamically allocated, 32GB

Settings > Storage > + Optical -- add the MojaveInstaller.iso
Settings > Display > Video memory -> MAX (128MB)
OK

Start
Wait for Shell prompt, and enter: exit
Select English as Language
Continue (use arrow keys to navigate)

STUCK at the Shell prompt (step 16 of the instructions)


---

https://www.geekrar.com/fix-efi-internal-shell-on-macos-mojave-on-virtualbox/


Download [APFS EFI Boot Image.iso](https://drive.google.com/drive/folders/18aszvAevDFUAigRvstsSM6MJQidylBSV?usp=sharing)

Add to VB image as virtual optical disk (Settings>Storage)

Tried edit startup.nsh but get invalid file name.


---

Does not work

exit
Boot Maintenance Manager
Boot From File

Doesn't show anything!


https://superuser.com/questions/1235970/stuck-on-uefi-interactive-shell-with-mac-os-x-high-sierra-vm



I was able to fix the UEFI problems as follows (credit to VirtualBox forum):

At UEFI prompt: Type exit
You'll be brought into an EFI text-mode GUI.
Select Boot Maintenance Manager and click.
Select Boot From File and click
You should see two entries in a list (they are cryptic looking PCI bus paths).

The first PCI path in the list is probably the boot partition that doesn't contain bootable firmware. The second PCI path is probably to the recovery partition, the one you need to boot from. If the 2nd partition isn't the recovery partition, look under the paths in the list to see if one of them is it. If the recovery partition isn't present and valid, these instructions won't work.

Click the 2nd entry, you should see (and then click):

macOS Install Data

Then click:

Locked Files

Then (if present), click

Boot Files

And finally click:

boot.efi

Installation will continue, or you will boot into the OS or get the Recovery Utilities menu (where macOS can be reinstalled from or Disk Utilities run). The ambiguity of that last statement is I did that awhile before writing this comment and I don't recall what I booted into first, only that it worked and was not hard to figure out what to do at that point. If you have a recovery partition, to boot directly into the Recovery Mode turn on the Mac and immediately press and hold (⌘)-R





---

Boot by clicking "Start".
When it boots, you will see some data being displayed.
This part needs clarification - UEFI Interactive Shell loads, but nothing happens. 

If you use the command "exit" you can shift to the EFI menu, but changing the settings doesn't seem to affect the progress of the UEFI Interactive Shell, which stops at the Shell> prompt.

After a while, you will need to choose the language for installation. Choose your own language.

**I never get past the Shell prompt**

Then you will be asked where to install macOS.
On the upper-left corner, you will see a "Utilities" button. Click it and select "Disk Utility".
You will see a window with different storages on the left. Choose "VBOX HARDDISK Media". Note: You may have to select View/View All Devices
Erase the Storage by clicking the "Erase" button on the top.
You will be prompted to enter the name for the storage. Enter your desired name and continue.
Wait for the process to complete. Then quit Disk Utility.
You will find a new storage media, which is like a hard disk. Choose that storage for the installation of OS X to install.
After installation completes, the virtual machine will automatically shut down. Go to "Settings".
Go to the "Storage" section to eject the .iso file.
Boot virtual machine again.
Choose system language.
Choose allow location or not.
You will be asked to enter your Apple ID. Even if you have an Apple ID, do not enter now.
Accept EULA of macOS.
Restore Time Machine Backups (if you have)
You will see the main page of OS X, open App Store.
Enter your Apple ID and sign in...

---
