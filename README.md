# What is this for?

When using the SteamOS compositor, some games start behind the big picture UI and no graphics are displayed. This script forces such games to be shown in the foreground.

Affected games this script fixes include:

 - Dead Cells
 - Dirt Rally
 - Civilization VI
 - The Count Lucanor
 - Mad Max

# Install

Run the following command:

`sudo curl https://raw.githubusercontent.com/alkazar/steamos-fg/master/steamos-fg -o /usr/local/bin/steamos-fg && sudo chmod a+x /usr/local/bin/steamos-fg`

# Usage

Add `steamos-fg %command%` to the launch options for each game you wish to use this script with.

# Notes

This script was tested on Arch and reported to work on Ubuntu and SteamOS.

On Arch, you will need the `xorg-xwininfo` and `xorg-xprop` packages.

On Ubuntu, you will need the `x11-utils` package.
