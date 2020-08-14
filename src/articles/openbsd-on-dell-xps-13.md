# OpenBSD on Dell XPS 13
#### May 26, 2020

![OpenBSD](https://www.openbsd.org/art/puffy/ppuf300X272.gif)

Yes, [OpenBSD][1] runs on Dell XPS 13 (9343). What happened to my [Gentoo build][2]? It is gone now. Sorry Gentoo, it is not personal, and you still have your place in my heart. You might be thinking that I will also update the color schema of ogrul.org, but *NOT*. For now.

This article is not about how you can install OpenBSD on your laptop but about what you can do after installing it. Trust me, OpenBSD has one of the easiest installers you can ever see. Don't delete partition i (MSDOS) after deciding to have your partition schema. And, whenever you boot up your freshly installed OpenBSD, please run fw_update and syspatch.

Out of the box on Dell XPS 13 (When I was writing this, I didn't test bluetooth and camera, and I don't use both.):

* Intel HD Graphics 5500
* Intel Dual Band Wireless AC 7265
* Touchpad
* Realtek RTS5249 Card Reader

are working without any issues. What about the Realtek ALC3263 chipset soundcard? Of course not. Because Dell has a fantastic [buggy BIOS][3] that causes problems with the detection of the hardware in the boot sequence, and proper codecs are not able to load time to time -even when you choose Thorough in the Fast Boot settings no matter what OS you are using. What I did in OpenBSD:

* Update azalia.c and dsdt.c manually
* After the update, compile my kernel

and the soundcard did work. If you have the same laptop, and want to try OpenBSD, follow the simple guide below.

## Step 1: Downloading the source tree

```
~$ cd /usr/src
~$ ftp https://cdn.openbsd.org/pub/OpenBSD/6.7/sys.tar.gz
~$ tar xzf sys.tar.gz
```

After unpacking the source tree, azalia.c and dsdt.c files must be updated. My method is based on [an old mailing list discussion][4], and the patches were mentioned there. I tried the patches, and they didn't work. Then, I decided to update both files manually.

## Step 2: Updating azalia.c and dsdt.c

```
~$ cd /usr/src/sys/dev/acpi
~$ nano dsdt.c
# Go to line 1469
{ "_REV", AML_OBJTYPE_INTEGER, 2, NULL },
# Change 2 with 5
{ "_REV", AML_OBJTYPE_INTEGER, 5, NULL },
# Save it.
# After dsdt.c, next stop is azalia.c
~$ cd ..
~$ cd pci
~$ nano azalia.c
# Go to line 458
case PCI_PRODUCT_INTEL_BAYTRAIL_HDA:
# Under it, as a line 459, put below.
case PCI_PRODUCT_INTEL_CORE5G_HDA_1:
# Save it.
```

Now, both important files are updated. It is time to build the custom kernel.

## Step 3: Building custom kernel

```
~$ cd /usr/src/arch/amd64/conf
~$ cp GENERIC.MP CUSTOM
~$ config CUSTOM
~$ cd ../compile/CUSTOM/
~$ make
~$ make install
~$ shutdown -p now
```

Cold boot is essential. Otherwise, changes won't take effect. Finally, it is time to validate the changes. 

## Step 4: It works!

```
azalia1 at pci0 dev 27 function 0 "Intel 9 Series HD Audio" rev 0x03: msi
azalia1: codecs: Realtek/0x0288
audio0 at azalia1
```

There it is. Now, OpenBSD is my daily OS. I had to replace [dwm][5] with [spectrwm][6] and [surf][7] with [vimb][8]. The rest of the applications are the same.

I want to emphasize one more time; the soundcard problem has nothing to do with OpenBSD. I have a [Logitech G432 gaming headset][9] for [Playstation 4 Pro][10], and it came with its USB soundcard dongle. Funny enough, I tried it on OpenBSD, and OpenBSD did detect it, and I even listened to music through it. The problem is with the BIOS of Dell XPS 13. I am not sure if it is also the case for newer models, but whatever Dell decided to do, it messed up -OS independent- the soundcard detection.

From now on, I will share my journeys from my OpenBSD installed laptop. In case of any questions, or better suggestions for the soundcard problem of Dell XPS 13 on OpenBSD, feel free to send me an email.


[1]: https://openbsd.org
[2]: https://ogrul.org/2020/05/04/my-ideal-setup-os.html
[3]: https://www.dell.com/community/Laptops-General-Read-Only/XPS-13-2015-9343-sound-card-issues/td-p/4568340
[4]: http://openbsd-archive.7691.n7.nabble.com/audio-codec-RealTek-ALC3263-td278384.html
[5]: https://dwm.suckless.org
[6]: https://github.com/conformal/spectrwm
[7]: https://surf.suckless.org
[8]: https://fanglingsu.github.io/vimb/
[9]: https://www.logitechg.com/en-us/products/gaming-audio/g432-7-1-surround-sound-gaming-headset.981-000769.html
[10]: https://www.playstation.com/nl-nl/explore/ps4/ps4-pro/
