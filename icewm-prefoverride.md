---
title: "icewm-prefoverride(5)"
---
## NAME

    icewm-prefoverride - override themable preferences file

## SYNOPSIS

    $ICEWM_PRIVCFG/prefoverride
    $XDG_CONFIG_HOME/icewm/prefoverride
    $HOME/.icewm/prefoverride
    /etc/icewm/prefoverride
    /usr/share/icewm/prefoverride

## DESCRIPTION

Settings that override the settings from a theme.  Some of the **icewm**
preferences that control the look may be set by the theme.
However, the settings in this `prefoverride` file override that.
It is safe to leave this file empty initially.
Note that this file is meant for themable preferences and a few icewm
startup settings cannot be set here, like `Splash`.

## FILES

Locations for the `prefoverride` file are as follows:

    $ICEWM_PRIVCFG/prefoverride
    $XDG_CONFIG_HOME/icewm/prefoverride
    $HOME/.icewm/prefoverride
    /etc/icewm/prefoverride
    /usr/share/icewm/prefoverride

The locations are searched in the order listed; the first file found is
read and the remainder ignored.

## SEE ALSO

[icewm(1)](icewm),
[icewm-preferences(5)](icewm-preferences).

## AUTHOR

[Brian Bidulock](mailto:bidulock@openss7.org).

## LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution.

| ------------: | :--------- |
| [Index](/man) | [![IceWM](/images/logom.jpg "ice-wm.org")](https://ice-wm.org "ice-wm.org") |
