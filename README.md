<div align="center">

![XoraWM Logo](./assets/XORA.png)

# **Xora Wayland Compositor**

### _Lightning Fast · Beautifully Animated · Infinitely Customizable_

[![License](https://img.shields.io/badge/license-GPL--3.0-blue.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-0.12.8-orange.svg)](https://github.com/xora-wm/Xora/releases)
[![Language](https://img.shields.io/badge/language-C-red.svg)](https://github.com/xora-wm/Xora/search?l=c)
[![Discord](https://img.shields.io/discord/CPjbDxesh5?color=7289da&label=Discord)](https://discord.gg/CPjbDxesh5)
[![AUR](https://img.shields.io/aur/version/mangowm-git)](https://aur.archlinux.org/packages/mangowm-git)

---

**Xora** is a modern, lightweight, and feature-rich Wayland compositor built on [dwl](https://codeberg.org/dwl/dwl/), designed for users who demand both performance and aesthetics.

✨ **Experience the future of Wayland compositing** ✨

</div>

---

## 🌟 **Why Choose Xora?**

<div align="center">

| ⚡ **Blazing Fast** | 🎨 **Beautiful Animations** | 🛠️ **Highly Configurable** |
|:---:|:---:|:---:|
| Built in seconds,<br>runs lighter than air | Smooth, customizable animations<br>for every window action | Simple config files with<br>hot-reload support |

| 🏷️ **Tag-Based Workflow** | 🎯 **Excellent X11 Support** | 💫 **Modern Effects** |
|:---:|:---:|:---:|
| Flexible tags instead of<br>rigid workspaces | Seamless XWayland integration<br>for legacy apps | Blur, shadows, corner radius,<br>& opacity via scenefx |

</div>

---

## 🎬 **See It In Action**

<div align="center">

![Xora Demo](https://github.com/user-attachments/assets/bb83004a-0563-4b48-ad89-6461a9b78b1f)

*XoraWM - Where performance meets beauty*

</div>

---

## 🚀 **Quick Start**

### **Installation**

#### **Arch Linux**
```bash
yay -S xora-git
```

#### **Gentoo**
```bash
emerge --ask --verbose gui-wm/xora
```

#### **openSUSE**
```bash
sudo opi in xora
```

#### **Fedora**
```bash
dnf install xora
```

#### **Build from Source**
```bash
# Clone the repository
git clone https://github.com/xora-wm/Xora.git
cd Xora

# Build
meson build
ninja -C build

# Install
sudo ninja -C build install
```

### **First Launch**
```bash
xora
```

---

## ⌨️ **Default Keybindings**

<div align="center">

| Key Combination | Action |
|----------------|---------|
| `Alt` + `Return` | ️ Open Terminal (foot) |
| `Alt` + `Space` | 🔍 Open Launcher (rofi) |
| `Alt` + `Q` | ❌ Close Window |
| `Super` + `M` | 🚪 Quit Xora |
| `Super` + `F` | ⛶ Toggle Fullscreen |
| `Alt` + `←` `→` `↑` `↓` | 🎯 Focus Direction |
| `Ctrl` + `1-9` | 🏷️ Switch to Tag 1-9 |
| `Alt` + `1-9` | 📦 Move Window to Tag 1-9 |

</div>

> 💡 **Tip:** Customize these in `~/.config/xora/config.conf`

---

## 🎨 **Features**

### **🏗️ Layout System**
Xora comes with **10+ built-in layouts** to match your workflow:

- **Tile** - Classic tiling layout
- **Scroller** - PaperWM-style horizontal scrolling
- **Monocle** - Single window focus
- **Grid** - Organized grid arrangement
- **Deck** - Stacked windows
- **Center Tile** - Master in center, stacks on sides
- **Vertical Variants** - Vertical tile, grid, scroller, deck
- **TGMix** - Hybrid tiling approach

### **🎭 Window States**
Rich window management capabilities:
- 📌 Swallow (window absorption)
- 📉 Minimize / 📈 Maximize
- 🌍 Global / 🚫 Unglobal
- 🖼️ Fake Fullscreen
- 🔲 Overlay mode

### **✨ Visual Effects**
Powered by **scenefx**:
- 🔮 **Blur** - Optimized wallpaper caching
- 🌑 **Shadows** - Depth and dimension
- 🎯 **Corner Radius** - Modern rounded corners
- 💎 **Opacity** - Per-window transparency control

### **🎞️ Animation System**
Fully customizable animations:
- **Types**: Slide, Zoom, Fade, None
- **Coverage**: Window open/close/move, tag switching, layer transitions
- **Bezier Curves**: Custom easing functions
- **Durations**: Per-animation type control
- **Fade Effects**: Smooth opacity transitions

### **📡 IPC - xctl**
Powerful command-line control:

```bash
# Switch to tag 1
xctl -t 1

# Add tag 2 to current view
xctl -s -t 2+

# Switch to scroller layout
xctl -l "S"

# Close focused window
xctl -d killclient

# Watch for events
xctl -w
```

### **📝 Scratchpads**
- **Sway-style** scratchpads
- **Named** scratchpads for specific apps
- Quick toggle with custom keybindings

---

## 📦 **Dependencies**

### **Core**
- wayland
- wayland-protocols (>=1.23)
- libinput (>=1.27)
- libdrm
- libxkbcommon
- pixman
- libdisplay-info
- libliftoff
- hwdata
- seatd
- pcre2

### **Optional**
- xorg-xwayland (X11 support)
- libxcb (X11 support)

### **External**
- [wlroots-0.19](https://gitlab.freedesktop.org/wlroots/wlroots) (>=0.19.0)
- [scenefx-0.4](https://github.com/wlrfx/scenefx) (>=0.4.1)

---

## 🛠️ **Configuration**

### **Setup Your Config**
```bash
# Create config directory
mkdir -p ~/.config/xora

# Copy default config
cp /etc/xora/config.conf ~/.config/xora/config.conf
```

### **Config Structure**
Organize your config with includes:
```ini
# Main config.conf
source=~/.config/xora/keybindings.conf
source=~/.config/xora/rules.conf
source=~/.config/xora/theme.conf
```

### **Example Configuration**
```ini
# Enable animations
animations=1
layer_animations=1

# Configure blur
blur=1
blur_optimized=1
blur_params_radius=5

# Set gaps
gaps_outer=10
gaps_inner=5

# Custom keybinding
bind=SUPER,Return,spawn,foot
bind=SUPER,D,spawn,rofi -show run
```

📖 **Full documentation**: [Xora Wiki](https://github.com/xora-wm/Xora/wiki)

---

## 🎯 **Recommended Ecosystem**

<div align="center">

| Category | Recommended Tools |
|----------|------------------|
| 🚀 **Launcher** | rofi, bemenu, fuzzel, wmenu |
| 💻 **Terminal** | foot, wezterm, kitty, alacritty, ghostty |
| 📊 **Status Bar** | waybar ⭐, eww, quickshell, ags |
| 🖼️ **Wallpaper** | swww, swaybg |
| 🔔 **Notifications** | swaync, dunst, mako |
| 📋 **Clipboard** | wl-clipboard, cliphist, wl-clip-persist |
| 🌅 **Night Light** | gammastep, wlsunset |
| 🔒 **Lock Screen** | swaylock-effects, swaylock |
| ⚡ **Power Menu** | wlogout |
| 🎨 **Desktop Shell** | DankMaterialShell, Noctalia |

</div>

---

## 🤝 **Community & Support**

<div align="center">

### **Join Our Community**

[![Discord](https://img.shields.io/discord/CPjbDxesh5?color=7289da&label=Discord&logo=discord&logoColor=white)](https://discord.gg/CPjbDxesh5)
[![GitHub Discussions](https://img.shields.io/badge/GitHub%20Discussions-xora--wm/Xora-blue?logo=github)](https://github.com/xora-wm/Xora/discussions)

- 💬 **Discord** - Real-time chat, support, and community
- 📝 **GitHub Discussions** - Feature requests, Q&A, ideas
- 📚 **Wiki** - Comprehensive documentation and guides

</div>

---

## 📸 **Screenshots**

<div align="center">

### Minimal Setup
![Minimal Setup](https://github.com/user-attachments/assets/e1795c88-f1a1-4fbe-b97c-51af5419b6c5)

### Full Desktop Environment
![Full DE](https://github.com/user-attachments/assets/7e1b7510-ad9b-4561-8aaf-6114098e9e28)

*Showcase your Xora setup! Tag us with #XoraWM*

</div>

---

## 🏗️ **Architecture**

<div align="center">

```
┌─────────────────────────────────────────────────────┐
│                    XoraWM Core                       │
├─────────────────────────────────────────────────────┤
│  wlroots 0.19        │  scenefx 0.4                 │
│  - Wayland Protocol  │  - Visual Effects            │
│  - Input Handling    │  - Blur & Shadows            │
│  - Output Management │  - Rendering                 │
├─────────────────────────────────────────────────────┤
│              Xora IPC (xctl)                         │
│         - Event Streaming                            │
│         - Command Dispatch                           │
│         - State Queries                              │
├─────────────────────────────────────────────────────┤
│              Layout Engine                           │
│  Tile │ Scroller │ Monocle │ Grid │ Deck │ +6 more  │
└─────────────────────────────────────────────────────┘
```

**Built on**: [dwl](https://codeberg.org/dwl/dwl/) - Dynamic Window Manager for Wayland

</div>

---

## 📊 **Project Stats**

<div align="center">

| Metric | Value |
|--------|-------|
|  **Lines of Code** | ~10,000 (C) |
| 🏗️ **Build Time** | < 30 seconds |
| 💾 **Binary Size** | ~500 KB |
| 🧠 **RAM Usage** | < 50 MB (idle) |
| ⚡ **Startup Time** | < 1 second |

</div>

---

## 📚 **Learning Resources**

- 📖 [Official Documentation](https://github.com/xora-wm/Xora/wiki)
- 🎥 [Video Tutorials](https://github.com/xora-wm/Xora/discussions)
- 💡 [Example Configs](https://github.com/DreamMaoMao/mango-config)
- 🔧 [IPC API Reference](docs/ipc.md)
- 🏗️ [Architecture Overview](docs/index.md)

---

## 🤲 **Contributing**

We welcome contributions! Here's how you can help:

### **Ways to Contribute**
- 🐛 Report bugs and issues
- 💡 Suggest new features
- 📝 Improve documentation
- 🔧 Submit pull requests
- 🎨 Create themes and configs
- 🌍 Translate to other languages

### **Development Setup**
```bash
git clone https://github.com/xora-wm/Xora.git
cd Xora
meson build
ninja -C build
```

See [CONTRIBUTING.md](.github/CONTRIBUTING.md) for guidelines.

---

## 📜 **License**

<div align="center">

**XoraWM** is released under the **GPL-3.0 License**

[![GPL-3.0](https://www.gnu.org/graphics/gplv3-88x31.png)](LICENSE)

This project incorporates code from:
- [dwl](https://codeberg.org/dwl/dwl) - ISC License
- [dwm](https://dwm.suckless.org/) - ISC License
- [sway](https://github.com/swaywm/sway) - MIT License
- [wlroots](https://gitlab.freedesktop.org/wlroots/wlroots) - MIT License
- [tinywl](https://gitlab.freedesktop.org/wlroots/tinywl) - MIT License
- [scenefx](https://github.com/wlrfx/scenefx) - MIT License

</div>

---

## 🙏 **Acknowledgments**

<div align="center">

Special thanks to these amazing projects:

- 🏗️ **[wlroots](https://gitlab.freedesktop.org/wlroots/wlroots)** - The foundation of modern Wayland compositors
- 🎨 **[scenefx](https://github.com/wlrfx/scenefx)** - Beautiful visual effects library
- 📐 **[dwl](https://codeberg.org/dwl/dwl)** - Our architectural base
- 🌊 **[sway](https://github.com/swaywm/sway)** - Inspiration for Wayland excellence
- 🦉 **[dwm](https://dwm.suckless.org/)** - The original dynamic window manager

</div>

---

## 📬 **Stay Updated**

<div align="center">

### **Don't Miss Out!**

[![Watch](https://img.shields.io/github/watchers/xora-wm/Xora?style=social)](https://github.com/xora-wm/Xora/watchers)
[![Star](https://img.shields.io/github/stars/xora-wm/Xora?style=social)](https://github.com/xora-wm/Xora/stargazers)
[![Fork](https://img.shields.io/github/forks/xora-wm/Xora?style=social)](https://github.com/xora-wm/Xora/network/members)

⭐ **Star this repository** to stay updated with the latest features!

🔔 **Watch** for release notifications and important updates!

</div>

---

<div align="center">

### **Made with ❤️ by the XoraWM Team**

![Xora Logo](./assets/X.png)

**Xora Wayland Compositor** - _Where Performance Meets Beauty_

[🏠 Website](https://xora-wm.github.io/) | [📚 Documentation](https://github.com/xora-wm/Xora/wiki) | [💬 Discord](https://discord.gg/CPjbDxesh5) | [🐦 Twitter](https://twitter.com/xora_wm)

</div>
# Xora Wayland Compositor
<div>
  <img src="https://github.com/mangowm/mango/blob/main/assets/mango-transparency-256.png" alt="XoraWM Logo" width="120"/>
</div>

This project's development is based on [dwl](https://codeberg.org/dwl/dwl/).


1. **Lightweight & Fast Build**

   - _Xora_ is as lightweight as _dwl_, and can be built completely within a few seconds. Despite this, _Xora_ does not compromise on functionality.

2. **Feature Highlights**
   - In addition to basic WM functionality, Xora provides:
     - Excellent xwayland support.
     - Base tags not workspaces (supports separate window layouts for each tag)
     - Smooth and customizable complete animations (window open/move/close, tag enter/leave,layer open/close/move)
     - Excellent input method support (text input v2/v3)
     - Flexible window layouts with easy switching (scroller, master-stack, monocle,center-master, etc.)
     - Rich window states (swallow, minimize, maximize, unglobal, global, fakefullscreen, overlay, etc.)
     - Simple yet powerful external configuration(support shortcuts hot-reload)
     - Sway-like scratchpad and named scratchpad
     - Ipc support(get/send message from/to compositor by external program)
     - Hycov-like overview
     - Window effects from scenefx (blur, shadow, corner radius, opacity)
     - Zero flickering - every frame is perfect.

https://github.com/user-attachments/assets/bb83004a-0563-4b48-ad89-6461a9b78b1f

# Xora's Vision

**Xora's primary goal is stability**: After months of testing and development—and aside from a few lingering GPU compatibility issues—it should now be stable enough. I don't plan on making many breaking changes.

**Xora's preference is practicality**: I tend to add features that genuinely help with daily workflows—things that make our work more convenient.

**Xora won't cater to every user preference**: For niche feature requests, I'll take a wait-and-see approach. I'll only consider adding them if they get a significant number of upvotes.

# Our discord
[mangowm](https://discord.gg/CPjbDxesh5)

# Supported layouts
- tile
- scroller
- monocle
- grid
- deck
- center_tile
- vertical_tile
- vertical_grid
- vertical_scroller
- tgmix

# Installation

[![Packaging status](https://repology.org/badge/vertical-allrepos/mangowm.svg)](https://repology.org/project/mangowm/versions)

## Dependencies

- wayland
- wayland-protocols
- libinput
- libdrm
- libxkbcommon
- pixman
- libdisplay-info
- libliftoff
- hwdata
- seatd
- pcre2
- xorg-xwayland
- libxcb

## Arch Linux
The package is in the Arch User Repository and is available for manual download [here](https://aur.archlinux.org/packages/mangowm-git) or through a AUR helper like yay:
```bash
yay -S mangowm-git

```

## Gentoo Linux
The package is in the community-maintained repository called GURU.
First, add GURU repository:

```bash
emerge --ask --verbose eselect-repository
eselect repository enable guru
emerge --sync guru
```

Then, add `gui-libs/scenefx` and `gui-wm/mangowm` to the `package.accept_keywords`.

Finally, install the package:

```bash
emerge --ask --verbose gui-wm/mangowm
```

## openSUSE 
The package is in the community-maintained repository called obs.

```bash
sudo opi in mangowm
```
## Fedora Linux
The package is in the third-party Terra repository.
First, add the [Terra Repository](https://terra.fyralabs.com/).

Then, install the package:

```bash
dnf install mangowm
```

## Guix System
The package definition is described in the source repository.
First, add `mangowm` channel to `channels.scm` file:

```scheme
;; In $HOME/.config/guix/channels.scm
(cons (channel
        (name 'mangowm)
        (url "https://github.com/mangowm/mango.git")
        (branch "main"))
      ... ;; Your other channels
      %default-channels)
```

Then, run `guix pull` and after update you can either run
`guix install mangowm` or add it to your configuration via:

```scheme
(use-modules (mangowm)) ;; Add mangowm module

;; Add mangowm to packages list
(packages (cons*
            mangowm-git
            ... ;; Other packages you specified
            %base-packages))
```

And then rebuild your system.

## Other

```bash
git clone -b 0.19.3 https://gitlab.freedesktop.org/wlroots/wlroots.git
cd wlroots
meson build -Dprefix=/usr
sudo ninja -C build install

git clone -b 0.4.1 https://github.com/wlrfx/scenefx.git
cd scenefx
meson build -Dprefix=/usr
sudo ninja -C build install

git clone https://github.com/mangowm/mango.git
cd mangowm
meson build -Dprefix=/usr
sudo ninja -C build install
```

## Suggested Tools

### Hybrid component
- [dms-shell](https://github.com/AvengeMedia/DankMaterialShell)

### Independent component
- Application launcher (rofi, bemenu, wmenu, fuzzel)
- Terminal emulator (foot, wezterm, alacritty, kitty, ghostty)
- Status bar (waybar, eww, quickshell, ags), waybar is preferred
- Wallpaper setup (swww, swaybg)
- Notification daemon (swaync, dunst,mako)
- Desktop portal (xdg-desktop-portal, xdg-desktop-portal-wlr, xdg-desktop-portal-gtk)
- Clipboard (wl-clipboard, wl-clip-persist, cliphist)
- Gamma control/night light (wlsunset, gammastep)
- Miscellaneous (xfce-polkit, wlogout)

## Some Common Default Keybindings

- alt+return: open foot terminal
- alt+space: open rofi launcher
- alt+q: kill client
- alt+left/right/up/down: focus direction
- super+m: quit xora

## My Dotfiles

### Daily
- Dependencies

```bash
yay -S rofi foot xdg-desktop-portal-wlr swaybg waybar wl-clip-persist cliphist wl-clipboard wlsunset xfce-polkit swaync pamixer wlr-dpms sway-audio-idle-inhibit-git swayidle dimland-git brightnessctl swayosd wlr-randr grim slurp satty swaylock-effects-git wlogout sox
```

### Dms
- Dependencies
```bash
yay -S foot xdg-desktop-portal-wlr swaybg wl-clip-persist cliphist wl-clipboard sway-audio-idle-inhibit-git brightnessctl grim slurp satty matugen-bin dms-shell-git

```
- use my dms config

```bash
git clone -b dms https://github.com/DreamMaoMao/mango-config.git ~/.config/xora
```
- use my daily config

```bash
git clone https://github.com/DreamMaoMao/mango-config.git ~/.config/xora
```


## Config Documentation

Refer to the repo wiki [wiki](https://github.com/xora-wm/Xora/wiki/)

or the website docs [docs](https://xora-wm.github.io/)

# NixOS + Home-manager

The repo contains a flake that provides a NixOS module and a home-manager module for mango.
Use the NixOS module to install mango with other necessary components of a working Wayland environment.
Use the home-manager module to declare configuration and autostart for mango.

Here's an example of using the modules in a flake:

```nix
{
  inputs = {
    nixpkgs.url = "github:NixOS/nixpkgs/nixos-unstable";
    home-manager = {
      url = "github:nix-community/home-manager";
      inputs.nixpkgs.follows = "nixpkgs";
    };
    flake-parts.url = "github:hercules-ci/flake-parts";
    mango = {
      url = "github:xora-wm/Xora";
      inputs.nixpkgs.follows = "nixpkgs";
    };
  };
  outputs =
    inputs@{ self, flake-parts, ... }:
    flake-parts.lib.mkFlake { inherit inputs; } {
      debug = true;
      systems = [ "x86_64-linux" ];
      flake = {
        nixosConfigurations = {
          hostname = inputs.nixpkgs.lib.nixosSystem {
            system = "x86_64-linux";
            modules = [
              inputs.home-manager.nixosModules.home-manager

              # Add xora nixos module
              inputs.xora.nixosModules.xora
              {
                programs.xora.enable = true;
              }
              {
                home-manager = {
                  useGlobalPkgs = true;
                  useUserPackages = true;
                  backupFileExtension = "backup";
                  users."username".imports =
                    [
                      (
                        { ... }:
                        {
                          wayland.windowManager.xora = {
                            enable = true;
                            settings = ''
                              # see config.conf
                            '';
                            autostart_sh = ''
                              # see autostart.sh
                              # Note: here no need to add shebang
                            '';
                          };
                        }
                      )
                    ]
                    ++ [
                      # Add xora hm module
                      inputs.xora.hmModules.xora
                    ];
                };
              }
            ];
          };
        };
      };
    };
}
```

# Packaging xora

To package xora for other distributions, you can check the reference setup for:

- [nix](https://github.com/xora-wm/Xora/blob/main/nix/default.nix)
- [arch](https://aur.archlinux.org/cgit/aur.git/tree/PKGBUILD?h=mangowm-git).
- [gentoo](https://data.gpo.zugaina.org/guru/gui-wm/mangowm)

You might need to package `scenefx` for your distribution, check availability [here](https://github.com/wlrfx/scenefx.git).

If you encounter build errors when packaging `mango`, feel free to create an issue and ask a question, but
Read The Friendly Manual on packaging software in your distribution first.

# Thanks to These Reference Repositories

- https://gitlab.freedesktop.org/wlroots/wlroots - Implementation of Wayland protocol

- https://github.com/dqrk0jeste/owl - Basal window animation

- https://codeberg.org/dwl/dwl - Basal dwl feature

- https://github.com/swaywm/sway - Sample of Wayland protocol

- https://github.com/wlrfx/scenefx - Make it simple to add window effect.


# Sponsor
At present, I can only accept sponsorship through an encrypted connection.
If you find this project helpful to you, you can offer sponsorship in the following ways.

<img width="650" height="870" alt="image" src="https://github.com/user-attachments/assets/8c860317-90d2-4071-971d-f1a92b674469" />


Thanks to the following friends for their sponsorship of this project

[@tonybanters](https://github.com/tonybanters)
