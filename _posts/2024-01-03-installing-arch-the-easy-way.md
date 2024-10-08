---
title: "Ditch the Manual: Installing Arch Linux the \"Easy\" Way with archinstall"
last_modified_at: 2024-09-28T23:21:20
categories:
  - Linux
  - English
tags:
  - Linux
  - Open Source
  - Arch Linux
header:
  image: /assets/svg/Archlinux_Logo_Dark.svg
  teaser: /assets/svg/Archlinux_Logo_Dark.svg
  caption: "Arch Linux Dark Logo"
---

<!-- ![Arch_Linux_Logo](/assets/svg/Archlinux_Logo_Dark.svg "Arch Linux logo") -->

Arch Linux. The name itself sends shivers down the spines of some, conjuring images of cryptic text files and hours spent wrestling with the command line. But what if I told you there was a way to experience the Arch magic without the steep learning curve? A streamlined installation process, guided by a friendly script, ready to go right on your Arch ISO? Introducing `archinstall`, the hidden gem waiting to be unleashed.

Forget scouring online forums and memorizing convoluted commands. With `archinstall`, installing Arch is as simple as, well, installing Arch (almost). Just follow these steps:

1. **Burn the ISO**: Download the latest Arch ISO and flash it onto a USB stick. You can use these following tools if you are already in: 
    - **GNU/Linux**: KDE ISO Image Writer, GNOME Disk Utility, SUSE Studio ImageWriter, ...
    - **Windows**: Rufus, USBwriter, ...
    - **MacOS**: USBImager
    
    In all of these OS, you can use **dd** (command line). For more, please check the [Arch Wiki](https://wiki.archlinux.org/title/USB_flash_installation_medium)

2. **Boot Up**: Plug the USB into your target machine and boot it up.

3. **Connect to the World**: Use `iwctl` to connect to your WiFi network and refresh the package keys with `pacman-keys --refresh-keys`.

```shell
# ------------------------------
# |             iwctl          |
# ------------------------------

$ iwctl

# show the list of devices
$ device list

# showing the device wlan0 status
$ station wlan0 show

# start scanning with the device wlan0
$ station wlan0 scan

# Connect to you Wifi
$ station wlan0 connect YourWifiSSID

# to leave iwctl
$ quit
```

Here is a tip:

---

```shell
# ------------------------------
# |  Refresh the package keys  |
# ------------------------------

# Reinitialize files & folders for keys
$ sudo pacman-key --init

# Repopulate keys
$ sudo pacman-key --populate archlinux

# Reinstall latest keyrings
$ sudo pacman -Sy gnupg archlinux-keyring

# Refresh the signature keys
$ sudo pacman-key --refresh-keys

# Clear out the software packages downloaded during aborted installations (optional):
sudo pacman -Sc
```
> I got that tips from [ [HowTo] Solve Keyring Related Issues in Manjaro ](https://forum.manjaro.org/t/howto-solve-keyring-related-issues-in-manjaro/96949) that time I tried to install Arch Linux and It got stuck because the keys where untrustworthy.

4. **Unlock the Magic**: Run the command `archinstall`. Buckle up, the script will guide you through the installation process like a seasoned navigator.

5. **Pick Your Path**: Choose your disk layout, set your timezone, select your audio backend (PipeWire (preferred) or PulseAudio), pick your desktop environment (GNOME, KDE, Xfce, and more!) or a windows manager (Hyprland, i3, sway, and more!), and answer some other key configuration questions.

6. **Sit Back and Relax**: Let archinstall works its magic. It will partition your disk, download and install essential packages, configure your chosen desktop environment, and set you up for success.

7. **Reboot and Revel**: Once the script finishes, reboot your machine. Welcome to the glorious world of Arch Linux, installed the easy way!

### What makes _archinstall_ so special?

* **Guided Installation**: No more deciphering cryptic documentation. archinstall asks you clear questions, making the process intuitive even for newcomers.
* **Flexibility**: Choose your disk layout, desktop environment, and other key settings to customize your Arch experience.
* **Time-Saving**: Ditch the hours of manual configuration. archinstall gets you up and running quickly and efficiently.
* **Pre-Bundled**: No need to download additional scripts or tools. Everything you need is already baked into the Arch ISO.

### Is it really that easy?

While Arch Linux still has its reputation for being a more hands-on distro, archinstall certainly aims to bridge the gap. It simplifies the initial installation process significantly, allowing you to experience the joy of Arch without the initial hurdle. However, remember that Arch remains a DIY-focused distro at its core. Once you're up and running, you'll still have access to the full Arch experience (and community), where customization and learning reign supreme.

**So, are you ready to embark on your Arch adventure with archinstall? Grab that ISO, plug in your USB, and get ready to experience the power and flexibility of Arch the easy way. Remember, the Arch community is always there to guide you along the way. Happy installing!**

> **Bonus Tip**: For even more customization, explore the various archinstall profiles available online. These pre-configured profiles let you tailor your installation to specific needs, like gaming, development, or server setups.

With archinstall, the gateway to Arch Linux is wider than ever. So, take the plunge and discover the beauty of Arch, simplified. [Arch Wiki](https://wiki.archlinux.org/)
