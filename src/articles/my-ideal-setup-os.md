# My Ideal Setup - OS
#### May 4, 2020

I am not a Windows user. And I was never a Windows user either. Because of it, my options were either installing a BSD which I don't prefer or a GNU/Linux distribution. I needed an OS that is minimal, simple, flexible, and stable. I never wanted too many choices, too many variants of packages that do the same thing, or pre-installed packages that I don't even need them. I made a list of what I can use accordingly:

* Fedora
* Ubuntu
* Debian
* Arch
* Gentoo

As a side note, the final outcome can be achieved by any GNU/Linux distribution (distro). To me, choosing a distro is just a personal preference. Each hop from any distro doesn't mean they were bad. It means I was looking for something else to meet my needs. If you are a hardcore fan of any of them, please don't take it personally.

### Fedora
[Fedora][1] is a terrific GNU/Linux distro. It is user friendly, easy to install and upgrade, having a great package manager, very stable, and having up-to-date packages, and goes well with my laptop. [Gnome 3][2] is the default desktop environment and despite all the hatred towards it, I found it is a very comfy environment. Plus, it didn't come with so many unncessary packages installed either. I used it around 1 week, and somewhat I felt I still have the same distracted mind and not able to focus on things the way I want to. At the end of the week, I found my self downloading Ubuntu.

### Ubuntu
For some, it is the best distro, and for others, it is the worst. For me, I always remember [Ubuntu][3] with [Nelson Mandela's short video][4] in the old installation CDs which you could order online. And still, free order wherever you are located in the world effort makes me very fund of [Canonical][5]. The first time I installed Ubuntu was 2005. Back then, I even subscribed to [Cedega][6] to play some Windows games on my Ubuntu installed PC. However, 2005 was also the last year I used Ubuntu.

Today, some of you may consider I am lucky because I didn't experience [Unity][7]. But Ubuntu is still shipped with lots of packages with [Gnome 3][2], and uninstalling an irrelevant package even breaks the system due to its dependencies. I used it for not more than a day. And I downloaded my old friend Debian to make sure I will remember Ubuntu with good memories only.

### Debian
[Debian][8] is my good old friend and the first distro I've ever used. Some of you may remember, you had 8 to 10 installation CDs with all the packages that you didn't need an Internet connection to download any. Very stable and rock-solid distro of the universe. And it is true.

However, stability and security comes with a sacrifice; old packages. While Fedora is also very stable and secure, I am having difficulties in understanding the insist on the old packages in 2020. Couldn't it be a bit up-to-date? Would it really sacrifice the 'stability and security'? Should I install 'testing' with the sacrifice of security? When my mind was lost in thoughts after couple days of usage, I knew I need to move on with something else.

### Arch
The time I discovered [Arch][9], it was a snowy and cold December of 2005. I didn't know what distro-hopping means or even it was a thing back then. The old, angry, and rude GNU/Linux users whom I knew were already migrated to Arch. Moreover, the rise of the graphical installer was bringing rookies to their sacred community every day. Non-sense and duplicate topics were rising. Rookies were asking how to play games, how to install their graphics card, why the exe file was not working at all, etc. What was this madness? It was blasphemy! Their sacred community was threatened by these rookies. They became rude, and making fun of people who were using distros like Ubuntu. To them, the graphical installer was for pussies. You would only be respected by them if you could install a distro like Arch. Guess what? None of these communities are alive. And no one gives damn about what you use or what you've installed today. I am pleased that this era is ended for good.

Above has nothing to do with Arch or its community at all, but I wanted to write it. The time I tried to install Arch, I've failed, and I do remember very it well. I was lynched due to an installation question in one of these type of communities back then. It was not only me, but anyone who was not in their circle asked certain questions was lynched by them. To me, their damage is still worse than their contribution today -if they've contributed anything anyways.

I have failed to install it so many times until there was no scenario left where I could have failed. Since my successful installation by the end of December 2005, I used Arch nearly non-stop. It's a lightweight, very flexible, bleeding edge, and unironically simple distro. [Pacman][10] is an awesome package manager, [aur][11] is a great third party repo with lots of packages and have great [forums][12] and [wiki][13].

I immediately installed [ratpoison][14] (then [dwm][15]), [urxvt][16], [ranger][17], [tizonia][18], [emacs][19], [tmux][20], [irssi][21], [rtorrent][22], [surf][23] (then, [luakit][24], [vimb][25], and [qutebrowser][26]), [gimp][27], [darktable][28], and [mpv][29] on my new laptop. I was thrilled with my final setup. It was the perfect, distract-free setup I was dreaming of. When I was searching for some configuration examples for fonts, I ended up in the Gentoo wiki. And that moment, I knew I was not going to stop until I install Gentoo (a distro hopper will understand what it means and if you didn't understand, don't worry).

### Gentoo
The time I installed [Gentoo][30] for the first time was around 2007, and it was with the help of my friend. I was using [Chrunchbang][31] through a USB stick on my old cheap Clevo laptop and talking with my friend via [Jabber][32] for each step I needed to do. It took nearly a whole day (around 22 hours) to install it. There were so many circular dependencies, kernel panics, failures, frustrations, but in the end, I had my Gentoo.

The more I deep dived into Gentoo, I learned more about GNU/Linux. I was trying to have the most minimal use flag collection for my system with the best kernel configuration that was only meant for my laptop. It multiplied my knowledge in the end. One month later, I decided to install it without any help. And I succeeded. My [use flags][33], my [make.conf][34], and my kernel configuration. I used it for 3 years on my laptop and one day my laptop fried by high voltage due to an accident. When I was trying to understand what happened, I saw some construction workers were trying to pick up a timber they used for the apartment construction from the ground. What happened is one worker dropped it directly to the lamp post, and it broke one of the high voltage cables. My laptop? I couldn't get it paid by them, and later on, they had a bankruptcy and couldn't deliver the apartment according to the agreement. It was poetic justice. You shouldn't mess with my Gentoo!

This time I tried it on my Dell laptop, and the core installation took around 6 hours. I set everything up, left it to compile, came back, rebooted, and had my [X][35]. No circular dependencies, no kernel panics, no weird crushes, nothing. Everything was very smooth. The time was around midnight, and I decided to run a final command to install the packages I needed in the morning. And it was installing the browser I want to use it on my Gentoo.

/make.conf (27/04/2020)

```
# These settings were set by the catalyst build script that automatically
# built this stage.
# Please consult /usr/share/portage/config/make.conf.example for a more
# detailed example.
CHOST="x86_64-pc-linux-gnu"
CFLAGS="-march=native -O2 -pipe"
CXXFLAGS="${CFLAGS}"
MAKEOPTS="-j5"
CPU_FLAGS_X86="aes avx avx2 f16c fma3 mmx mmxext pclmul popcnt sse sse2 sse3 sse4_1 sse4_2 ssse3"

# NOTE: This stage was built with the bindist Use flag enabled
PORTDIR="/var/db/repos/gentoo"
DISTDIR="/var/cache/distfiles"
PKGDIR="/var/cache/binpkgs"

# This sets the language of build output to English.
# Please keep this setting intact when reporting bugs.
LC_MESSAGES=C

# This sets the laptop specific configuration
USE="-gtk -gnome -kde -qt5 wayland gnutls vaapi libressl"
VIDEO_CARDS="intel i965"
INPUT_DEVICES="libinput"
LINGUAS="en_US"
L10N="en"
GRUB_PLATFORMS="efi-64"
ACCEPT_LICENSE="* -@EULA"
CURL_SSL="libressl"
```

[1]: https://getfedora.org
[2]: https://www.gnome.org
[3]: https://ubuntu.com
[4]: https://www.youtube.com/watch?v=HED4h00xPPA
[5]: https://canonical.com
[6]: https://en.wikipedia.org/wiki/Cedega_(software)
[7]: https://en.wikipedia.org/wiki/Unity_(user_interface)
[8]: https://www.debian.org
[9]: https://www.archlinux.org
[10]: https://wiki.archlinux.org/index.php/Pacman 
[11]: https://aur.archlinux.org/
[12]: https://bbs.archlinux.org/
[13]: https://wiki.archlinux.org/
[14]: https://www.nongnu.org/ratpoison/
[15]: https://dwm.suckless.org/
[16]: http://software.schmorp.de/pkg/rxvt-unicode.html
[17]: https://ranger.github.io/
[18]: https://tizonia.org/
[19]: https://www.gnu.org/software/emacs/
[20]: https://github.com/tmux/tmux/wiki
[21]: https://irssi.org
[22]: https://rakshasa.github.io/rtorrent/
[23]: https://surf.suckless.org/
[24]: https://luakit.github.io/
[25]: https://fanglingsu.github.io/vimb/
[26]: https://qutebrowser.org
[27]: https://www.gimp.org/
[28]: https://www.darktable.org/
[29]: https://mpv.io/
[30]: https://gentoo.org/
[31]: https://en.wikipedia.org/wiki/CrunchBang_Linux
[32]: http://www.jabber.org/
[33]: https://wiki.gentoo.org/wiki/USE_flag
[34]: https://wiki.gentoo.org/wiki//etc/portage/make.conf
[35]: https://wiki.gentoo.org/wiki/Xorg
