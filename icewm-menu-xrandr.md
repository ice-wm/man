---
title: "icewm-menu-xrandr(1)"
---
# NAME

    icewm-menu-xrandr - IceWM menu provider for multi-monitor setup shortcuts

# SYNOPSIS

**icewm-menu-xrandr**

# DESCRIPTION

**icewm-menu-xrandr** is a helper to manage multi-screen configurations
in a semi-automated way. It is a regular icewm menu generator which dynamically
detects the available xrandr screens (i.e. connected monitors) and
creates menu entries that call the xrandr command to setup this
configuration.

Optionally, the contents of the generated configurations can be accessed
on-the-fly as a "quick-switch" menu which is accessible by Super-P key
binding of **icewm**.

# OPTIONS

**icewm-menu-xrandr** does not support any options.

# ENVIRONMENT

# CAVEATS

The quick-switch menu is only accessible when **icewm-menu-xrandr** program
is registered as special binding of type **switchkey** in
[icewm-keys(5)](icewm-keys.md) configuration.

# SEE ALSO

[icewm(1)](icewm.md),
[xrandr(1)](https://manned.org/xrandr.1).

# BUGS

**icewm-menu-xrandr** had no known bugs at the time of release.  Please report bugs
for current versions to the source code repository at
[https://github.com/bbidulock/icewm/issues](https://github.com/bbidulock/icewm/issues).

# AUTHOR

Eduard Bloch [mailto:edi@gmx.de](mailto:edi@gmx.de).

# LICENSE

**icewm-menu-xrandr** is licensed under the Simplified BSD License.
**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution.
