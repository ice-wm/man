---
title: "icewm-focus_mode(5)"
---
# NAME

    icewm-focus_mode - icewm focus mode configuration file

# SYNOPSIS

- `$ICEWM_PRIVCFG/focus_mode`
- `$XDG_CONFIG_HOME/icewm/focus_mode`
- `$HOME/.icewm/focus_mode`
- `/etc/icewm/focus_mode`
- `/usr/share/icewm/focus_mode`

# DESCRIPTION

Defines the initial value for `FocusMode`.  Its default value is
`FocusMode=1` (Click-to-focus).  This can be changed via the menu.
**icewm** will save the Focus menu choice in this file.

# FORMAT

The file contains a single line containing the preferences assignment
for **FocusMode**.

# EXAMPLES

The following is my `focus_mode` file:

    FocusMode=2

# FILES

Locations for the toolbar options file are as follows:

- `$ICEWM_PRIVCFG/focus_mode`
- `$XDG_CONFIG_HOME/icewm/focus_mode`
- `$HOME/.icewm/focus_mode`
- `/usr/share/icewm/focus_mode`
- `/usr/local/share/icewm/focus_mode`

# SEE ALSO

[icewm(1)](icewm.md),
[icewm-preferences(5)](icewm-preferences.md).

# AUTHOR

[Brian Bidulock](mailto:bidulock@openss7.org).

# LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution.

[Index](/man) | [IceWM](/)
