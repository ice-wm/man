---
title: "icewm-startup(5)"
---
# NAME

    icewm-startup - icewm startup configuration file

# SYNOPSIS

- `$ICEWM_PRIVCFG/startup`
- `$XDG_CONFIG_HOME/icewm/startup`
- `$HOME/.icewm/startup`
- `/etc/icewm/startup`
- `/usr/share/icewm/startup`

# DESCRIPTION

Contains commands to be executed on **icewm** startup.  This is an
executable script with commands to tweak X11 settings and launch some
applications which need to be active whenever **icewm** is started.
It is run by [icewm-session(1)](icewm-session.md) when **icewm** starts.

# FORMAT

# EXAMPLES

# FILES

Locations for the toolbar options file are as follows:

- `$ICEWM_PRIVCFG/startup`
- `$XDG_CONFIG_HOME/icewm/startup`
- `$HOME/.icewm/startup`
- `/etc/icewm/startup`
- `/usr/share/icewm/startup`

# SEE ALSO

[icewm(1)](icewm.md),
[icewm-env(5)](icewm-env.md),
[icewm-session(1)](icewm-session.md),
[icewm-shutdown(5)](icewm-shutdown.md).

# AUTHOR

[Brian Bidulock](mailto:bidulock@openss7.org).

# LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution.

| ------------: | :--------- |
| [Index](/man) | [IceWM](/) |
