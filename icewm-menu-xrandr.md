---
title: "icewm-menu-xrandr(1)"
---
## NAME

    icewm-menu-xrandr - IceWM menu provider for multi-monitor setup shortcuts

## SYNOPSIS

**icewm-menu-xrandr**

## DESCRIPTION

**icewm-menu-xrandr** is a helper to manage multi-screen configurations
in a semi-automated way. It is a regular icewm menu generator which dynamically
detects the available xrandr screens (i.e. connected monitors) and
creates menu entries that call the xrandr command to setup this
configuration.

Optionally, the contents of the generated configurations can be accessed
on-the-fly through a "quick-switch" style menu which pops up upon
pressing Super-P key binding (or a manually configured key, see
[icewm-keys(5)](icewm-keys) for the configuration of **switchkey** directive).

The tool does not examine the exact monitor resolutions, refresh rates
or screen orientation. For this matters it uses auto selected mode by
default. However, it is possible to replace the custom option selection
for each output using _xrandr_ options in a custom configuration file
(see _CONFIGURATION_ below). Also tuning specific options like
\--brightness and --gamma is possible there.

The displayed name of the monitors is constructed using the output name
and the monitor information from its EDID data (either from its "Display
Name" field or from the "Unspecified ASCII text" fields (concatenated).

## OPTIONS

- **--max**

    Obsolete and ineffective option. Used to select the _xrandr_ mode with the
    highest detected refresh rate. However, the maximum rate might cause
    problems, therefore the explicit configuration in the _INI file_ should be
    used now, see _CONFIGURATION_.

- **--auto-number \[ init value \]**

    Adding a auto-incremented numbered prefix to each display name,
    optionally started at the specified value. This mostly useful for menu
    creation.

- **--xrandr command**

    Replacement for _xrandr_ command which should deliver equivalent data
    and accept the same options as _xrandr_.

- **--activate combo-name**

    A shortcut to run the activation command of the specified combo, just
    like _IceWM_ would run the commmand when selected from the menu or
    quick-switch dialog. The _combo-name_ parameter needs to match the
    displayed name exactly.

## CONFIGURATION

Optionally, a local configuration can specify command line options to
_xrandr_ calls, and further commands to run after mode switching.

Refer to configuration examples (_xrandr\_menu_) in _icewm_
documentation or its contrib folder for the syntax and rules of that
file. It can be placed into _$HOME/.config/icewm_ or into
_$HOME/.icewm_ or wherever _$XDG\_CONFIG\_HOME/.config/icewm_ might
resolve to.

## SEE ALSO

[icewm(1)](icewm),
[xrandr(1)](https://manned.org/xrandr.1).

## BUGS

Please report bugs at [Github](https://github.com/bbidulock/icewm/issues).

## AUTHOR

[Eduard Bloch](mailto:edi@gmx.de).

## LICENSE

**icewm-menu-xrandr** is licensed under the Simplified BSD License.
**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution.

| ------------: | :--------- |
| [Index](/man) | [![IceWM](/images/logom.jpg "ice-wm.org")](https://ice-wm.org "ice-wm.org") |
