# TERMUX UBUNTU

<div style="width:100%;background-color:black;border:3px solid black;border-radius:6px;margin:5px 0;padding:2px 5px">
  <img src="./logo.jpg"
    alt="image could not be loaded"
    style="color:red;background-color:black;font-weight:bold"/>
</div>

Install Ubuntu in Termux.

> Author: Jore

> Version: jammy-20230626

<details>
<summary>CONTENTS</summary>

- [FEATURES](#features "List of available features.")
- [INSTALLATION](#installation "Steps for installation.")
- [COMMAND LINE OPTIONS](#command-line-options "Available command line options.")
- [HOW TO LOGIN](#how-to-login "Steps on how to login.")
  - [LOGIN INFORMATION](#login-information "User name and password for logging in.")
- [HOW TO START THE VNC SERVER](#how-to-start-the-vnc-server "Steps on how to start the VNC server.")
  - [REQUIREMENTS](#requirements "Requirements for starting the VNC server.")
  - [PROCEDURE](#procedure "Procedure for starting the VNC server.")
- [HOW TO INSTALL DESKTOP AND VNC SERVER](#how-to-install-desktop-and-vnc-server "Steps on how to install a Desktop Environment and a VNC server.")
- [USING AS ROOT](#using-as-root "Installing Ubuntu as root")
- [HOW TO UNINSTALL UBUNTU](#how-to-uninstall-ubuntu "Steps on how to uninstall Ubuntu.")
- [BUGS](#bugs "Bug information")
- [LICENSE](#license "Program license.")

</details>

## FEATURES

- Anti-root fuse.
- Interactive Installation.
- Color output. (if supported)
- Command line options. (see [here](#command-line-options "Available command line options."))
  - Install in custom directory.
  - Install only i.e no configurations. (**use with caution**)
  - Configurations only (**if already installed**)
  - Modify color output.
  - Uninstall.
- Creates a VNC wrapper (see [here](#how-to-start-the-vnc-server "Steps on how to start the VNC server."))
- Automatic configurations. (i.e binding necessary directories)
- Access System and Termux commands. (i.e termux-api commands)
- Customize default shell and zone information before startup.
- Other optimizations and improvements.

## INSTALLATION

1.  Update installed packages by executing the following commands.

```bash
pkg update && pkg upgrade
```

2.  Install `wget`. (`curl` is an alternative)

```bash
pkg install wget
```

3.  Download the installer script. (**install-ubuntu.sh**)

```bash
wget -O install-ubuntu.sh https://raw.githubusercontent.com/jorexdeveloper/termux-ubuntu/main/install-ubuntu.sh
```

4.  Now execute the installer script.

```bash
bash install-ubuntu.sh --help
```

If you are lazy like me, just copy and paste the below commands in Termux.

```bash
pkg update -y && pkg upgrade -y && pkg install -y wget && wget -O install-ubuntu.sh https://raw.githubusercontent.com/jorexdeveloper/termux-ubuntu/main/install-ubuntu.sh && bash install-ubuntu.sh --help
```

## COMMAND LINE OPTIONS

Execute the installer script with `--help` to see available command line options.

```bash
bash install-ubuntu.sh --help
```

## HOW TO LOGIN

After successful installation, run command `ub` or `ubuntu` to start Ubuntu.

### LOGIN INFORMATION

| Login              | Password |
| ------------------ | -------- |
| root (super user)  | **root** |

## HOW TO START THE VNC SERVER

#### REQUIREMENTS:

1.  Make sure you have a **VNC server** and **Desktop environment** installed. (See [here](#how-to-install-desktop-and-vnc-server "Steps on how to start the VNC server."))

2.  Install [NetHunter KeX](https://store.nethunter.com/en/packages "Kali NetHunter Store"), or a **VNC viewer** of your choice.

#### PROCEDURE:

1.  [Login in Ubuntu](#how-to-login "Steps on how to login.") and run command `vnc` to start the VNC server. The server will be started at **localhost** (`127.0.0.1`).

> **Tip:** The program also displays help information with option `-h` or `--help` to guide you further.

2.  On the first run, you will be prompted for a password. You will use this password to login and connect to the VNC server.

3.  Now open NetHunter KeX and login with the password in step 2.

| User  | Display | Port | Address     |
| ----- | ------- | ---- | ----------- |
| Root  | :0      | 5900 | localhost:0 |
| Other | :1      | 5901 | localhost:1 |

## HOW TO INSTALL DESKTOP AND VNC SERVER

1.  [Login in Ubuntu as root](#how-to-login "Steps on how to login.").

2.  Make a full upgrade of your system.

```bash
apt update && apt full-upgrade
```

3.  Install `sudo`

```bash
apt install sudo
```

4.  Unminimize the file system.

```bash
sudo unminimize <<<"y"
```

5. Install desktop dependencies.

 ```bash
sudo apt install man sudo dbus-x11 tigervnc-standalone-server
```

6. Install desktop.

```bash
sudo apt install ubuntu-gnome-desktop gnome-core
```
or

```bash
sudo apt install ubuntu-desktop-xfce
```

> **Tip:** This will take a while, just make sure you don't exit Termux during the installation or you might run into some problems later.

## USING AS ROOT

**Installing/Running Ubuntu as root** can have unintended effects, and should only be done when you are sure of what's happening in the background (how linux works) or you might **damage your device**, even worse **bricking it**.

For that reason, I have added an **anti root fuse** and disabling it will require you to comment out the appropriate lines from the installer script.

**NOTE: You can still have root privileges within Ubuntu provided by `proot`, even without installing as root. (see the proot manual pages)**

You will have to search and comment out the function call to `check_root` in the installer script. i.e

```bash
  # check_root
```

## HOW TO UNINSTALL UBUNTU

To uninstall Ubuntu, run the installer script (**install-ubuntu.sh**) with option `--uninstall`.

**NOTE:** If you installed Ubuntu in a custom directory, also supply the path to the directory as an argument.

```bash
bash install-ubuntu.sh --uninstall
```

## BUGS

All currently known bugs are fixed. Please let me know in the [issues section](https://github.com/jorexdeveloper/termux-ubuntu/issues "The issues section.") if you find any.

## LICENSE

```txt
    Copyright (C) 2023  Jore

    This program is free software: you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation, either version 3 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program.  If not, see <https://www.gnu.org/licenses/>.
```
