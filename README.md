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
### From AUR

``` sh
yay -S dmenu-bluetooth
```

### Manually

Install dependencies: dmenu and bluetoothctl (provided by `bluez-utils` in Arch)

``` sh
wget "https://raw.githubusercontent.com/Layerex/dmenu-bluetooth/master/dmenu-bluetooth"
install dmenu-bluetooth /usr/local/bin
```

## Usage

```
usage: dmenu-bluetooth [--help] [--status] [--connected-icon [ICON]] [PROMPT] DMENU_ARGS...

A script that generates a dmenu menu that uses bluetoothctl to connect to bluetooth devices and display status info.

positional arguments:
  PROMPT                    dmenu prompt
  DMENU_ARGS...             arguments passed to dmenu

options:
--help                      show this help message and exit
--status                    print a short string about current bluetooth status and exit
--connected-icon [ICON]     add icon on device list next to connected devices

environment variables:
  DMENU_BLUETOOTH_PROMPT    dmenu prompt
  DMENU_BLUETOOTH_LAUNCHER  command to use instead of 'dmenu'

Positional arguments have to be placed after all other arguments.
A PROMPT positional argument will be interpreted as part of DMENU_ARGS if it starts with '-'. It won't be parsed if the DMENU_BLUETOOTH_PROMPT environment variable is set.
Use the DMENU_BLUETOOTH_LAUNCHER environment variable to use launchers other than dmenu. Rofi, fuzzel, and any dmenu-compatible launchers are supported.
```

### Polybar configuration

`NOTE:` In order to properly display the bluetooth icon, you will need to use an iconic font in your bar, e.g. [Nerd Fonts](https://github.com/ryanoasis/nerd-fonts)

```
[module/bluetooth]
type = custom/script
exec = dmenu-bluetooth --status
interval = 1
click-left = dmenu-bluetooth &
```

### i3 keybinding

```
bindsym $mod+b exec --no-startup-id dmenu-bluetooth
```

### Thanks for the inspiration!

- [firecat53/networkmanager-dmenu](https://github.com/firecat53/networkmanager-dmenu)
- [x70b1's bluetoothctl polybar script](https://github.com/polybar/polybar-scripts/tree/master/polybar-scripts/system-bluetooth-bluetoothctl)
