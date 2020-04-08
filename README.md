# steamos-fg

## What is this for?

When using the SteamOS compositor, some games start behind the big picture UI and no graphics are displayed. This script forces such games to be shown in the foreground.

Affected games this script fixes include:

 - Dead Cells
 - Dirt Rally
 - Civilization VI
 - The Count Lucanor
 - Mad Max
 - Mirror's Edge (Steam Play)

Also games installed as snaps and flatpaks do share this fate and can be fixed by wrapping them with this script.

## Installation

Run the following command:

`sudo curl https://raw.githubusercontent.com/alkazar/steamos-fg/master/steamos-fg -o /usr/local/bin/steamos-fg && sudo chmod a+x /usr/local/bin/steamos-fg`

## Usage

### Steam games

Add `steamos-fg %command%` to the launch options for each game you wish to use this script with.

### Games imported from desktop shortcuts

You can do this is by editing the `.desktop` files and prepending the command with the script path.

Example locations of `.desktop` files, here for Debian/Ubuntu:

||system-wide|user|
|---:|:---|:---|
|**Snap**|`/var/lib/snapd/desktop/applications`|-|
|**Flatpak**|`/var/lib/flatpak/exports/share/applications`|`${HOME}/.local/share/flatpak/exports/share/applications`|

There is a gotcha however: In its "Add Desktop Shortcut" GUI, Steam ignores all desktop shortcuts where the exacutable has steam in the filename (the arguments are fine).

To fix this, create a link to `steamos-fg` with a different name:

```
ln -s /usr/local/bin/steamos-fg /usr/local/bin/gameros-fg
```

Then you can change those `.desktop` files by prepending `/usr/local/bin/gameros-fg` to the value of the `Exec` property:

Snap example:

```
Exec=/usr/local/bin/gameros-fg env BAMF_DESKTOP_FILE_HINT=/var/lib/snapd/desktop/applications/xyz.desktop /snap/bin/xyz %U
```

Flatpak example:

```
Exec=/usr/local/bin/gameros-fg /usr/bin/flatpak run --branch=stable --arch=x86_64 --command=xyz xyz
```

## Notes

This script was tested on Arch and Ubuntu and has been reported to work on SteamOS.

On Arch, you will need the `xorg-xwininfo`, `xorg-xprop`, `procps-ng` and `xdotool` packages.

On Ubuntu, you will need the `x11-utils`, `procps` and `xdotool` packages.
