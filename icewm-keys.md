---
title: "icewm-keys(5)"
---
## NAME

    icewm-keys - icewm keys configuration file

## SYNOPSIS

    $ICEWM_PRIVCFG/keys
    $XDG_CONFIG_HOME/icewm/keys
    $HOME/.icewm/keys
    /etc/icewm/keys
    /usr/share/icewm/keys

## DESCRIPTION

The `keys` file defines global keybindings to launch applications.
A keybinding has three parts: the word **key**, a double-quoted string
with an X11 key combination and a program with its arguments.
These are separated by one or more spaces. Empty lines are allowed.
Comment lines start with a hash.

For example, the following defines a hotkey to restart **icewm**:

    key "Ctrl+Shift+r"      icesh restart

See the output of `xmodmap -pk` for a list of the many keystroke names
you can use in icewm key definitions. Since IceWM version 3.4.0,
bindings can not only be defined by their keystroke name, but also by
their key label. In addition, the shifted key is now definable as well.
For example, the key with + and = can be bound in either of the
following four ways, which are identical:

    key "Ctrl+Shift+equal"  xterm
    key "Ctrl+Shift+="      xterm
    key "Ctrl+plus"         xterm
    key "Ctrl++"            xterm

To bind the mouse, use `Pointer_Button1` for button 1, and so on.
This only works when the mouse is over the root window.
See below for examples.

Sometimes you may want to start an application just once. For this, use
the `runonce` keyword, which accepts an additional resource argument.

The command `icesh keys` instructs icewm to reload this file.

## FORMAT

The syntax of the `keys` file is as follows:

> - **key** **"**_key\_combination_**"** _program_ _options_

Where,

- **key**

    The word **key** begins the definition of a keybinding.

- _key\_combination_

    A combination of modifiers and a key, like `Ctrl+Alt+Delete`.
    Valid modifiers are Alt, AltGr, Ctrl, Hyper, Meta, Shift, Super.
    Each modifier must be followed by a single plus-sign.
    The key is either a keystroke name or a key label.
    Instead of a key, mouse pointer buttons can be specified by
    `Pointer_Button1` and up, like `Shift+Pointer_Button3`.

- _program_ _options_

    _program_ is the name of the executable or its path.
    It may start with a tilde or an environment variable,
    which will be expanded.
    The _options_ are passed as arguments to the _program_.

- **runonce**

    Is an alternative to **key**. Its syntax is:

    >     - **runonce** **"**_hotkey_**"** **"**_wmclass_**"** _program_ _options_

    Here _wmclass_ is the resource name and/or class. The class must be
    prefixed by a dot. The program is only run when no other application
    window with the same _wmclass_ exists. Icewm ignores key repeat events
    for this hotkey.

- **switchkey**

    Is an alternative to **key**. In this case the _program_ must print on
    standard output the definition of a dynamic [icewm-menu(1)](icewm-menu).
    This menu will presented as a popup menu.

## EXAMPLES

Following is the example `keys` file that ships with [icewm(1)](icewm):

    # This is an example for IceWM's hotkey definition file.
    #
    # A list of all valid keyboard symbols can be found in
    # /usr/include/X11/keysymdef.h, XF86keysym.h, ...
    # Omit the XK_ prefixs and replace XF86XK_ prefixes by XF86.
    # Valid modifiers are Alt, AltGr, Ctrl, Shift, Meta, Super, Hyper.
    #
    key "Alt+Ctrl+t" xterm
    key "Alt+Ctrl+b" xdg-open about:blank
    key "Alt+Ctrl+s" xdg-open https://www.google.com

    key "Super+KP_Subtract" amixer sset PCM 5%-
    key "Super+KP_Add" amixer sset PCM 5%+

    # "Multimedia key" bindings for XFree86. Gather the
    # keycodes of your advanced function keys by watching the
    # output of the xev command whilst pressing those keys
    # and map those symbols using xmodmap.

    key "XF86AudioLowerVolume" amixer sset PCM 5%-
    key "XF86AudioRaiseVolume" amixer sset PCM 5%+
    key "XF86AudioMute" amixer sset PCM 0%
    key "XF86HomePage" xdg-open about:blank
    key "XF86Search" xdg-open https://www.google.com
    key "XF86Eject" eject

    # display and select monitor setup configurations
    switchkey "Super+p" icewm-menu-xrandr

    # display and select from all terminals
    switchkey "Super+q"     icesh -Z switchmenu

Following shows how to add mouse button bindings on the root window to
change the current workspace rolling the mouse wheel on the desktop:

    key "Pointer_Button4"   icesh goto prev
    key "Pointer_Button5"   icesh goto next

These are key bindings for single window tile operations to replace the
_KeyWinArrange_ key bindings from the `preferences` file:

    key "Ctrl+Alt+KP_Home"  icesh -f sizeto 49% 49% top left
    key "Ctrl+Alt+KP_Up"    icesh -f sizeto 100% 49% top left
    key "Ctrl+Alt+KP_Prior" icesh -f sizeto 49% 49% top right
    key "Ctrl+Alt+KP_Right" icesh -f sizeto 49% 100% top right
    key "Ctrl+Alt+KP_Next"  icesh -f sizeto 49% 49% bottom right
    key "Ctrl+Alt+KP_Down"  icesh -f sizeto 100% 49% bottom left
    key "Ctrl+Alt+KP_End"   icesh -f sizeto 49% 49% bottom left
    key "Ctrl+Alt+KP_Left"  icesh -f sizeto 49% 100% top left
    key "Ctrl+Alt+KP_Begin" icesh -f sizeto 49% 49% center

## FILES

Locations for the `keys` file are as follows:

    $ICEWM_PRIVCFG/keys
    $XDG_CONFIG_HOME/icewm/keys
    $HOME/.icewm/keys
    /etc/icewm/keys
    /usr/share/icewm/keys

The locations are searched in the order listed; the first file found is
read and the remainder ignored.

## SEE ALSO

[icewm(1)](icewm).

## AUTHOR

[Brian Bidulock](mailto:bidulock@openss7.org).

## LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution.

| ------------: | :--------- |
| [Index](/man) | [![IceWM](/images/logom.jpg "ice-wm.org")](https://ice-wm.org "ice-wm.org") |
