# Android Studio Setup

<img src="https://skillicons.dev/icons?i=androidstudio" alt="AndroidStudio" title="Android Studio" align="right">

Android Studio at 42 School requieres too much space to be installed (42School session storage in 2025 - 5GB).

This script setup symbolic link to overide Android Studio default installation locations
to locations defined in the script (u can change them depending on what u need).

If you use a temporary directory. You should `--save` before logging out.

## First time setup

1. Clone this repository:
   ```bash
   git clone
   ```
2. Change directory to the cloned repository:
   ```bash
   cd 42School_AndroidStudioSetup
   ```
   
> [!IMPORTANT]\
   > 3. **Modify the `setup_android.sh` script to suit your needs**:
   ```bash
   nano setup_android.sh
   ```
   - You **must change** `usage` and `storage` variables to your desired locations.
      - `usage` is where Android Studio will run from, and `storage` is where it will save files when you use the `--save` option.
        - `usage` should be a location with enough space for Android Studio to run. (e.g., `/tmp`, `/goinfre`, or a mounted drive).
        - `storage` should be a location where you can store files persistently (e.g., a USB drive, SSD, or a directory in your home folder).
      - If you want to use a USB drive or SSD, make sure to create a symbolic link in your home directory pointing to the device path.
        - For example do this if your device is mounted at `/path/to/your/device`:
          ```bash
          ln -s /path/to/your/device ~/android_storage
          ```
          To find the device path, you can use the `df` command or similar commands to list mounted filesystems.
          ```bash
          df -h
          ```
          ```output
          Filesystem      Size  Used Avail Use% Mounted on
          /dev/sda1       100G   50G   50G	50% /
          /dev/sdb1       200G  150G	 50G	75% /path/to/your/device
          ```
        - Then set `storage` to `android_storage` in the script and `usage` to `android_storage` if you want to use the same location for both.
   - After modifying, save the file:
     - If using `nano`, press `CTRL + O`, then `Enter` to save, and `CTRL + X` to exit.
     - If using another editor, follow the appropriate save and exit commands for that editor.
       
4. Run the script to set up Android Studio:
   ```bash
   ./setup_android.sh --init
   ```

5. After **running the script, you can start Android Studio.**
   - You can then follow the Android Studio setup wizard to configure it for your needs.
     
6. If you need to save your Android Studio files for later use, run:
   ```bash
   ./setup_android.sh --save
   ```

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
