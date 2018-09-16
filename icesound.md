---
title: "icesound(1)"
---
# NAME

    icesound - play audio files when interesting GUI events happen

# SYNOPSIS

**icesound** \[_OPTIONS_\]

# DESCRIPTION

The [icewm(1)](icewm.md) window manager can be configured to generate so-called
GUI events in response to interesting actions, like opening or closing
of application windows, switching of work space, etc.  GUI events are a
property of the root window.  [icewm(1)](icewm.md) changes this property when a
new GUI event occurs.  Interested applications can listen for changes to
this property.  GUI events are an optional feature of [icewm(1)](icewm.md).  It
must be explicitly enabled by giving the **--enable-guievents** option
during configuration.  There are nearly twenty GUI events defined.  The
**--list-sounds** option will show them.

**icesound** is an application, which is one of the [icewm(1)](icewm.md)
applications, which responds to these GUI events by playing audio files.
These sound files are `.wav` files located in a `sounds` sub-directory
in one of the [icewm(1)](icewm.md) configuration directories.

**icesound** supports several common audio interfaces.  These are: ALSA,
ESounD, OSS and libAO.  These must be enabled during configuration.
ALSA, OSS and libAO all require support for [libsndfile](https://en.wikipedia.org/wiki/Libsndfile), which is a
very common library to read audio files.

- **ALSA**

    **ALSA** is rather involved to program and it works, but this could use
    more testing.  It plays at most one sound at a time.

- **ESounD**

    The **ESounD** interface is much simpler to implement and this works very
    well, because the difficult details are handled by the **ESounD** Sound
    Daemon.  It supports mixing of sounds when multiple GUI events occur
    within a second.  This may be the best option currently.  It requires
    that [esd(1)](https://manned.org/esd.1) is running and that **icesound** can connect to it.

- **LibAO**

    **LibAO** is a cross-platform audio output library which is a convenient
    wrapper around a significant number of common audio interfaces.  It has
    a simple configuration file which is documented in the [libao.conf(5)](https://manned.org/libao.conf.5)
    manual page.

- **OSS**

    The _Open Sound System (OSS)_ is a cross-platform sound interface,
    which is fully supported by **icesound**.

When multiple audio interfaces are available **icesound** will examine
them all until it finds one which it can connect to and then use that
one.  By default it prefers them in the order of: **AO**, **ESD**,
**ALSA**, **OSS**.

# OPTIONS

## SPECIFIC OPTIONS

- **-d**, **--display**=_DISPLAY_

    X11 display used by [icewm(1)](icewm.md) (default: $DISPLAY).

- **-s**, **--sample-dir**=_DIRECTORY_

    Specifies a directory with sound files.  The default is:
    `$HOME/.config/icewm/sounds`, `$HOME/.icewm/sounds`, `CFGDIR/sounds`
    and `LIBDIR/sounds`.  See the output of `icewm --directories`.

- **-i**, **--interface**={**AO**\|**ESD**\|**ALSA**\|**OSS**}\[,{**AO**\|**ESD**\|**ALSA**\|**OSS**}\]\*

    Specifies the audio output interfaces. One or more of: **AO**, **ESD**,
    **ALSA**, **OSS** separated by commas (`,`).

- **-D**, **--device**=_DEVICE_

    Backwards compatibility only: the default device.
    Please prefer one of the **-A**, **-O** or **-S** options.

- **-O**, **--oss**=_DEVICE_

    Specifies the OSS device (default: `default`).

- **-A**, **--alsa**=_DEVICE_

    Specifies the ALSA device (default: `/dev/dsp`).

- **-S**, **--server**=_ADDR_\[**:**_PORT_\]

    Specifies the ESD server address and port number.
    For ESD the default is `localhost:16001`.

- **-z**, **--snooze**=_MILLISECONDS_

    Specifies the snooze interval between sound events
    in milliseconds.  Default is 500 milliseconds.

- **-p**, **--play**=_SOUND_

    Plays the given sound (name or number) and exits.

- **-l**, **--list-files**

    Lists the available sound file paths and exits.

- **--list-sounds**

    Lists the supported sound file names and exits.

- **--list-interfaces**

    Lists the supported audio interfaces and exits.

- **-v**, **--verbose**

    Be verbose and print some information when sound events occur.

## GENERAL OPTIONS

- **-h**, **--help**

    Print a brief usage statement to `stdout` and exit.

- **-V**, **--version**

    Print the program version to `stdout` and exit.

- **-C**, **--copying**

    Print copying permissions to `stdout` for the program and exit.

# EXIT STATUS

- **0**

    Success.

- **1**

    General error.

- **2**

    Command line error.

- **3**

    Subsystems error (i.e cannot connect to server).

# SEE ALSO

[icewm(1)](icewm.md),
[libao.conf(5)](https://manned.org/libao.conf.5),
[esd(1)](https://manned.org/esd.1),
[padsp(1)](https://manned.org/padsp.1),
[aplay(1)](https://manned.org/aplay.1),
[alsamixer(1)](https://manned.org/alsamixer.1).

# BUGS

**icesound** had no known bugs at the time of release.  Please report bugs
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
| [Index](/man) | [![IceWM][/images/logom.jpg "ice-wm.org"]](https://ice-wm.org "ice-wm.org") |
