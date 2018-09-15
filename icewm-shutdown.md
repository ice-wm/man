---
title: "icewm-shutdown(5)"
---
# NAME

    icewm-shutdown - icewm shutdown configuration file

# SYNOPSIS

- `$ICEWM_PRIVCFG/shutdown`
- `$XDG_CONFIG_HOME/icewm/shutdown`
- `$HOME/.icewm/shutdown`
- `/etc/icewm/shutdown`
- `/usr/share/icewm/shutdown`

# DESCRIPTION

Contains commands to be executed on **icewm** shutdown.  This is an
executable script with commands to be executed in the last stage of
**icewm** termination.  Typically they may undo some of the effects of
the `startup` script.  It is run by [icewm-session(1)](icewm-session.md) when **icewm**
terminates.

# FORMAT

# EXAMPLES

# FILES

Locations for the toolbar options file are as follows:

- `$ICEWM_PRIVCFG/shutdown`
- `$XDG_CONFIG_HOME/icewm/shutdown`
- `$HOME/.icewm/shutdown`
- `/etc/icewm/shutdown`
- `/usr/share/icewm/shutdown`

# SEE ALSO

[icewm(1)](icewm.md),
[icewm-env(5)](icewm-env.md),
[icewm-session(1)](icewm-session.md),
[icewm-startup(5)](icewm-startup.md).

# AUTHOR

[Brian Bidulock](mailto:bidulock@openss7.org).

# LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution.
