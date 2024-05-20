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

This GTK theme is based on the [Colloid](https://github.com/vinceliuice/Colloid-gtk-theme) theme made by [vinceliuice](https://github.com/vinceliuice)


## Installation
This GTK theme requires:
- GTK >=3.20
- Python 3+

<details open>
  <summary>Automated script</summary>
  We provide a Python script to automate the process of installing the theme:

  ```
  curl -LsS "https://raw.githubusercontent.com/catppuccin/gtk/main/install.py" -o install.py
  python3 install.py <flavor> <accent>
    [catppuccin-gtk] [INFO] - Installation info:
        flavor:     mocha
        accent:     blue
        dest:       /home/****/.local/share/themes
        link:       False

        remote_url: https://github.com/catppuccin/gtk/releases/download/v1.0.0-alpha/catppuccin-mocha-blue-standard+default.zip
    [catppuccin-gtk] [INFO] - Starting download...
    [catppuccin-gtk] [INFO] - Response status: 200
    [catppuccin-gtk] [INFO] - Download finished, zip is valid
    [catppuccin-gtk] [INFO] - Verifying download..
    [catppuccin-gtk] [INFO] - Download verified
    [catppuccin-gtk] [INFO] - Extracting...
    [catppuccin-gtk] [INFO] - Extraction complete
    [catppuccin-gtk] [INFO] - Theme installation complete! 
  ```
</details>

<details>
  <summary>Arch Linux</summary>
  With your favourite AUR helper, you can install your theme of choice:

  ```bash
  yay -S catppuccin-gtk-theme-<flavor>
  paru -S catppuccin-gtk-theme-<flavor>
  ```
</details>

<details>
  <summary>Nix</summary>

  We have created a Nix module (<a href="https://github.com/catppuccin/nix">catppuccin/nix</a>) for theming apps under Nix, and recommend that you use it.
  You can set up our Nix module for GTK with the following config:
  ```nix
  {inputs, ...}: {
    imports = [inputs.catppuccin.homeManagerModules.catppuccin];

    gtk = {
      enable = true;
      catppuccin = {
        enable = true;
        flavor = "mocha";
        accent = "pink";
        size = "standard";
        tweaks = [ "normal" ];
      };
    };
  }
  ```
  > [!TIP]
  > For further information on the options available with our module, see the [full documentation](https://github.com/catppuccin/nix/blob/main/docs/home-manager-options.md#gtkcatppuccinenable).

  Alternatively, if you are not using our Nix module, you can grab the theme from <a href="https://github.com/NixOS/nixpkgs/blob/master/pkgs/data/themes/catppuccin-gtk/default.nix">nixpkgs/catppuccin-gtk</a>.
</details>

<details>
  <summary>Manual installation</summary>
  If your distro does not package our theme, and the installation script will not work for your use case, you can pull down releases and extract them yourself.

  ```bash
  cd ~/.local/share/themes

  local ROOT_URL="https://https://github.com/catppuccin/gtk/releases/download"
  local RELEASE = "v1.0.0"
  local FLAVOR = "mocha"
  local ACCENT = "mauve"
  curl -LsS "${ROOT_URL}/${RELEASE}/catppuccin-${FLAVOR}-${ACCENT}-standard+default.zip"

  unzip catppuccin-${FLAVOR}-${ACCENT}-standard+default.zip

  export THEME_DIR="~/.local/share/themes/catppuccin-${FLAVOR}-${ACCENT}-standard+default"

  # Optionally, add support for libadwaita
  mkdir -p "${HOME}/.config/gtk-4.0" && 
  ln -sf "${THEME_DIR}/gtk-4.0/assets" "${HOME}/.config/gtk-4.0/assets" &&
  ln -sf "${THEME_DIR}/gtk-4.0/gtk.css" "${HOME}/.config/gtk-4.0/gtk.css" &&
  ln -sf "${THEME_DIR}/gtk-4.0/gtk-dark.css" "${HOME}/.config/gtk-4.0/gtk-dark.css"
  ```
</details>

## Building
If our prebuilt offerings do not match your requirements, you will have to build the theme from source.

### Requirements
- Python 3+
- `sassc`, the Sass compiler

> [!WARNING]
> We use a submodule to bring in colloid, the theme this theme is based on. You will need to clone
> with `git clone <url> --recurse-submodules` to bring in the submodule.

To build the theme, simply invoke `build.py`:
```bash
python3 build.py mocha --dest ./build -a rosewater --tweaks rimless
  [catppuccin-gtk] [INFO] - Patches seem to be applied, remove "colloid/.patched" to force application (this may fail)
  [catppuccin-gtk] [INFO] - Building temp tweaks file
  [catppuccin-gtk] [INFO] - Inserting gnome-shell imports
  [catppuccin-gtk] [INFO] - Building main theme
  [catppuccin-gtk] [INFO] - Build info:
      build_root: ./build
      theme_name: catppuccin
      flavor:     mocha
      accent:     rosewater
      size:       standard
      tweaks:     Tweaks(tweaks=['rimless'])
  [catppuccin-gtk] [INFO] - Building into './build/catppuccin-mocha-rosewater-standard+rimless'...
  [catppuccin-gtk] [INFO] - Main build complete
  [catppuccin-gtk] [INFO] - Bundling assets...
  [catppuccin-gtk] [INFO] - Asset bundling done
  [catppuccin-gtk] [INFO] - Done!
```

You can now find the built theme under `./build`. If you want to package the theme up as a zip instead, pass `--zip` to the build script.

## Development

### Requirements
- All the [requirements for building](#building)
- `whiskers`, optionally, from [catppucin/toolbox](https://github.com/catppuccin/toolbox/tree/main/whiskers#installation)

We patch upstream colloid through a series of `.patch` files, applied through `git apply` once when the build begins.
The patches are located in `./patches/colloid/`. 
<br>
> [!TIP]
> Once the build script patches the submodule, it will write a file into
> `colloid/.patched`, to signal to future invocations that the patches have already been applied.
> If you need to change the patches, reset the submodule and rerun the build script.

The palette patches are generated through `whiskers`,
so if you're changing them, they will need regenerated. Simply run `whiskers palette.tera` to rebuild them.

The process for building the theme is [documented above](#building).

## Notes

### GDM theming
In order to theme the GDM theme, install the `gdm-settings` app, select the Catppuccin theme, and click *Save*.

## 💝 Thanks to

**Current maintainers**

- [nullishamy](https://github.com/nullishamy)
- [npv12](https://github.com/npv12)
- [ghostx31](https://github.com/ghostx31)
- [Syndrizzle](https://github.com/Syndrizzle)

**Contributions**

- [rubyowo](https://github.com/rubyowo) - CI and docs
- [braheezy](https://github.com/braheezy) - Instructions for the GDM theme

**Previous maintainer(s)**

- [sadrach-cl](https://github.com/sadrach-cl)

&nbsp;

<p align="center"><img src="https://raw.githubusercontent.com/catppuccin/catppuccin/main/assets/footers/gray0_ctp_on_line.svg?sanitize=true" /></p>
<p align="center">Copyright &copy; 2021-present <a href="https://github.com/catppuccin" target="_blank">Catppuccin Org</a>
<p align="center"><a href="https://github.com/catppuccin/gtk/blob/main/LICENSE"><img src="https://img.shields.io/static/v1.svg?style=for-the-badge&label=License&message=GPLv3&logoColor=d9e0ee&colorA=363a4f&colorB=b7bdf8"/></a></p>
