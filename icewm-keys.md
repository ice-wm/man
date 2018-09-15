# NAME

    icewm-keys - icewm keys configuration file

# SYNOPSIS

- `$ICEWM_PRIVCFG/keys`
- `$XDG_CONFIG_HOME/icewm/keys`
- `$HOME/.icewm/keys`
- `/etc/icewm/keys`
- `/usr/share/icewm/keys`

# DESCRIPTION

Global key bindings to launch applications (not window manager related).
IceWM allows launching of arbitrary programs with any key combination.
This is configured in the `keys` file.

Global keybindings to launch applications, which need not be window
manager related.  Each non-empty line starts with the word `key`.
After one or more spaces follows a double-quoted string of the bound X11
key combination like `Alt+Ctrl+Shift+X`.  Then after at least one space
follows a shell command line which will be executed by **icewm** whenever
this key combination is pressed.  For example, the following line
creates a hotkey to reload the **icewm** configuration:

    key "Ctrl+Shift+r"      pkill -x -HUP icewm

# FORMAT

The syntax of the `keys` file is as follows:

> - **key** **"**_key\_combination_**"** _program_ _options_

Where,

- **key**

    The literal string keyword.

- _key\_combination_

    Any combination of keys, separated by plus-sign (`+`).

- _program_ _options_

    _program_ is the name of the executable or full path to the executable
    file that will be run in response to selecting the menu item.  When used
    with the **menuprog** keyword, the _program_ must print on standard
    output the contents of the menu and is used for dynamic menus.

    _options_ is the options and arguments passed to the _program_
    verbatim.

# EXAMPLES

Following is the example `keys` file that ships with [icewm(1)](icewm.md):

    # This is an example for IceWM's hotkey definition file.
    #
    # Place your variants in @CFGDIR@ or in $HOME/.icewm
    # since modifications to this file will be discarded when
    # you (re)install icewm.
    #
    # A list of all valid keyboard symbols can be found in
    # /usr/include/X11/keysym.h, keysymdefs.h, XF86keysym.h,
    # ...  You'll have to omit XK_ prefixs and to replace
    # XF86XK_ prefixes by XF86. Valid modifiers are Alt,
    # Ctrl, Shift, Meta, Super and Hyper.
    #
    key "Alt+Ctrl+t" xterm
    key "Alt+Ctrl+b" xdg-open about:blank
    key "Alt+Ctrl+s" xdg-open http://www.google.com
    
    key "Super+KP_Subtract" amixer sset PCM 5%-
    key "Super+KP_Add" amixer sset PCM 5%+
    
    # "Multimedia key" bindings for XFree86. Gather the
    # keycodes of your advanced function keys by watching the
    # output of the xev command whilest pressing those keys
    # and map those symbols by using xmodmap.
    
    key "XF86AudioLowerVolume" amixer sset PCM 5%-
    key "XF86AudioRaiseVolume" amixer sset PCM 5%+
    key "XF86AudioMute" amixer sset PCM 0%
    key "XF86HomePage" xdg-open about:blank
    key "XF86Search" xdg-open http://www.google.com
    key "XF86Eject" eject

# FILES

Locations for the `keys` file are as follows:

- `$ICEWM_PRIVCFG/keys`
- `$XDG_CONFIG_HOME/icewm/keys`
- `$HOME/.icewm/keys`
- `/etc/icewm/keys`
- `/usr/share/icewm/keys`

# SEE ALSO

[icewm(1)](icewm.md).

# AUTHOR

Brian Bidulock [mailto:bidulock@openss7.org](mailto:bidulock@openss7.org).

# LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution.
