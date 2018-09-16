---
title: "icewm-toolbar(5)"
---
# NAME

    icewm-toolbar - icewm toolbar configuration file

# SYNOPSIS

- `$ICEWM_PRIVCFG/toolbar`
- `$XDG_CONFIG_HOME/icewm/toolbar`
- `$HOME/.icewm/toolbar`
- `/etc/icewm/toolbar`
- `/usr/share/icewm/toolbar`

# DESCRIPTION

The `toolbar` file is responsible for configuring quick launch
application icons that are placed on the [icewm(1)](icewm.md) panel.  The file is
used to place programs as buttons on the [icewm(1)](icewm.md) pane

Contains names of quick to launch applications with icons for the task
bar.  Each non-empty non-comment line starts with the keyword **prog**.
After one or more spaces follows a name, which is displayed in a tool
tip whenever the mouse cursor hovers over the toolbar icon.  This name
may be a double quoted string.  Then follows the bare name of the icon
to use without extensions.  This icon will be shown in the toolbar.  The
last component is a shell command line which will be executed whenever
the user presses the icon in the toolbar.  For example, the following
line in toolbar will create a button with tool tip `Mozilla Firefox`
with the `firefox` icon which launches [firefox(1)](https://manned.org/firefox.1) when clicked:

    prog  "Mozilla Firefox"  firefox  /usr/bin/firefox --private-window

# FORMAT

The format of the file contains one of the following line syntax:

> **prog** **"**_title_**"** _icon_ _program_ _options_

Where,

- **prog**

    The literal string **prog**.

- **"**_title_**"**

    The title of the toolbar item, which will appear as a tool-tip for the
    program button, enclosed in double quotes (`"`).

- _icon_

    The icon to display on the toolbar button.  May be specified as a single
    dash (`-`) when no icon is provided.  When no icon is provided, the
    _title_ text will be displayed on the button in place of the icon.

- _program_

    The executable program (full path or executable name) to run when the
    button is pressed.

- _options_

    Options and arguments that are passed to _program_.

Lines beginning with a hash (`#`) are comment lines.  Comment lines and
blank lines are ignored.

# EXAMPLES

Following is an example that places a number of toolbar buttons on the
[icewm(1)](icewm.md) panel:

    prog "File Manager" file-manager.png pcmanfm
    prog "Web Browser" web-browser.png /usr/lib/firefox/firefox
    prog "Terminal" terminal.png roxterm
    prog "Graphical Editor" text-editor.png gvim -f
    prog "Calculator" accessories-calculator.png calculator
    prog "Run Command" gtk-execute.png xde-run
    prog "Network" gtk-network.png pcmanfm ~/Network
    prog "Logout" system-log-out.png xde-logout

# FILES

Locations for the toolbar options file are as follows:

- `$ICEWM_PRIVCFG/toolbar`
- `$XDG_CONFIG_HOME/icewm/toolbar`
- `$HOME/.icewm/toolbar`
- `/etc/icewm/toolbar`
- `/usr/share/icewm/toolbar`

# SEE ALSO

[icewm(1)](icewm.md),
[icewm-programs(5)](icewm-programs.md),
[icewm-menu(5)](icewm-menu.md),
[icewm-menu-fdo(1)](icewm-menu-fdo.md).

# AUTHOR

[Brian Bidulock](mailto:bidulock@openss7.org).

# LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution.

| ------------: | :--------- |
| [Index](/man) | [![IceWM](/images/logom.jpg "ice-wm.org")](https://ice-wm.org "ice-wm.org") |
