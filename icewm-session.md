---
title: "icewm-session(1)"
---
## NAME

    icewm-session - X.Org session manager provider with IceWM

## SYNOPSIS

**icewm-session** \[_OPTIONS_\]

## DESCRIPTION

icewm-session is an implementation of a X.Org session manager and can be
run from a X11 session setup. It runs **icewm** as default window manager
and controls the life cycle of related support applications.

## OPTIONS

## SPECIFIC OPTIONS

- **-c**, **--config=FILE**

    Let IceWM load preferences from _FILE_.

- **-t**, **--theme=FILE**

    Let IceWM load the theme _FILE_.

- **-i**, **--icewm=FILE**

    Use _FILE_ as the IceWM window manager.

- **-o**, **--output=FILE**

    Redirect all output to _FILE_.
    A leading tilde or environment variable is expanded.

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

    Use a slower synchronous mode communication with the _X11_ server.

- **-h**, **--help**

    Give a list of all supported options and exit.

- **-V**, **--version**

    Print the program version and exit.

- **-C**, **--copying**

    Print copying permissions and exit.

## DEBUGGING OPTIONS

- **-v**, **---valgrind**

    Let `/usr/bin/valgrind` run icewm.
    Thoroughly examines the execution of icewm.

- **-g**, **---catchsegv**

    Let `/usr/bin/catchsegv` run icewm.
    Gives a backtrace if icewm segfaults.

## USAGE

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

When icewm exits, icewm-session will execute a `shutdown` script,
if it exists in the configuration directory.
When this finishes, icewm-session will terminate icewm, icewmbg
and icesound. Finally, icewm-session will exit.

If the icewm process crashes then icewm-session will attempt to restart
it. If two such crashes occur in a short period, then icewm-session will
attempt to popup a dialog using either `yad`, `xmessage`, `kdialog`
or `zenity`.  This dialog presents a choice between restarting icewm,
starting a terminal, or abort execution of icewm-session.

## ENVIRONMENT

- **ICEWM\_OPTIONS**

    A space separated list of options which will be added to the command
    line invocation of `icewm`. This can be set in the `env` file.

## SEE ALSO

[icewm(1)](icewm),
[icewm-env(5)](icewm-env),
[icewm-shutdown(5)](icewm-shutdown),
[icewm-startup(5)](icewm-startup),
[icewmbg(1)](icewmbg).

## BUGS

Please report bugs at [Github](https://github.com/bbidulock/icewm/issues).

## AUTHOR

[Brian Bidulock](mailto:bidulock@openss7.org).

See **--copying** for full copyright notice and copying permissions.

## LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution or use the **--copying** flag
to display copying permissions.

| ------------: | :--------- |
| [Index](/man) | [![IceWM](/images/logom.jpg "ice-wm.org")](https://ice-wm.org "ice-wm.org") |
