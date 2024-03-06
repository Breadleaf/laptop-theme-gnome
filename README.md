# My laptop theme

There is a LOT of customization that went into setting up my laptop. Here is the documentation to get to the final theme. This theme is not concrete, mess with it until it feels good to you!

## Bootstrap yay

My config uses a lot of AUR packages. I personally like to use `yay`, feel free to use whatever you would like.

First install go with `sudo pacman -S go` as yay will need it to build

Next run the following command `cd ~ && mkdir yay-bootstrap && touch yay-bootstrap/PKGBUILD`

Go to https://aur.archlinux.org/cgit/aur.git/tree/PKGBUILD?h=yay and copy that into `~/yay-bootstrap/PKGBUILD`

Run `makepkg PKGBUILD` in `~/yay-bootstrap/`

Navigate to `~/yay-bootstrap/pkg/yay/usr/bin/`

Run `./yay yay`

Remove `~/yay-bootstrap/`

## Gnome apps to install

### pacman

- https://archlinux.org/packages/extra/any/gnome-tweaks/
- https://archlinux.org/packages/extra/any/gnome-shell-extensions/

### yay

- https://aur.archlinux.org/packages/gdm-settings

## Gnome Extensions

### Install

#### yay

- https://aur.archlinux.org/packages/gnome-shell-extension-pop-shell-git

#### extensions.gnome.org

- https://extensions.gnome.org/extension/19/user-themes/
- https://extensions.gnome.org/extension/5090/space-bar/
- https://extensions.gnome.org/extension/1160/dash-to-panel/

### Configuration

#### User-Themes

See Below

#### Space-Bar

I used this to customize how the workspaces look in the top bar. Disable any keybinds as sxhkd will take care of it. I used different color heart emoji to signify different workspaces. I also used multitasking in gnome settings to set the fixed workspace size to 5; this is important for sxkhd to work.

#### Dash-To-Panel

I use this to make a custom top bar, mess with this until it looks good and acts how you like.

## Gnome Tweaks

### Setup

To install themes you will need to create `~/.themes/` and `~/.local/share/icons`

### Install

**NOTE** You may need to move subfolders into the main dirs listed above.

#### Icons

- https://www.gnome-look.org/p/1571937

#### Theme

- https://www.gnome-look.org/p/1977647/

## Hotkey Setup

### Install

- https://wiki.archlinux.org/title/Sxhkd

### Config

Put this in `~/.config/sxhkd/sxhkdrc`

```
# Move to another workspace

alt + 1
        wmctrl -s 0

alt + 2
        wmctrl -s 1

alt + 3
        wmctrl -s 2

alt + 4
        wmctrl -s 3

alt + 5
        wmctrl -s 4

# Move Window to another workspace

alt + shift + 1
        wmctrl -r :ACTIVE: -t 0 && wmctrl -s 0

alt + shift + 2
        wmctrl -r :ACTIVE: -t 1 && wmctrl -s 1

alt + shift + 3
        wmctrl -r :ACTIVE: -t 2 && wmctrl -s 2

alt + shift + 4
        wmctrl -r :ACTIVE: -t 3 && wmctrl -s 3

alt + shift + 5
        wmctrl -r :ACTIVE: -t 4 && wmctrl -s 4
```

### Autostart

Put this in `~/.config/autostart/sxhkd.desktop`

```
[Desktop Entry]
Name=sxhkd
Comment=Simple X hotkey daemon
Exec=/usr/bin/sxhkd
Terminal=false
Type=Application
```

Finally Reboot

## Dotfiles

Clone my dotfiles at https://github.com/breadleaf/dotfiles

**NOTE** As of Feb 12 2024 you will need to manually install the dotfiles, do not use any included scripts in the repo. Vim config is also iffy and should probably be ignored.

## Language Setup

I write in Japanese sometimes and like to have native Japanese typing ready to go. For this I use fcitx5 and mozc. To prevent a **lot** of pain, follow the steps I found to work as listed below:

- install yay fcitx5-configtool
- install sudo pacman -S fcitx5-mozc
- install sudo pacman -S https://archlinux.org/packages/extra/any/noto-fonts-cjk/
- start Fcitx5
- start Fcitx5-configtool
- uncheck only show current language
- search mozc
- create ~/.profile
- paste https://wiki.archlinux.org/title/Fcitx5 (section 2.1) into `~/.profile`
- open gnome tweaks
- find startup applications
- add fcitx5
- reboot
- start gnome keyboard settings
- add Japanese in languages list

NOTE: you might need to install fcitx5-qt or fcitx5-gtk

There is no guarantee this will work, these are the steps that finally got it to work for me.

## Optional Packages

## pacman

- https://archlinux.org/packages/extra/x86_64/fastfetch/
- https://archlinux.org/packages/extra/any/hyfetch/

## yay

- https://aur.archlinux.org/packages/visual-studio-code-insiders-bin
