<img align="left" alt="Gradience" src="https://github.com/GradienceTeam/Gradience/raw/main/data/icons/hicolor/scalable/apps/com.github.GradienceTeam.Gradience.svg">

# Gradience

Change the look of Adwaita, with ease

![Gradience with Adwaita Light](https://github.com/GradienceTeam/Design/raw/main/Screenshots/colors.png)

Gradience is a tool for customizing Libadwaita applications and the adw-gtk3 theme.

> **Warning**
> [Gradience, stopthemingmy.app and Adwaita Developers](#gradience-stopthemingmyapp-and-adwaita-developers)

<details>
  <summary>More screenshots</summary>
  
  ![Monet Tab](https://github.com/GradienceTeam/Design/raw/main/Screenshots/monet_purple.png)
  
  ![Proof of work](https://github.com/GradienceTeam/Design/raw/main/Screenshots/proof_purple.png)
</details>

[![Flatpak build](https://github.com/GradienceTeam/Gradience/actions/workflows/flatpak.yml/badge.svg)](https://github.com/GradienceTeam/Gradience/actions/workflows/flatpak.yml)
[![Copr build status](https://img.shields.io/badge/dynamic/json?color=blue&label=copr&query=builds.latest.state&url=https%3A%2F%2Fcopr.fedorainfracloud.org%2Fapi_3%2Fpackage%3Fownername%3Dlyessaadi%26projectname%3Dgradience%26packagename%3Dgradience%26with_latest_build%3DTrue)](https://copr.fedorainfracloud.org/coprs/lyessaadi/gradience/package/gradience/)
[![Flathub](https://img.shields.io/badge/dynamic/json?color=informational&label=downloads&logo=flathub&logoColor=white&query=%24.installs_total&url=https%3A%2F%2Fflathub.org%2Fapi%2Fv2%2Fstats%2Fcom.github.GradienceTeam.Gradience)](https://beta.flathub.org/apps/details/com.github.GradienceTeam.Gradience)
[![Translate on Weblate](https://hosted.weblate.org/widgets/GradienceTeam/-/svg-badge.svg)](https://hosted.weblate.org/engage/GradienceTeam)
[![Chat on Matrix](https://img.shields.io/matrix/Gradience:matrix.org?label=matrix&logo=matrix)](https://matrix.to/#/#Gradience:matrix.org)
[![Chat on Discord](https://img.shields.io/discord/1013779899821064202?label=discord&logo=discord&logoColor=white)](https://discord.com/invite/MYa8Sr7btJ)

<!--[![Flatpak build - Nightly](https://github.com/GradienceTeam/Gradience/actions/workflows/flatpak-nightly.yml/badge.svg)](https://github.com/GradienceTeam/Gradience/actions/workflows/flatpak-nightly.yml)-->

## Download

Gradience is available on Flathub.

<a href="https://beta.flathub.org/apps/details/com.github.GradienceTeam.Gradience">
    <img width="200" alt="Download on Flathub" src="https://flathub.org/assets/badges/flathub-badge-i-en.svg"/>
</a>

## Building and Installing

Gradience can be installed using multiple methods.

- Flathub (Recommended)
- As RPM package
- As DEB package (not available yet)
- From AUR

### Flatpak

Gradience is available on Flathub. You can install it using the following command:

```bash
flatpak install flathub com.github.GradienceTeam.Gradience
```

### COPR 

Gradience is available on COPR. You can install it using the following command:

```bash
dnf copr enable lyessaadi/gradience
dnf install gradience
```

### Debian (And derivates)

> **Warning**
> Not available yet. If you want, submit a PR.

### AUR 

Gradience is available on AUR. You can install it using the following command:

```bash
yay -S gradience # or gradience-git
```

### Building from source

#### Requirements

- Python 3 `python`
- PyGObject `python-gobject`
- Blueprint [`blueprint-compiler`](https://jwestman.pages.gitlab.gnome.org/blueprint-compiler/setup.html)
- GTK 4 `gtk4`
- Libadwaita (>= 1.2.alpha) `libadwaita`
- Libsoup 3 (>= 3.2.0) `libsoup`
- Meson `meson`
- Ninja `ninja-build`

Install required Python libraries:

```sh
pip install -r requirements.txt
```

### Global installation

```sh
git clone https://github.com/GradienceTeam/Gradience.git
cd Gradience
meson builddir --prefix=/usr/local
sudo ninja -C builddir install
```

### Local build (for testing and development purposes)

```sh
git clone https://github.com/GradienceTeam/Gradience.git
cd Gradience
meson builddir
meson configure builddir -Dprefix="$(pwd)/builddir"
ninja -C builddir install
ninja -C builddir run
```

> **Note** 
> During testing and developement, as a convenience, you can use the `local.sh` script to quickly rebuild local builds.

### Building using flatpak-builder

1. Open Terminal
2. Run `git clone https://github.com/GradienceTeam/Gradience.git && cd Gradience`
3. Install the `43` version of GNOME runtime and SDK: `flatpak install org.gnome.Sdk//43 org.gnome.Platform//43`
4. Run: `flatpak-builder --install --user --force-clean repo/ build-aux/flatpak/com.github.GradienceTeam.Gradience.Devel.json`

Alternatively, open the project with GNOME Builder, then build and run it.

## Theming Setup

> **Note** 
> You can also go to `Preferences` and apply overrides for Flatpak

### Libadwaita applications

No additional setup is required for native Libadwaita applications.

For Flatpak Libadwaita applications, you need to override their permissions:

- Run `sudo flatpak override --filesystem=xdg-config/gtk-4.0` or
- Use [Flatseal](https://github.com/tchx84/Flatseal) and adding `xdg-config/gtk-4.0` to **Other files** in the **Filesystem** section of **All Applications**

### Vanilla GTK 4 applications

Use [this guide](https://github.com/lassekongo83/adw-gtk3/blob/main/gtk4.md) to theme vanilla GTK 4 applications.

### GTK 3 applications

- Install and apply the [adw-gtk3](https://github.com/lassekongo83/adw-gtk3#readme) theme (don't forget to install the Flatpak package!)
- For Flatpak applications, you need to override their permissions:
  - Run `sudo flatpak override --filesystem=xdg-config/gtk-3.0` or
  - Use [Flatseal](https://github.com/tchx84/Flatseal) and adding `xdg-config/gtk-3.0` to **Other files** in the **Filesystem** section of **All Applications**

## Revert Theming

### Using app:

Press on the menu button in the headerbar and press `Reset Applied Color Scheme`

![Main Gradience menu](https://raw.githubusercontent.com/GradienceTeam/Design/main/Screenshots/hamburger_menu.png)

### Manually:

Remove GTK 3 and GTK 4 configs:

- Run `rm -rf .config/gtk-4.0 .config/gtk-3.0`

Remove adw-gtk3 theme:

- Run `flatpak uninstall adw-gtk3` to remove Flatpak adw-gtk3 theme
- Run `rm -rf .themes/adw-gtk3 .themes/adw-gtk3-dark .local/share/themes/adw-gtk3 .local/share/themes/adw-gtk3-dark` to remove local adw-gtk3 theme

Reset Flatpak overrides:

- Run `sudo flatpak override --reset`

> **Warning**
> This will reset all Flatpak overrides, such as Firefox Wayland override

## Roadmap

See [`ROADMAP.md`](ROADMAP.md)

## Contribute

See [`CONTRIBUTING.md`](CONTRIBUTING.md) for more informations and a list of contributors

[![Contributors](https://contrib.rocks/image?repo=GradienceTeam/Gradience)](https://github.com/GradienceTeam/Gradience/graphs/contributors)

## About Name

Gradience was originally named Adwaita Manager.

You can see the meaning of Gradience on [Wiktionary](https://en.wiktionary.org/wiki/gradience).

The icon represents: _A Paint Roller repainting an Adwaita window, keeping it's functionality._

## Gradience, [stopthemingmy.app](https://stopthemingmy.app) and Adwaita Developers

Gradience Team is not against [stopthemingmy.app](https://stopthemingmy.app) and Adwaita Developers idea, Gradience is a tool for tinkers that want to theme their desktops at their liking, and not a tool for distributions to change theme in them by default, Gradience Team agrees with importance of unified look of Adwaita to make sure that all apps work right and Developers have unified and stable tool for creating their apps.
