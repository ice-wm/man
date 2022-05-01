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

Global keybindings to launch applications, which need not be window
manager related. If you are looking for ways to disable icewm's grabbing
of default key combinations, please read [icewm-preferences(5)](icewm-preferences)
instead.

Each non-empty line starts with the word `key`.
After one or more spaces follows a double-quoted string of the bound X11
key combination like `Alt+Ctrl+Shift+X`.  Then after at least one space
follows a shell command line which will be executed by **icewm** whenever
this key combination is pressed.  For example, the following line
creates a hotkey to reload the **icewm** configuration:

    key "Ctrl+Shift+r"      icesh restart

See the output of `xmodmap -pk` for a list of keystroke names.
To bind the mouse use `Pointer_Button1` for button 1, and so on.
The command `icesh keys` instructs icewm to reload this file.

## FORMAT

The syntax of the `keys` file is as follows:

> - **key** **"**_key\_combination_**"** _program_ _options_

Where,

- **key**

    The literal string keyword.

- **switchkey**

    The literal string keyword, instead of `key`, to build popup menus.
    The output of _program_ should conform to [icewm-menu(1)](icewm-menu).

- _key\_combination_

    A combination of modifiers and a key separated by a plus-sign (`+`),
    like `Ctrl+Alt+Delete`. Mouse pointer buttons can be specified by
    `Pointer_Button1` and up.

- _program_ _options_

    _program_ is the name of the executable or full path to the executable
    file that will be run in response to selecting the menu item.  When used
    with the **switchkey** keyword, the _program_ must print on standard
    output the contents of the popup like it would be used for dynamic menus.

    _options_ are the options and arguments passed to the _program_.

## EXAMPLES

Following is the example `keys` file that ships with [icewm(1)](icewm):

    # This is an example for IceWM's hotkey definition file.
    #
    # A list of all valid keyboard symbols can be found in
    # /usr/include/X11/keysym.h, keysymdefs.h, XF86keysym.h,
    # ...  You'll have to omit XK_ prefixs and to replace
    # XF86XK_ prefixes by XF86. Valid modifiers are Alt,
    # Ctrl, Shift, Meta, Super and Hyper.
    #
    key "Alt+Ctrl+t" xterm
    key "Alt+Ctrl+b" xdg-open about:blank
    key "Alt+Ctrl+s" xdg-open https://www.google.com

    key "Super+KP_Subtract" amixer sset PCM 5%-
    key "Super+KP_Add" amixer sset PCM 5%+

    # "Multimedia key" bindings for XFree86. Gather the
    # keycodes of your advanced function keys by watching the
    # output of the xev command whilst pressing those keys
    # and map those symbols by using xmodmap.

    key "XF86AudioLowerVolume" amixer sset PCM 5%-
    key "XF86AudioRaiseVolume" amixer sset PCM 5%+
    key "XF86AudioMute" amixer sset PCM 0%
    key "XF86HomePage" xdg-open about:blank
    key "XF86Search" xdg-open https://www.google.com
    key "XF86Eject" eject

    # display and select monitor setup configurations
    switchkey "Super+p" icewm-menu-xrandr

Following shows how to add mouse button bindings on the root window to
change the current workspace rolling the mouse wheel on the desktop:

    key "Pointer_Button4"   icesh goto prev
    key "Pointer_Button5"   icesh goto next

These are key bindings for single window tile operations to replace the
_KeyWinArrange_ key bindings from the `preferences` file:

    key "Ctrl+Alt+KP_7" icesh -f sizeto 49% 49% top left
    key "Ctrl+Alt+KP_8" icesh -f sizeto 100% 49% top left
    key "Ctrl+Alt+KP_9" icesh -f sizeto 49% 49% top right
    key "Ctrl+Alt+KP_6" icesh -f sizeto 49% 100% top right
    key "Ctrl+Alt+KP_3" icesh -f sizeto 49% 49% bottom right
    key "Ctrl+Alt+KP_2" icesh -f sizeto 100% 49% bottom left
    key "Ctrl+Alt+KP_1" icesh -f sizeto 49% 49% bottom right
    key "Ctrl+Alt+KP_4" icesh -f sizeto 49% 100% top left
    key "Ctrl+Alt+KP_5" icesh -f sizeto 49% 49% center

Some systems need this instead:

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
