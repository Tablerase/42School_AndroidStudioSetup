# Android Studio Setup

<img src="https://skillicons.dev/icons?i=androidstudio" alt="AndroidStudio" title="Android Studio" align="right">

Android Studio at 42 School requieres too much space to be installed (42School session storage in 2025 - 5GB).

This script setup symbolic link to overide Android Studio default installation locations
to locations defined in the script (u can change them depending on what u need).

If you use a temporary directory. You should `--save` before logging out.

## Usage

```bash
Usage: ./setup_android.sh [option...] {init|save}

-h/--help	Display this msg
--init		Setup android studio to `usage set in script` and exit
--save		Move android studio needed files into `storage set in script`
```

### Setup

```bash
./setup_android.sh --init
```

Creates folders and symbolic links according to defined locations with user home dir.
- If you need to install on another devices like a `usb, ssd, etc...` do a symbolic link in your home to this device.
	```bash
	ln -s your/device/path ~/symbolic_link_name
	```
	- Device path can be found with `df` cmd and other similar cmds

### Save

If you use a temporary directory such as `/tmp` or `/goinfre`, use:

```
./setup_android.sh --save
```

to store android studio files after usage. The choosen storage location will be used when `--init` is run to load your saved files back into usage location.

