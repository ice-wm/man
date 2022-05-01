---
title: "icewm-shutdown(5)"
---
## NAME

    icewm-shutdown - icewm shutdown configuration file

## SYNOPSIS

    $ICEWM_PRIVCFG/shutdown
    $XDG_CONFIG_HOME/icewm/shutdown
    $HOME/.icewm/shutdown
    /etc/icewm/shutdown
    /usr/share/icewm/shutdown

## DESCRIPTION

Contains commands to be executed on **icewm** shutdown.  This is an
executable script with commands to be executed in the last stage of
**icewm** termination.  Typically they may undo some of the effects of
the `startup` script.  It is run by [icewm-session(1)](icewm-session) when **icewm**
terminates.

## FILES

Locations for the `shutdown` file are as follows:

    $ICEWM_PRIVCFG/shutdown
    $XDG_CONFIG_HOME/icewm/shutdown
    $HOME/.icewm/shutdown
    /etc/icewm/shutdown
    /usr/share/icewm/shutdown

The locations are searched in the order listed; the first file found is
read and the remainder ignored.

## SEE ALSO

[icewm-session(1)](icewm-session),
[icewm-startup(5)](icewm-startup).

## AUTHOR

[Brian Bidulock](mailto:bidulock@openss7.org).

## LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution.

| ------------: | :--------- |
| [Index](/man) | [![IceWM](/images/logom.jpg "ice-wm.org")](https://ice-wm.org "ice-wm.org") |
