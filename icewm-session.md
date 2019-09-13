---
title: "icewm-session(1)"
---
# NAME

    icewm-session - X.Org session manager provider with IceWM

# SYNOPSIS

**icewm-session** \[_OPTIONS_\]

# DESCRIPTION

icewm-session is an implementation of X.Org session manager and can be
run from X11 session setup. It runs **icewm** as default window manager
and handles the startup and life cycle control of the WM and all related
support applications.

# OPTIONS

## SPECIFIC OPTIONS

- **-c**, **--config=FILE**

    Let IceWM load preferences from _FILE_.

- **-t**, **--theme=FILE**

    Let IceWM load the theme _FILE_.

- **-i**, **--icewm=FILE**

    Use _FILE_ as the IceWM window manager.

- **-a**, **--alpha**

    Use a 32-bit visual for translucency.

- **-b**, **--nobg**

    Do not start icewmbg.

- **-n**, **--notray**

    Do not start icewmtray.
    This is only applicable if IceWM was explicitly configured
    to use an external icewmtray process.

- **-s**, **--sound**

    Also start icesound.

## GENERAL OPTIONS

- **-d**, **--display**=_DISPLAY_

    Use _DISPLAY_ to connect to the X server.
    If this option is missing then _DISPLAY_
    is read from the environment variable `DISPLAY`.

- **--sync**

    Use a slower synchronous mode communication with _X11_ server.

- **-h**, **--help**

    Print a brief usage statement to `stdout` and exit.

- **-V**, **--version**

    Print the program version to `stdout` and exit.

- **-C**, **--copying**

    Print copying permissions to `stdout` for the program and exit.

# USAGE

On startup icewm-session executes the following steps.
From the file `env` in the configuration directory
it loads additional environment variables, if that file exists.
Then it will start `icewmbg` to manage root background colors and images.
It may also start `icesound`, if this was enabled at configuration time.
Then `icewm` is started.

If there exists an executable script `startup` in the configuration
directory, it will be executed. It may contain commands to initialize X11
settings with `xset`, load keyboard configuration, start a compositing
manager like `compton` and load system tray applications.

When icewm exits or is told to exit, icewm-session will execute
a `shutdown` script, if it exists in the configuration directory.
When this finishes, icewm-session will terminate icewm, icewmbg
and icesound. Finally icewm-session will exit.

If the icewm process crashes then icewm-session will attempt to restart
it. If two such crashes occur in a short period, then icewm-session will
attempt to popup a dialog using either `xmessage`, `kdialog` or
`zenity`.  This dialog asks if the user wishes to continue restarting
icewm or abort execution of icewm-session.

# SEE ALSO

[icewm(1)](icewm),
[icewm-env(5)](icewm-env),
[icewm-shutdown(5)](icewm-shutdown),
[icewm-startup(5)](icewm-startup),
[icewmbg(1)](icewmbg).

# BUGS

**icewm-session** had no known bugs at the time of release.  Please report bugs
for current versions to the source code repository at
[Github](https://github.com/bbidulock/icewm/issues).

# AUTHOR

[Brian Bidulock](mailto:bidulock@openss7.org).

See **--copying** for full copyright notice and copying permissions.

# LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution or use the **--copying** flag
to display copying permissions.

| ------------: | :--------- |
| [Index](/man) | [![IceWM](/images/logom.jpg "ice-wm.org")](https://ice-wm.org "ice-wm.org") |
