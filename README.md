# nibspark

A keyboard-first app for your docs, written in plain Markdown.

**Download it at [nibspark.app](https://nibspark.app)**, or pick a file from
the [latest release](https://github.com/tulios/nibspark-releases/releases/latest).
This repository holds nibspark's releases.

## Installing

### macOS

`nibspark-<version>.dmg`, universal for Apple silicon and Intel, macOS 11 or
later.
Open it and drag nibspark to Applications. It's signed and notarized by
Apple.

### Windows

`nibspark-<version>-setup.exe`, for x64, Windows 10 or later. It installs
nibspark for you alone, with no admin rights needed, and adds it to the Start
menu. Settings > Apps uninstalls it. `nibspark-<version>-windows-x64.zip` is
the app alone, to run from anywhere.

### Linux

The AppImage is the recommended way: it runs on any distribution, with every
feature. One command downloads it, checks it against the release's checksum,
and adds it to your app launcher, with no root needed:

```sh
curl -fsSL https://nibspark.app/install.sh | sh
```

It works on x86_64 and ARM (aarch64), and nibspark updates itself from then
on. [Review the script](https://nibspark.app/install.sh) before running it if
you like. To uninstall:

```sh
curl -fsSL https://nibspark.app/install.sh | sh -s -- --uninstall
```

Or download `nibspark-x86_64.AppImage` (or `nibspark-aarch64.AppImage` for
ARM) and run it by hand:

```sh
chmod +x nibspark-x86_64.AppImage
./nibspark-x86_64.AppImage
```

#### Flatpak and Snap

nibspark is also available as a Flatpak and a Snap. Because they're
sandboxed, **the AI integration is disabled** in both: their sandboxes don't
let nibspark run the agent installed on your computer.

- **Flatpak**, from nibspark's own Flatpak repository (new to Flatpak?
  [Set it up](https://flatpak.org/setup/) first):

  ```sh
  flatpak install https://flatpak.nibspark.app/nibspark.flatpakref
  ```

  Or open [the link](https://flatpak.nibspark.app/nibspark.flatpakref) in
  GNOME Software or Discover. `flatpak update` keeps it up to date.

- **Snap**, from the [Snap Store](https://snapcraft.io/nibspark) or Ubuntu's
  App Center:

  ```sh
  sudo snap install nibspark
  ```

  Snap keeps it up to date.
