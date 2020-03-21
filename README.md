# emerge_monitor

Monitor system status during Gentoo emerge. This is likely a bit
system-specific and some things may not work out-of-the-box. This will
probably mostly mean the CPU temperature display. A setup-agnostic
implementation of that is hoped for at some point.

Requires root to read portage logs. Might even work with `sudo -u portage`.
The second option should be more secure, or less likely to break something.

# Demo Output
Output of the monitor in action as of [commit f79077c](https://github.com/ncdulo/portop/commit/f79077c7a58e9779ff51143670dd488a75f8cbab). If that commit is no longer current, this output may not be current. I will keep updated between large revisions, otherwise this is just a general feel of the monitor.
```
┌────────────────────────────────────────────────────────┐┌────────────────────────────────────────────────────────┐
│                         mercury                        ││                 title information here                 │
├────────────────────────────────────────────────────────┤├────────────────────────────────────────────────────────┤
│                     Portage Status                     ││                    Core Frequencies                    │
├────────────────────────────────────────────────────────┤├────────────────────────────────────────────────────────┤
│                                                        ││                   cpu MHz		: 3492.815         │
│              Currently merging 1 out of 1              ││                   cpu MHz		: 3371.200         │
│                                                        ││                   cpu MHz		: 3346.858         │
│                * x11-libs/libxcb-1.13.1                ││                   cpu MHz		: 3510.742         │
│                                                        │└────────────────────────────────────────────────────────┘
│         current merge time: 4 seconds.                 │┌────────────────────────────────────────────────────────┐
│           ETA: less than a minute.                     ││                    emerge-fetch.log                    │
└────────────────────────────────────────────────────────┘├────────────────────────────────────────────────────────┤
┌────────────────────────────────────────────────────────┐│      0K .......... .......... .......... .......... ...│
│                       emerge.log                       ││     50K .......... .......... .......... .......... ...│
├────────────────────────────────────────────────────────┤│    100K .......... .......... .......... .......... ...│
│ 1584810101:  *** exiting successfully.                 ││    150K .......... .......... .......... .......... ...│
│ 1584810101:  *** terminating.                          ││    200K .......... .......... .......... .......... ...│
│ 1584823780: Started emerge on: Mar 21, 2020 16:49:39   ││    250K .......... .......... .......... .......... ...│
│ 1584823780:  *** emerge --oneshot --tree --ask --jobs=2│└────────────────────────────────────────────────────────┘
│ 1584823800:  >>> emerge (1 of 1) x11-libs/libxcb-1.13.1│
│ 1584823800:  === (1 of 1) Cleaning (x11-libs/libxcb-1.1│
│ 1584823800:  === (1 of 1) Compiling/Merging (x11-libs/l│
└────────────────────────────────────────────────────────┘
```
# Usage & Requirements
No special setup required for this one. However, a Bash-compatible shell, `genlop`, `lm_sensors`, and of course `emerge` are required to exist on the system. This will only work on Linux systems with the Portage package manager installed. Geared towards Gentoo Linux, it may work Bedrock, Mandrake, or derivatives.

To simply run the monitor, after cloning into the repo:
```bash
# Run as portage
sudo -u portage ./portop
# Run as root
sudo ./portop
```
