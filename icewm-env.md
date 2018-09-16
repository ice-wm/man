---
title: "icewm-env(5)"
---
# NAME

    icewm-env - icewm environment configuration file

# SYNOPSIS

- `$ICEWM_PRIVCFG/env`
- `$XDG_CONFIG_HOME/icewm/env`
- `$HOME/.icewm/env`
- `/etc/icewm/env`
- `/usr/share/icewm/env`

# DESCRIPTION

[icewm-session(1)](icewm-session.md) loads additional environment variables from the file
`env`.

# FORMAT

Each line is subjected to POSIX shell expansion by [wordexp(3)](https://manned.org/wordexp.3).
Comment lines starting by a hash-sign (`#`) are ignored.
[icewm-session(1)](icewm-session.md) will load those expanded lines which contain a name,
followed by an equals sign, followed by the value (which may be empty).

# EXAMPLES

    # This is a comment.
    # And another.

    XDG_CURRENT_DESKTOP="ICEWM"
    XDG_MENU_PREFIX="unexicon-"

# FILES

Locations for the toolbar options file are as follows:

- `$ICEWM_PRIVCFG/env`
- `$XDG_CONFIG_HOME/icewm/env`
- `$HOME/.icewm/env`
- `/etc/icewm/env`
- `/usr/share/icewm/env`

# SEE ALSO

[icewm(1)](icewm.md),
[icewm-session(1)](icewm-session.md),
[icewm-startup(5)](icewm-startup.md).

# AUTHOR

[Brian Bidulock](mailto:bidulock@openss7.org).

# LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution.

| ------------: | :--------- |
| [Index](/man) | [![IceWM][/images/logom.jpg]](https://ice-wm.org "ice-wm.org") |
