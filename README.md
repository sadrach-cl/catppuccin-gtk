<h3 align="center">
	<img src="https://raw.githubusercontent.com/catppuccin/catppuccin/main/assets/logos/exports/1544x1544_circle.png" width="100" alt="Logo"/><br/>
	<img src="https://raw.githubusercontent.com/catppuccin/catppuccin/main/assets/misc/transparent.png" height="30" width="0px"/>
	Catppuccin for <a href="https://gtk.org/">GTK</a>
	<img src="https://raw.githubusercontent.com/catppuccin/catppuccin/main/assets/misc/transparent.png" height="30" width="0px"/>
</h3>

<p align="center">
    <a href="https://github.com/catppuccin/gtk/stargazers"><img src="https://img.shields.io/github/stars/catppuccin/gtk?colorA=363a4f&colorB=b7bdf8&style=for-the-badge"></a>
    <a href="https://github.com/catppuccin/gtk/issues"><img src="https://img.shields.io/github/issues/catppuccin/gtk?colorA=363a4f&colorB=f5a97f&style=for-the-badge"></a>
    <a href="https://github.com/catppuccin/gtk/contributors"><img src="https://img.shields.io/github/contributors/catppuccin/gtk?colorA=363a4f&colorB=a6da95&style=for-the-badge"></a>
</p>

<p align="center">
  <img src="assets/res.webp"/>
</p>

# About

This GTK theme is based on the [Colloid](https://github.com/vinceliuice/Colloid-gtk-theme) theme made by [Vinceliuice](https://github.com/vinceliuice)

## Usage

### Requirements

-   GTK `>=3.20`
-   `gnome-themes-extra` (or `gnome-themes-standard`)
-   Murrine engine

### Installation

1. Download and extract the theme zip from [releases](https://github.com/catppuccin/gtk/releases/) or you can install the theme from the [AUR](#for-arch-linux-users).
2. Move the theme folder to **".themes"** in your home directory. **(~/.themes)** (Skip this step if you are using the AUR package)
3. Select the downloaded theme via your desktop specific tweaks application (**gnome-tweaks** on Gnome 3+).

### For Flatpak users

1. To give your Flatpaks access to your themes folder run:
  ```bash
  sudo flatpak override --filesystem=$HOME/.themes
  ```
2. To set the theme for all Flatpaks, replace `##theme##` with the name of the theme you want to use and run this command:
  ```bash
  sudo flatpak override --env=GTK_THEME=##theme##
  ```
3. For a more in depth tutorial see Hamza Algohary's tutorial on [It's Foss](https://itsfoss.com/flatpak-app-apply-theme/)

### For Arch Linux users

We have 4 AUR packages for all the 4 flavours of the theme:
- [Latte](https://aur.archlinux.org/packages/catppuccin-gtk-theme-latte)
- [Frappe](https://aur.archlinux.org/packages/catppuccin-gtk-theme-frappe)
- [Macchiato](https://aur.archlinux.org/packages/catppuccin-gtk-theme-macchiato)
- [Mocha](https://aur.archlinux.org/packages/catppuccin-gtk-theme-mocha)

With your favourite AUR helper, install them:
  ```bash
  yay -S catppuccin-gtk-theme-mocha catppuccin-gtk-theme-macchiato catppuccin-gtk-theme-frappe catppuccin-gtk-theme-latte
  ```

## Development

**Note**: Ensure that you have atleast python version 3.10 installed

Clone the repository using
```bash
git clone --recurse-submodules git@github.com:catppuccin/gtk.git
virtualenv -p python3 venv  # to be created only once and only if you need a virtual env
source venv/bin/activate  
pip install -r requirements.txt
```
To check out the install script, run 
```bash
python install.py --help
```

You can install any theme like the following example
```bash
python install.py mocha -a sky --tweaks rimless -d ~/.themes
```
You can build all possible variations of the theme possible using the following command and it will install it tot releases folder
```bash
python install.py all -a all
```

A few important notes to keep in mind

* `recolor.py` handles all changes that needs to be done to colloid to ensure it generated catppuccin colors. If vinceliuice changes anything in his theme in future, that is where you must change
* `var.py` includes all different variables that you can tinker around as per your personal requirements. 
* `create_theme.py` consists of a wrapper that will recolor the colloid theme, install it as per the args provided and rename it accordingly. 
 
## 💝 Thanks to

**Current maintainers**
- [npv12](https://github.com/npv12)
- [ghostx31](https://github.com/ghostx31)
- [Syndrizzle](https://github.com/Syndrizzle)

**Contributions**
- [rubyowo](https://github.com/rubyowo) - for working on the build and CI script

**Previous maintainer(s)**
- [sadrach-cl](https://github.com/sadrach-cl)

&nbsp;

<p align="center"><img src="https://raw.githubusercontent.com/catppuccin/catppuccin/main/assets/footers/gray0_ctp_on_line.svg?sanitize=true" /></p>
<p align="center">Copyright &copy; 2021-present <a href="https://github.com/catppuccin" target="_blank">Catppuccin Org</a>
<p align="center"><a href="https://github.com/catppuccin/gtk/blob/main/LICENSE"><img src="https://img.shields.io/static/v1.svg?style=for-the-badge&label=License&message=GPLv3&logoColor=d9e0ee&colorA=363a4f&colorB=b7bdf8"/></a></p>
