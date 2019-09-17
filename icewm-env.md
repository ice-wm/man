---
title: "icewm-env(5)"
---
# NAME

    icewm-env - icewm environment configuration file

# SYNOPSIS

    $ICEWM_PRIVCFG/env
    $XDG_CONFIG_HOME/icewm/env
    $HOME/.icewm/env
    /etc/icewm/env
    /usr/share/icewm/env

# DESCRIPTION

[icewm-session(1)](icewm-session) loads additional environment variables from the file
`env` before it does anything else. These variables are then propagated
to all other processes, including [icewm(1)](icewm), via their environment.

# FORMAT

Each line is subjected to POSIX shell expansion by [wordexp(3)](https://manned.org/wordexp.3).
Comment lines starting by a hash-sign (`#`) are ignored.
[icewm-session(1)](icewm-session) will load those expanded lines which contain a name,
followed by an equals sign, followed by the value (which may be empty).

# EXAMPLES

    # This is a comment.
    # And another.

    XDG_CURRENT_DESKTOP="ICEWM"
    XDG_MENU_PREFIX="unexicon-"

    START_DATE=`date`
    START_FROM=`pwd`

# FILES

[icewm-session(1)](icewm-session) looks for the `env` file in the following locations:

    $ICEWM_PRIVCFG/env
    $XDG_CONFIG_HOME/icewm/env
    $HOME/.icewm/env
    /etc/icewm/env
    /usr/share/icewm/env

# SEE ALSO

[icewm(1)](icewm),
[icewm-session(1)](icewm-session),
[icewm-startup(5)](icewm-startup).

# AUTHOR

[Brian Bidulock](mailto:bidulock@openss7.org).

# LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution.

| ------------: | :--------- |
| [Index](/man) | [![IceWM](/images/logom.jpg "ice-wm.org")](https://ice-wm.org "ice-wm.org") |
