---
title: "icewm-theme(5)"
---
## NAME

    icewm-theme - icewm theme configuration file

## SYNOPSIS

    $ICEWM_PRIVCFG/theme
    $XDG_CONFIG_HOME/icewm/theme
    $HOME/.icewm/theme
    /etc/icewm/theme
    /usr/share/icewm/theme

## DESCRIPTION

The `theme` file contains the name of the default theme.  On startup
**icewm** reads this file to obtain the theme name, unless **icewm** was
started with the **--theme** option.  Whenever a different theme is
selected from the **icewm** Menu then the theme file is overwritten with
the name of the selected theme.

## FORMAT

This theme file contains the keyword `Theme`, followed by an equals
sign, followed by a double-quoted string with the theme name.  The theme
name is the name of the theme directory, followed by a slash, followed
by the theme file.

Usually the theme file is just `default.theme`, but a theme may have
alternatives.  Alternatives are small tweaks of a theme.  These are
specified in their own `.theme` file, which replaces `default.theme`.

If no theme file exists then **icewm** will use the default setting of
`Theme="icedesert/default.theme"`.

## EXAMPLES

Following is a `theme` file.  The comments show that [icewm(1)](icewm) keeps
a history of previous theme settings.

    Theme="CrystalBlue/default.theme"
    #Theme="icedesert/default.theme"
    ##Theme="default/default.theme"

## FILES

Locations for the `theme` file are as follows:

    $ICEWM_PRIVCFG/theme
    $XDG_CONFIG_HOME/icewm/theme
    $HOME/.icewm/theme
    /etc/icewm/theme
    /usr/share/icewm/theme

The locations are searched in the order listed; the first file found is
read and the remainder ignored.

## SEE ALSO

[icewm(1)](icewm),
[icewm-preferences(5)](icewm-preferences),
[icewm-prefoverride(5)](icewm-prefoverride).

## AUTHOR

[Brian Bidulock](mailto:bidulock@openss7.org).

## LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution.

| ------------: | :--------- |
| [Index](/man) | [![IceWM](/images/logom.jpg "ice-wm.org")](https://ice-wm.org "ice-wm.org") |
