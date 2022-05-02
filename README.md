**_This repo is no longer maintained as I no longer run Ubuntu so have no way to test this._**

# NordVPN-Local
<img align="right" src="img/screenshot.png">
A Gnome extension that shows your NordVPN status in the top bar, features a menu showing the current status and a button to Connect / Disconnect.

Source: https://github.com/ThatRobVK/NordVPN-Local

## What it does
When disconnected, the top bar will show a red button reading `UNPROTECTED`, to remind you that you are not connected to the VPN. When connecting or disconnecting the button turns amber, and once connected it will turn green showing you the country and server number you are connected to, e.g. `UNITED KINGDOM #813`. When you click the button it will show the full command-line output of the command `nordvpn status` in the menu. Undearneath the status is a button that allows you to connect / disconnect.

### How it's different 
This is loosely based on Quadipedia's NordVPN Status extension (found on the Gnome extensions site), kudos to them for creating the original. Their version works by reading the server list from NordVPN's API and comparing the computer's public IP against this list. I found it often didn't pick up my active connection, which I suspect is due to incorrect API data.

This version uses the NordVPN command-line tools to determine the status. It updates as soon as you use the menu to connect or disconnect, and it refreshes every 30 seconds in case you change your connection external to the plugin.

Note that due to using the local command-line tools, this only works if you use NordVPN locally (hence the title). If your VPN connection is established outside of your computer, e.g. on your router, then this plugin __will not__ detect your VPN connection. Use Quasipedia's version instead, which will detect that, if it finds your public IP in the NordVPN server list.

## How to Install
This extension uses the NordVPN command line client, which can be set up as follows.

### Install NordVPN
1. Install NordVPN with `sudo apt install nordvpn`.
2. Configure your credentials with `nordvpn login`, following the prompts.
3. Check NordVPN is set up with `nordvpn c`, if it connects successfully then you're good to go.

### Install the extension
Easiest way: enable on gnome-extensions at [NordVPN Local on gnome extensions](https://extensions.gnome.org/extension/1656/nordvpn-local/)

Manual install:  
1. Create a folder for the extension with `mkdir ~/.local/share/gnome-shell/extensions/nordvpn-local@robvk.uk`
2. Copy the files from this repo into that folder
3. Enable the extension using `Tweaks` (if you don't have it, install via `sudo apt install gnome-tweaks`)

## Development

Contributions welcome! If you find any issues or think of any cool features, check it's not already been raised under Issues and raise it.
