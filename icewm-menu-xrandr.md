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
on-the-fly through a "quick-switch" style menu which pops up upon
pressing Super-P key binding (or a manually configured key, see
[icewm-keys(5)](icewm-keys) for the configuration of **switchkey** directive).

# OPTIONS

- **--max**

    Instead of using the preferred mode and refresh rate of each monitor
    (xrandr's `--auto` option), identify and use the modes with the highest
    bandwidth usage (i.e. usually the ones with the highest resolution and
    refresh rate). This behaviour is also enabled by creating the file
    `$HOME/.cache/xrandrmenu.max` which would also effect the monitor
    quick-switch menu.

# SEE ALSO

[icewm(1)](icewm),
[xrandr(1)](https://manned.org/xrandr.1).

# BUGS

**icewm-menu-xrandr** had no known bugs at the time of release.  Please report bugs
for current versions to the source code repository at
[Github](https://github.com/bbidulock/icewm/issues).

# AUTHOR

[Eduard Bloch](mailto:edi@gmx.de).

# LICENSE

**icewm-menu-xrandr** is licensed under the Simplified BSD License.
**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution.

| ------------: | :--------- |
| [Index](/man) | [![IceWM](/images/logom.jpg "ice-wm.org")](https://ice-wm.org "ice-wm.org") |
