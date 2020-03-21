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
───────────────────────────────────────────────────────────────────────────────────────────────────────────────┐┌───────────────────────────────────────────────────────────────────────────────────────────────────────────────┐
│                                                    gentoo                                                     ││                                                 System Status                                                 │
├───────────────────────────────────────────────────────────────────────────────────────────────────────────────┤├───────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│                                                Portage Status                                                 ││                                          Load average:0.58 0.42 0.38                                          │
├───────────────────────────────────────────────────────────────────────────────────────────────────────────────┤├───────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
│                                 !!! Error: no working merge found.                                            ││                                              cpu MHz : 2675.633                                               │
│                  (the -c option only works if there is an ongoing compilation, see manpage)                   ││                                              cpu MHz : 2397.806                                               │
└───────────────────────────────────────────────────────────────────────────────────────────────────────────────┘│                                              cpu MHz : 3129.755                                               │
┌───────────────────────────────────────────────────────────────────────────────────────────────────────────────┐│                                              cpu MHz : 2440.836                                               │
│                                                  emerge.log                                                   │├───────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
├───────────────────────────────────────────────────────────────────────────────────────────────────────────────┤│                                               Core 0: +100.4°                                                 │
│ 1584815435:  >>> AUTOCLEAN: dev-vcs/gh-bin:0                                                                  ││                                                Core 1: +98.6°                                                 │
│ 1584815437:  === (1 of 1) Updating world file (dev-vcs/gh-bin-0.6.2)                                          ││                                               Core 2: +114.8°                                                 │
│ 1584815437:  === (1 of 1) Post-Build Cleaning (dev-vcs/gh-bin-0.6.2::/var/db/repos/p6nc/dev-vcs/gh-bin/gh-bin-││                                               Core 3: +102.2°                                                 │
│ 1584815437:  ::: completed emerge (1 of 1) dev-vcs/gh-bin-0.6.2 to /                                          │└───────────────────────────────────────────────────────────────────────────────────────────────────────────────┘
│ 1584815437:  *** Finished. Cleaning up...                                                                     │┌───────────────────────────────────────────────────────────────────────────────────────────────────────────────┐
│ 1584815437:  *** exiting successfully.                                                                        ││                                               emerge-fetch.log                                                │
│ 1584815437:  *** terminating.                                                                                 │├───────────────────────────────────────────────────────────────────────────────────────────────────────────────┤
└───────────────────────────────────────────────────────────────────────────────────────────────────────────────┘│                                                                                                               │
                                                                                                                 │      0K ........                                              100% 57.6M=0s                                   │
                                                                                                                 │                                                                                                               │
                                                                                                                 │ 2020-03-20 21:34:47 (57.6 MB/s) - ‘/var/cache/distfiles/LWP-UserAgent-Cached-0.06.tar.gz.__download__’ save   │
                                                                                                                 │                                                                                                               │
                                                                                                                 │  * LWP-UserAgent-Cached-0.06.tar.gz BLAKE2B SHA512 size ;-) ...          [ ok ]                               │
                                                                                                                 │  * 0.0.2.tar.gz size ;-) ...                                             [ ok ]                               │
                                                                                                                 └───────────────────────────────────────────────────────────────────────────────────────────────────────────────┘
```
# Usage & Requirements
No special setup required for this one. However, a Bash-compatible shell, `genlop`, `lm_sensors`, and of course `emerge` are required to exist on the system. This will only work on Linux systems with the Portage package manager installed. Geared towards Gentoo Linux, it may work Bedrock, Mandrake, or derivatives.

Clone the repo: `git clone --recurse https://github.com/ncdulo/portop`<br>
cd into it: `cd portop`<br>
Run as root: `sudo ./portop`<br>
Or if you'd rather run it as portage: `sudo -u portage ./portop`<br>
