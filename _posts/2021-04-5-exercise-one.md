---
title:  "Exercise One " 
permalink: /posts/2021/04/exercise-one 
date: 2021-04-05-15
---


<h1 align="center">
  <br>
  <a href="#"><img src="https://media.tenor.com/images/bb95d074ec6de10b49eea8e14bd2fa3c/tenor.gif" alt="Markdownify" width="200"></a>
  <br>
 Exercise 1 
  <br>
</h1>


# Question :

1. Use **man** to look at the man page for one of your preferred commands.
2. Use **man** to look for a keyword related to file compression.
3. Use **which** to locate the pwd command on your Kali virtual machine.
4. Use **locate** to locate wce32.exe on your Kali virtual machine.
5. Use **find** to identify any file (not directory) modified in the last day, NOT owned by the root
   user and execute ls -l on them. Chaining/piping commands is NOT allowed!

##  Answer Solution  Number 1 

**Command :**

```bash 
man ping 
```
**output**

```bash
PING(8)                                         iputils                                        PING(8)

NAME
       ping - send ICMP ECHO_REQUEST to network hosts

SYNOPSIS
       ping [-aAbBdDfhLnOqrRUvV46] [-c count] [-F flowlabel] [-i interval] [-I interface] [-l preload]
            [-m mark] [-M pmtudisc_option] [-N nodeinfo_option] [-w deadline] [-W timeout]
            [-p pattern] [-Q tos] [-s packetsize] [-S sndbuf] [-t ttl] [-T timestamp option] [hop...]
            {destination}

DESCRIPTION
       ping uses the ICMP protocol's mandatory ECHO_REQUEST datagram to elicit an ICMP ECHO_RESPONSE
       from a host or gateway. ECHO_REQUEST datagrams (“pings”) have an IP and ICMP header, followed
       by a struct timeval and then an arbitrary number of “pad” bytes used to fill out the packet.

       ping works with both IPv4 and IPv6. Using only one of them explicitly can be enforced by
       specifying -4 or -6.

       ping can also send IPv6 Node Information Queries (RFC4620). Intermediate hops may not be
       allowed, because IPv6 source routing was deprecated (RFC5095).
DESCRIPTION
       ping uses the ICMP protocol's mandatory ECHO_REQUEST datagram to elicit an ICMP ECHO_RESPONSE
       from a host or gateway. ECHO_REQUEST datagrams (“pings”) have an IP and ICMP header, followed
       by a struct timeval and then an arbitrary number of “pad” bytes used to fill out the packet.

       ping works with both IPv4 and IPv6. Using only one of them explicitly can be enforced by
       specifying -4 or -6.

       ping can also send IPv6 Node Information Queries (RFC4620). Intermediate hops may not be
       allowed, because IPv6 source routing was deprecated (RFC5095).

OPTIONS
       -4
           Use IPv4 only.

       -6
           Use IPv6 only.

       -a
           Audible ping.

       -A
           Adaptive ping. Interpacket interval adapts to round-trip time, so that effectively not more
           than one (or more, if preload is set) unanswered probe is present in the network. Minimal
           interval is 200msec unless super-user. On networks with low RTT this mode is essentially
           equivalent to flood mode.
           
       -b Allow pinging a broadcast address.

       -B
           Do not allow ping to change source address of probes. The address is bound to one selected
           when ping starts.

       -c count
           Stop after sending count ECHO_REQUEST packets. With deadline option, ping waits for count
           ECHO_REPLY packets, until the timeout expires.

       -d
           Set the SO_DEBUG option on the socket being used. Essentially, this socket option is not
           used by Linux kernel.

       -D
           Print timestamp (unix time + microseconds as in gettimeofday) before each line.
       -f
           Flood ping. For every ECHO_REQUEST sent a period “.” is printed, while for every ECHO_REPLY received a backspace is printed. This
           provides a rapid display of how many packets are being dropped. If interval is not given, it sets interval to zero and outputs
           packets as fast as they come back or one hundred times per second, whichever is more. Only the super-user may use this option with
           zero interval.

       -F flow label
           IPv6 only. Allocate and set 20 bit flow label (in hex) on echo request packets. If value is zero, kernel allocates random flow
           label.

       -h
           Show help.

       -i interval
           Wait interval seconds between sending each packet. Real number allowed with dot as a decimal separator (regardless locale setup).
           The default is to wait for one second between each packet normally, or not to wait in flood mode. Only super-user may set interval
           to values less than 0.2 seconds.

```


##  Answer Solution Number : 2

**Command** 

```bash
apropos file | grep compression

```
**output**

```bash 
apropos: can't set the locale; make sure $LC_* and $LANG are correct
7z (1)               - A file archiver with high compression ratio format
7za (1)              - A file archiver with high compression ratio format
7zr (1)              - A file archiver with high compression ratio format
Dpkg::Compression::FileHandle (3perl) - class dealing transparently with file compression
p7zip (1)            - Wrapper on 7-Zip file archiver with high compression ratio
zip_set_file_compression (3) - set compression method for file in zip

```

##  Answer Solution Number : 3

q : Use **which** to locate the pwd command on your Kali virtual machine.

A : 

Command : 

```bash
└─$ which -a pwd                                                                                            
```
**Output**

```bash
pwd: shell built-in command
/usr/bin/pwd
/bin/pwd
```

##  Answer Solution Number : 4

Q : Use **locate** to locate wce32.exe on your Kali virtual machine.

Command: 
```bash
locate wce32.exe
```

Ouput

```bash
/usr/share/windows-resources/wce/wce32.exe
```

##  Answer Solution Number : 4

find files that have been modified over a period of time 

```bash 
find /home/kali newermt "1 day ago" -ls


  4456450      4 drwxr-xr-x  16 kali     kali         4096 Apr  5 04:52 /home/kali
  4456480      4 drwxr-xr-x   2 kali     kali         4096 Feb 23 05:37 /home/kali/Documents
  4456486      4 drwxr-xr-x   3 kali     kali         4096 Feb 23 05:37 /home/kali/.local
  4456487      4 drwx------   4 kali     kali         4096 Apr  5 04:33 /home/kali/.local/share
  4456506      4 drwxr-xr-x   2 kali     kali         4096 Feb 23 05:37 /home/kali/.local/share/icc
  4456541      4 drwx------   2 kali     kali         4096 Apr  5 04:33 /home/kali/.local/share/keyrings
  4456543      4 -rw-------   1 kali     kali          105 Apr  5 04:33 /home/kali/.local/share/keyrings/login.keyring
  4456542      0 -rw-------   1 kali     kali            0 Apr  5 04:33 /home/kali/.local/share/keyrings/user.keystore
  4456451      4 -rw-r--r--   1 kali     kali          807 Feb 23 05:32 /home/kali/.profile
  4456463      8 -rw-------   1 kali     kali         6069 Feb 23 05:42 /home/kali/.xsession-errors.old
  4456536      4 -rw-r-----   1 kali     kali            4 Apr  5 04:29 /home/kali/.vboxclient-display-svga-x11.pid
  4456464      4 drwx------   8 kali     kali         4096 Feb 23 05:37 /home/kali/.config
  4456512      4 drwxr-xr-x   2 kali     kali         4096 Feb 23 05:42 /home/kali/.config/qterminal.org
  4456531      4 -rw-r--r--   1 kali     kali         2591 Feb 23 05:42 /home/kali/.config/qterminal.org/qterminal.ini
  4456488      4 drwxr-xr-x   6 kali     kali         4096 Feb 23 05:37 /home/kali/.config/xfce4
  4456493      4 drwx------   2 kali     kali         4096 Feb 23 05:37 /home/kali/.config/xfce4/xfwm4
  4456519      4 drwx------   2 kali     kali         4096 Apr  5 04:30 /home/kali/.config/xfce4/desktop
  4456538      4 -rw-r--r--   1 kali     kali          120 Apr  5 04:30 /home/kali/.config/xfce4/desktop/icons.screen0-1350x721.rc
  4456471      4 -rw-r--r--   1 kali     kali          120 Feb 23 05:41 /home/kali/.config/xfce4/desktop/icons.screen0-702x309.rc
  4456520      4 -rw-r--r--   1 kali     kali          120 Feb 23 05:37 /home/kali/.config/xfce4/desktop/icons.screen0-784x553.rc
  4456508      4 -rw-r--r--   1 kali     kali          120 Apr  5 04:30 /home/kali/.config/xfce4/desktop/icons.screen0-1008x721.rc
  4456502      4 -rw-r--r--   1 kali     kali          120 Apr  5 04:30 /home/kali/.config/xfce4/desktop/icons.screen0-1264x753.rc
  4456521      0 lrwxrwxrwx   1 kali     kali           58 Apr  5 04:30 /home/kali/.config/xfce4/desktop/icons.screen.latest.rc -> /home/kali/.config/xfce4/desktop/icons.screen0-1424x853.rc
  4456539      4 -rw-r--r--   1 kali     kali          120 Apr  5 04:30 /home/kali/.config/xfce4/desktop/icons.screen0-1424x853.rc
  4456494      4 drwxr-xr-x   4 kali     kali         4096 Feb 23 05:37 /home/kali/.config/xfce4/panel
  4456495      4 drwx------   2 kali     kali         4096 Feb 23 05:37 /home/kali/.config/xfce4/panel/launcher-6
  4456496      4 -rw-r--r--   1 kali     kali          363 Feb 23 05:37 /home/kali/.config/xfce4/panel/launcher-6/16140766351.desktop
  4456497      4 drwx------   2 kali     kali         4096 Feb 23 05:37 /home/kali/.config/xfce4/panel/launcher-7
  4456498      4 -rw-r--r--   1 kali     kali          703 Feb 23 05:37 /home/kali/.config/xfce4/panel/launcher-7/16140766352.desktop
  4456489      4 drwxr-xr-x   3 kali     kali         4096 Feb 23 05:37 /home/kali/.config/xfce4/xfconf
  4456490      4 drwx------   2 kali     kali         4096 Apr  5 04:33 /home/kali/.config/xfce4/xfconf/xfce-perchannel-xml
  4456470      4 -rw-r--r--   1 kali     kali          203 Feb 23 05:42 /home/kali/.config/xfce4/xfconf/xfce-perchannel-xml/keyboards.xml
  4456472      4 -rw-r--r--   1 kali     kali         1819 Feb 23 05:42 /home/kali/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml
  4456529      4 -rw-r--r--   1 kali     kali          209 Feb 23 05:37 /home/kali/.config/xfce4/xfconf/xfce-perchannel-xml/thunar.xml
  4456523     16 -rw-r--r--   1 kali     kali        12368 Feb 23 05:37 /home/kali/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-keyboard-shortcuts.xml
  4456525      4 -rw-r--r--   1 kali     kali          342 Feb 23 05:37 /home/kali/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-power-manager.xml
  4456527      8 -rw-r--r--   1 kali     kali         5113 Feb 23 05:37 /home/kali/.config/xfce4/xfconf/xfce-perchannel-xml/xfwm4.xml
  4456526      4 -rw-r--r--   1 kali     kali          156 Feb 23 05:37 /home/kali/.config/xfce4/xfconf/xfce-perchannel-xml/displays.xml
  4456528      4 -rw-r--r--   1 kali     kali         2388 Feb 23 05:37 /home/kali/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-desktop.xml
  4456540      4 -rw-r--r--   1 kali     kali          285 Apr  5 04:33 /home/kali/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-notifyd.xml
  4456522      8 -rw-r--r--   1 kali     kali         4941 Feb 23 05:37 /home/kali/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml
  4456524      4 -rw-r--r--   1 kali     kali          804 Feb 23 05:37 /home/kali/.config/xfce4/xfconf/xfce-perchannel-xml/xsettings.xml
  4456485      4 -rw-r--r--   1 kali     kali            5 Feb 23 05:37 /home/kali/.config/user-dirs.locale
  4456501      4 drwx------   2 kali     kali         4096 Feb 23 05:37 /home/kali/.config/dconf
  4456504      4 -rw-r--r--   1 kali     kali          627 Feb 23 05:37 /home/kali/.config/dconf/user
  4456499      4 drwx------   2 kali     kali         4096 Apr  5 04:29 /home/kali/.config/gtk-3.0
  4456537      4 -rw-r--r--   1 kali     kali          132 Apr  5 04:29 /home/kali/.config/gtk-3.0/bookmarks
  4456510      4 drwxr-xr-x   2 kali     kali         4096 Feb 23 05:37 /home/kali/.config/qt5ct
  4456511      4 -rw-r--r--   1 kali     kali          486 Feb 23 05:37 /home/kali/.config/qt5ct/qt5ct.conf
  4456465      4 drwx------   2 kali     kali         4096 Feb 23 05:37 /home/kali/.config/pulse
  4456467      4 -rw-------   1 kali     kali          696 Feb 23 05:37 /home/kali/.config/pulse/6ad05c973d864e6c9bcd1e297134a217-stream-volumes.tdb
  4456503      4 -rw-------   1 kali     kali           43 Apr  5 04:29 /home/kali/.config/pulse/6ad05c973d864e6c9bcd1e297134a217-default-sink
  4456469      4 -rw-------   1 kali     kali          256 Feb 23 05:37 /home/kali/.config/pulse/cookie
  4456466     12 -rw-------   1 kali     kali        12288 Feb 23 05:37 /home/kali/.config/pulse/6ad05c973d864e6c9bcd1e297134a217-device-volumes.tdb
  4456468     44 -rw-------   1 kali     kali        45056 Feb 23 05:37 /home/kali/.config/pulse/6ad05c973d864e6c9bcd1e297134a217-card-database.tdb
  4456505      4 -rw-------   1 kali     kali           42 Apr  5 04:29 /home/kali/.config/pulse/6ad05c973d864e6c9bcd1e297134a217-default-source
  4456484      4 -rw-------   1 kali     kali          633 Feb 23 05:37 /home/kali/.config/user-dirs.dirs
  4456476      4 drwxr-xr-x   2 kali     kali         4096 Feb 23 05:37 /home/kali/Desktop
  4456452     12 -rw-r--r--   1 kali     kali        11759 Feb 23 05:32 /home/kali/.face
  4456544      4 drwxr-xr-x   3 kali     kali         4096 Apr  5 04:36 /home/kali/notes
  4456545      4 drwxr-xr-x   2 kali     kali         4096 Apr  5 04:36 /home/kali/notes/module\ one
  4456461      4 -rw-------   1 kali     kali           49 Apr  5 04:29 /home/kali/.Xauthority
  4456491      0 -rw-------   1 kali     kali            0 Feb 23 05:37 /home/kali/.ICEauthority
  4456478      4 drwxr-xr-x   2 kali     kali         4096 Feb 23 05:37 /home/kali/Templates
  4456453      4 -rw-r--r--   1 kali     kali         3526 Feb 23 05:32 /home/kali/.bashrc.original
  4456477      4 drwxr-xr-x   2 kali     kali         4096 Feb 23 05:37 /home/kali/Downloads
  4456475      4 drwxr-xr-x   6 kali     kali         4096 Apr  5 04:29 /home/kali/.cache
  4456492      4 drwx------   3 kali     kali         4096 Feb 23 05:42 /home/kali/.cache/sessions
  4456514      4 drwx------   2 kali     kali         4096 Feb 23 05:42 /home/kali/.cache/sessions/thumbs-kali:0
  4456532      8 -rw-r--r--   1 kali     kali         4474 Feb 23 05:42 /home/kali/.cache/sessions/thumbs-kali:0/Default.png
  4456518     52 -rw-r--r--   1 kali     kali        49550 Feb 23 05:37 /home/kali/.cache/zcompdump
  4456513      4 drwxr-xr-x   2 kali     kali         4096 Feb 23 05:37 /home/kali/.cache/mesa_shader_cache
  4456515      0 -rw-r--r--   1 kali     kali      1310728 Feb 23 05:37 /home/kali/.cache/mesa_shader_cache/index
  4456516      4 drwxr-xr-x   2 kali     kali         4096 Feb 23 05:37 /home/kali/.cache/gstreamer-1.0
  4456517    792 -rw-------   1 kali     kali       807799 Feb 23 05:37 /home/kali/.cache/gstreamer-1.0/registry.x86_64.bin
  4456509      4 drwx------   2 kali     kali         4096 Feb 23 05:37 /home/kali/.cache/obexd
  4456500      4 -rw-r--r--   1 kali     kali            5 Apr  5 04:29 /home/kali/.cache/blueman-applet-1000
  4456507      4 -rw-r--r--   1 kali     kali            8 Apr  5 04:29 /home/kali/.cache/blueman-tray-1000
  4456546      4 drwxr-xr-x   5 kali     kali         4096 Apr  5 04:38 /home/kali/test
  4456547      4 drwxr-xr-x   2 kali     kali         4096 Apr  5 04:38 /home/kali/test/recon
  4456549      4 drwxr-xr-x   2 kali     kali         4096 Apr  5 04:38 /home/kali/test/report
  4456548      4 drwxr-xr-x   2 kali     kali         4096 Apr  5 04:38 /home/kali/test/exploit
  4456534      4 -rw-r-----   1 kali     kali            4 Apr  5 04:29 /home/kali/.vboxclient-seamless.pid
  4456481      4 drwxr-xr-x   2 kali     kali         4096 Feb 23 05:37 /home/kali/Music
  4456479      4 drwxr-xr-x   2 kali     kali         4096 Feb 23 05:37 /home/kali/Public
  4456458      4 drwx------   3 kali     kali         4096 Apr  5 04:29 /home/kali/.gnupg
  4456460      4 drwx------   2 kali     kali         4096 Feb 23 05:37 /home/kali/.gnupg/private-keys-v1.d
  4456462      4 -rw-------   1 kali     kali           32 Feb 23 05:37 /home/kali/.gnupg/pubring.kbx
  4456454      8 -rw-r--r--   1 kali     kali         4705 Feb 23 05:32 /home/kali/.bashrc
  4456474      4 -rw-r-----   1 kali     kali            4 Apr  5 04:29 /home/kali/.vboxclient-clipboard.pid
  4456455      0 lrwxrwxrwx   1 kali     kali            5 Feb 23 05:32 /home/kali/.face.icon -> .face
  4456533      4 -rw-r--r--   1 kali     kali           97 Feb 23 05:42 /home/kali/.zsh_history
  4456473      8 -rw-------   1 kali     kali         5478 Apr  5 04:40 /home/kali/.xsession-errors
  4456483      4 drwxr-xr-x   2 kali     kali         4096 Feb 23 05:37 /home/kali/Videos
  4456482      4 drwxr-xr-x   2 kali     kali         4096 Feb 23 05:37 /home/kali/Pictures
  4456530      4 -rw-r--r--   1 kali     kali            1 Feb 23 05:42 /home/kali/.bash_history
  4456535      4 -rw-r-----   1 kali     kali            4 Apr  5 04:29 /home/kali/.vboxclient-draganddrop.pid
  4456456      4 -rw-r--r--   1 kali     kali          220 Feb 23 05:32 /home/kali/.bash_logout
  4456457     12 -rw-r--r--   1 kali     kali         8381 Feb 23 05:32 /home/kali/.zshrc
  4456459      4 -rw-r--r--   1 kali     kali           55 Feb 23 05:37 /home/kali/.dmrc

```