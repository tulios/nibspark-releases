# nibspark

A keyboard-first app for your docs, written in plain Markdown.

**Download it at [nibspark.app](https://nibspark.app)**, or pick a file from
the [latest release](https://github.com/tulios/nibspark-releases/releases/latest).
This repository holds nibspark's releases: the app itself is developed
elsewhere.

## Installing

### macOS

`nibspark-<version>.dmg`, for Apple silicon and Intel, macOS 11 or later.
Open it and drag nibspark to Applications. It's signed and notarized by
Apple, so it opens like any app.

### Windows

`nibspark-<version>-setup.exe`, for x64, Windows 10 or later. It installs
nibspark for you alone, with no admin rights needed, and adds it to the Start
menu; Settings > Apps uninstalls it. `nibspark-<version>-windows-x64.zip` is
the app alone, to run from anywhere.

They aren't signed yet: Windows may say "Windows protected your PC" the first
time. Click **More info**, then **Run anyway**.

### Linux

For x86_64, on Ubuntu 22.04, Debian 12, Arch, or anything as recent.

- **Ubuntu and Debian:** `nibspark_<version>-1_amd64.deb`

  ```sh
  sudo apt install ./nibspark_<version>-1_amd64.deb
  ```

- **Arch and others:** `nibspark-<version>-linux-x86_64.tar.gz`, the app and
  an `install.sh` that adds it to your apps:

  ```sh
  tar -xzf nibspark-<version>-linux-x86_64.tar.gz
  cd nibspark-<version>-linux-x86_64
  ./install.sh              # for you alone, in ~/.local
  sudo ./install.sh --system  # or for everyone, in /usr/local
  ```

  `./install.sh --uninstall` removes it (with `--system` too, if installed for
  everyone).
