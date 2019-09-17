---
title: "icewm-prefoverride(5)"
---
# NAME

    icewm-prefoverride - icewm override preferences configuration file

# SYNOPSIS

    $ICEWM_PRIVCFG/prefoverride
    $XDG_CONFIG_HOME/icewm/prefoverride
    $HOME/.icewm/prefoverride
    /etc/icewm/prefoverride
    /usr/share/icewm/prefoverride

# DESCRIPTION

Settings which override the settings from a theme.  Some of the **icewm**
configuration options from the preferences file which control the
look-and-feel may be overridden by the theme, if the theme designer
thinks this is desirable.  However, this `prefoverride` file will again
override this for a few specific options of your choosing.  It is safe
to leave this file empty initially.

# FILES

Locations for the `prefoverride` file are as follows:

    $ICEWM_PRIVCFG/prefoverride
    $XDG_CONFIG_HOME/icewm/prefoverride
    $HOME/.icewm/prefoverride
    /etc/icewm/prefoverride
    /usr/share/icewm/prefoverride

# SEE ALSO

[icewm(1)](icewm),
[icewm-preferences(5)](icewm-preferences).

# AUTHOR

[Brian Bidulock](mailto:bidulock@openss7.org).

# LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution.

| ------------: | :--------- |
| [Index](/man) | [![IceWM](/images/logom.jpg "ice-wm.org")](https://ice-wm.org "ice-wm.org") |
