# Notes

Read after https://wiki.archlinux.org/title/General_recommendations#Power_management

## Core utilities

- [ ] Find or invent the command `ls-or-cat`

## Emacs

- [ ] Emacs doesn't respect the .editorconfig in home directory; fix this
- [x] Alias for emacsclient as emacs

## pacman

- [ ] Drop-in pacman config file for NoExtract option
- [ ] Make the NoExtract string under pacman hook section in Reflector article, precise; it is etc/pacman.d/mirrorlist
- [ ] Check reflector development status
- [ ] Read https://wiki.archlinux.org/title/Pacman/Tips_and_tricks#Removing_unused_packages_(orphans)

## Sound

- [ ] Mute leds are not working while connecting to Bluetooth headset

## Sway

- [ ] Remove titlebar from applications
- [ ] Read https://wiki.archlinux.org/title/Sway#Control_swaynag_with_the_keyboard

### Display

- [ ] System dark mode
- [ ] Make color temperature adjustment work (https://wiki.archlinux.org/title/Sway#Color_temperature_adjustment)
- [ ] Fix that kanshi is not applied after applying new Sway config with $mod+Shift+c
- [x] Add a section about kanshi to Sway

### Status bar

- [ ] Network indicator in status bar
- [ ] Colorize battery status
- [ ] Show bluetooth connection status in statusbar

## Zsh

- [x] Fix that Delete key puts tilde in terminal (~)

### Autosuggestions

- [ ] Zsh in the second footclient does not have autosuggestions
- [ ] Make Zsh autosuggestions suggest things WRT the current directory
- [ ] Find a way to select the first word instead of the whole command when autosuggestion suggested a command
- [ ] Make autosuggestion work even if the given word is not matched in order
