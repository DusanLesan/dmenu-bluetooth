## Fork Changes Compared to Layerex Version
- Rewritten for easier use as a status bar element for [dwmblocks-async](https://github.com/UtkarshVerma/dwmblocks-async) or similar programs.
- Fixed and made the status functionality default.
- Status now displays device battery state in addition to the alias.
- Input arguments are replaced with the environment variable `BLOCK_BUTTON` to control the script.
- Code is greatly simplified while maintaining similar functionality.
- Some effort was put into optimizing the script by reducing unnecessary calls to `bluetoothctl`.

<div align="center">
<h3>dmenu-bluetooth</h3>
<img src="https://github.com/ClydeDroid/rofi-bluetooth/raw/master/.meta/menu.gif">

`bluetoothctl` `rofi` `dmenu`

</div>

## Installation
### Manually

Install dependencies: dmenu and bluetoothctl (provided by `bluez-utils` in Arch)

## Usage

- Run `dmenu-bluetooth` without anything else to get device status (bluetooth icon + alias and battery percent for each connected device)
- Run `BLOCK_BUTTON=1 dmenu-bluetooth` to be prompted with the menu
- Edit `prompt` function to change display options or the whole menu program

#### `NOTE:` In order to properly display the bluetooth icon, you will need to use an iconic font in your bar, e.g. [Nerd Fonts](https://github.com/ryanoasis/nerd-fonts). You can even use nerd fonts as a device alias for more compact status output.


### Thanks for the inspiration!

- [firecat53/networkmanager-dmenu](https://github.com/firecat53/networkmanager-dmenu)
- [x70b1's bluetoothctl polybar script](https://github.com/polybar/polybar-scripts/tree/master/polybar-scripts/system-bluetooth-bluetoothctl)
