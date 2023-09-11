---
title: "icewm-startup(5)"
---
## NAME

    icewm-startup - icewm startup configuration file

## SYNOPSIS

    $ICEWM_PRIVCFG/startup
    $XDG_CONFIG_HOME/icewm/startup
    $HOME/.icewm/startup
    /etc/icewm/startup
    /usr/share/icewm/startup

## DESCRIPTION

The `startup` file contains commands to be executed on **icewm** startup.
This is an executable script. Typically the commands tweak X11 settings
and launch some applications that always need to be active.
It is run by [icewm-session(1)](icewm-session) when **icewm** starts.

## EXAMPLES

    #!/bin/bash
    xset r rate 250 32
    flameshot &
    volumeicon &
    redshift-gtk &
    picom -b

Remember to `chmod +x ~/.icewm/startup`.
The first line must be a hash-bang, followed by the path of your script
interpreter or shell.

## FILES

Locations for the `startup` file are as follows:

    $ICEWM_PRIVCFG/startup
    $XDG_CONFIG_HOME/icewm/startup
    $HOME/.icewm/startup
    /etc/icewm/startup
    /usr/share/icewm/startup

The locations are searched in the order listed; the first file found is
executed and the remainder ignored.

## SEE ALSO

[icewm-session(1)](icewm-session),
[icewm-shutdown(5)](icewm-shutdown).

## AUTHOR

[Brian Bidulock](mailto:bidulock@openss7.org).

## LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution.

| ------------: | :--------- |
| [Index](/man) | [![IceWM](/images/logom.jpg "ice-wm.org")](https://ice-wm.org "ice-wm.org") |
