# Spotify on OpenBSD
#### July 07, 2020

![ncspot on OpenBSD](/images/ncspot.png)

Easiest way to have a [Spotify][1] client on OpenBSD is to install [ncspot][2] through [ports][3]. ncspot is an ncurses Spotify client written in [Rust][4] using librespot. It is heavily inspired by ncurses [MPD][5] clients, such as ncmpc. The motivation of ncspot is to provide a simple and resource friendly alternative to the official client as well as to support platforms that currently don't have a Spotify client, such as the *BSDs. The only thing you need to consider is that you need a premium subscription of Spotify to use ncspot. 

A simple tutorial of installation on OpenBSD is below.

## 1. Ports

```
~$ cd /tmp
~$ ftp https://cdn.openbsd.org/pub/OpenBSD/$(uname -r)/{ports.tar.gz,SHA256.sig}
~$ signify -Cp /etc/signify/openbsd-$(uname -r | cut -c 1,3)-base.pub -x SHA256.sig ports.tar.gz
~$ cd /usr
~$ doas tar xzf /tmp/ports.tar.gz
```

Currently, ncspot does not have a pre-compiled binary package, and it requires a manual compilation by the user. Step 1 is basically fetching the ports tree of OpenBSD where ncspot port is available for compilation.

## 2. Configuring Ports

```
~$ doas vim /etc/mk.conf
# Paste below to separate directories that are written to during port building
WRKOBJDIR=/usr/obj/ports
DISTDIR=/usr/distfiles
PACKAGE_REPOSITORY=/usr/packages
# Write and close the file
```

After configuring the directories, it is ideal to install the binary package of Rust rather than building through the ports. Because, it takes too long, and if there is already a pre-compiled package available, I would install it directly rather than building it through ports.

## 3. Installing Rust

```
~$ doas pkg_add rust cargo-generate-vendor
```

Now, final step is to install ncspot.

## 4. Installing ncspot

```
# Searching ncspot on ports tree
~$ cd /usr/ports
~$ doas make search key=ncspot
# If you get an error says "Please install portslist", install it.
~$ doas pkg_add portslist
# The output of the search:
# Port:   ncspot-0.1.3
# Path:   audio/ncspot
# Info:   ncurses Spotify client
# Maint:  Henrik Friedrichsen <henrik@diff.cc>
# Index:  audio lang/rust
# L-deps: audio/portaudio-svn
# B-deps: STEM->=1.30:lang/rust devel/cargo-generate-vendor lang/rust
# R-deps: 
# Archs:  any
~$ cd audio/ncspot
~$ doas make install
```

It will take some time to compile and install it. After the installation is completed, please run ncspot and login to Spotify. And enjoy!

It is really easy to use and navigate through menus on ncspot. F2 is to search anything you want on Spotify, and F1 is the queue of the music you want to listen. You have to like albums on Spotify to make them available on the Albums menu. Otherwise, it will show it empty.

PS: I don't have [Google Music][6], [Tidal][7] or any other subscriptions other than Spotify, and I didn't try cargo package of ncspot or python packages for other Spotify clients such as [mopidy][8], [tizonia][9], etc. 

[1]: https://spotify.com
[2]: https://github.com/hrkfdn/ncspot
[3]: https://www.openbsd.org/faq/ports/ports.html
[4]: https://rust-lang.org
[5]: https://musicpd.org
[6]: https://music.google.com
[7]: https://tidal.com
[8]: https://mopidy.com
[9]: https://tizonia.org
