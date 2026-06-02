# Euro-Office Desktop Editors (Automated Builds)

This repository provides automated compiled releases of [Euro-Office Desktop Editors](https://github.com/Euro-Office/DesktopEditors). 

Euro-Office is a robust, heavily tailored European community alternative for document editing and collaboration. Since compiling the application from source can take significant time and system resources, this project automates the process and provides immediate downloads.

## Features

- **Daily Upstream Tracking:** The repository automatically tracks the primary Euro-Office repository for new releases via GitHub Actions.
- **Arch Linux Packages:** Natively built Arch Linux `.pkg.tar.zst` packages are generated and provided for easy installation on Arch-based distributions.
- **AUR Integration:** Maintains the `euro-office-desktopeditors-bin` wrapper script for the Arch User Repository (AUR), allowing Arch users to simply install the pre-compiled version via pacman or their favorite AUR helper.
- **Universal AppImages:** Creates a portable `.AppImage` out of the build artifacts, ensuring users on Ubuntu, Fedora, Debian, and other distributions can run Euro-Office without compilation or dependency headaches.

## Installation

### Arch Linux (via AUR)

The simplest way for Arch Linux users to install the pre-compiled binary is through the AUR. Using `yay` (or another AUR helper):

```bash
yay -S euro-office-desktopeditors-bin
```

### Other Linux Distributions (AppImage)

For non-Arch users, navigate to the [Releases](https://github.com/YOUR_USERNAME/euro-office-builds/releases) page of this repository and download the latest `.AppImage` file.

```bash
# Make the downloaded AppImage executable
chmod +x euro-office-desktopeditors.AppImage

# Run it
./euro-office-desktopeditors.AppImage
```

## How It Works

1. A daily cron job securely pings the upstream GitHub API to identify new version tags.
2. If a new tag is detected, the GitHub Actions runner provisions an Arch Linux build environment.
3. The host Docker socket is exposed to compile the official build targets securely using `docker buildx bake`.
4. Artifacts are bundled into Arch Linux's pacman format and then securely transformed into a standalone portable AppImage.
5. Everything is uploaded to GitHub Releases automatically and the AUR package `PKGBUILD` index is updated.

## Contributing

Pull requests targeting workflow improvements, package structure, and general fixes are always welcome. Please ensure they remain compatible with the GitHub Actions CI environment.
