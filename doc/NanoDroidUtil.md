Table of Contents
=================

   * [NanoDroid-Util Script](#nanodroid-util-script)
      * [Purpose](#purpose)
      * [Invocation](#invocation)
      * [Feature overview](#feature-overview)
         * [Fix OTA-Update issues](#fix-ota-update-issues)
         * [Airplane Mode settings](#airplane-mode-settings)
         * [Prevent audio focus stealing](#prevent-audio-focus-stealing)
         * [Prevent clipboard reading](#prevent-clipboard-reading)
         * [Read boot count](#read-boot-count)

Created by [gh-md-toc](https://github.com/ekalinin/github-markdown-toc)

# NanoDroid-Util Script

## Purpose

The `nanodroid-util` Script, respectively it's shortcut `nutl` is used by NanoDroid to perform various actions:

* fix navigation bar, status bar or lock screen issues after OTA update
* change Airplane Mode radio settings
* prevent applications from stealing audio focus
* prevent applications from reading the clipboard
* display device's boot count
  * requires Android 7.0 or newer

## Invocation

From within a terminal on your device, for example `adb shell` or `Termux` invoke the script using either

`nanodroid-util [switch] [parameter(s)]`

or

`nutl [switch] [parameter(s)]`

## Feature overview

### Fix OTA-Update issues

`-f`, `--fix-update`

fix issues with the navigation bar, status bar or lock screen after applying an OTA update; for a detailed description about this check [> XDA](https://www.xda-developers.com/broken-navigation-bar-lock-screen-ota-update/)

### Airplane Mode settings

`-a`, `--airplane-mode`

change Airplane Mode settings, this is interactive, user will be given instructions what to do. This allows to change which radios are disabled by Airplane Mode **and additionally** it instructs Android that it does **not** allow re-activation of **those** radios until Airplane Mode is switched off

### Prevent audio focus stealing

`-F`, `--audio-focus` [app]

some apps stop audio playback of other apps, when you bring them in foreground (or activate them in multi window mode), with this you can prevent Android from allowing this; [app] is the application name in `com.organisation.application` format, for example `com.xda.labs`

### Prevent clipboard reading

`-B`, `--read-clipboard` [app]

many apps have the permission to read the clipboard for no reason, with this you can prevent Android from allowing this; [app] is the application name in `com.organisation.application` format, for example `com.xda.labs`

**Note:** don't do this in applications like Browsers or the-like, as you'll disable the whole copy-paste feature for those app(s) with this feature

### Read boot count

`-b`, `--boot-count`

show how often the device was booted; requires Android 7.0 or newer

### Reset GCM Connection

You can reset GCM connection of all apps using

`-r`, `--reset-gms-data`

or for a single app using

`-r [appid]`, `--reset-gms-data [appid]`

this is especially useful when the ROM in use previously had GApps installed and now you're not receving any push messages anymore.

### Reset Permissions

In a rare corner case applications are not granted permission to access camera or storage, despite the user granted the corresponding permission, using

`-R`, `--reset-permissions`

followed by a reboot will fix this issue.
