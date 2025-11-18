# orphanrm

A simple command-line tool for Arch Linux that scans for and removes orphaned packages.

## What are orphaned packages?

Orphaned packages are packages that were installed as dependencies but are no longer required by any installed package. They take up disk space and can clutter your system over time.

## Features

- 🔍 Scan for orphaned packages
- 📋 List orphaned packages with details (size, description)
- 🗑️ Interactive removal with confirmation
- ⚡ Auto-removal mode for advanced users
- 🎨 Colorful terminal output

## Installation

### From AUR

```bash
# Using yay
yay -S orphanrm

# Using paru
paru -S orphanrm

# Manual installation
git clone https://aur.archlinux.org/orphanrm.git
cd orphanrm
makepkg -si
```

### Manual Installation

```bash
git clone https://github.com/AquaCheese/orphanrm.git
cd orphanrm
sudo install -Dm755 orphanrm /usr/bin/orphanrm
```

## Usage

### Interactive Mode (Default)

Simply run the command to scan for orphans and choose whether to remove them:

```bash
orphanrm
```

### List Only Mode

View orphaned packages without removing them:

```bash
orphanrm --list
# or
orphanrm -l
```

### Auto-Remove Mode

Automatically remove all orphaned packages without confirmation (use with caution):

```bash
orphanrm --auto
# or
orphanrm -a
```

### Other Options

```bash
orphanrm --help      # Show help message
orphanrm --version   # Show version information
```

## Example Output

```
Scanning for orphaned packages...

Found 3 orphaned package(s):

▸ example-lib
  Size: 2.5 MiB
  Description: Example library for demonstration

▸ old-dependency
  Size: 512.0 KiB
  Description: Legacy dependency package

▸ unused-tool
  Size: 1.2 MiB
  Description: Unused utility tool

The following packages will be removed:
  - example-lib
  - old-dependency
  - unused-tool

Do you want to proceed? [y/N]
```

## Requirements

- Arch Linux or Arch-based distribution
- `pacman` package manager
- `sudo` privileges (for package removal)

## Safety

- The script prevents running as root directly and will request sudo privileges only when needed
- Interactive mode requires explicit confirmation before removing packages
- All package information is displayed before removal

## Contributing

Contributions are welcome! Please feel free to submit issues or pull requests.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

Copyright (c) 2025 AquaCheese

## Acknowledgments

This tool uses `pacman -Qdtq` to identify orphaned packages, which is the standard method on Arch Linux systems.
