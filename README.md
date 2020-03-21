# emerge_monitor

Monitor system status during Gentoo emerge. This is likely a bit
system-specific and some things may not work out-of-the-box. This will
probably mostly mean the CPU temperature display. A setup-agnostic
implementation of that is hoped for at some point.

Requires root to read portage logs. Might even work with `sudo -u portage`.
The second option should be more secure, or less likely to break something.
