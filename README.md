# LinuxTools

## System Information

These tools were created to help improve my own personal Linux experience, so they might not work for others, especially with vastly different distros (such as Debian based distros due to it using a different package manager, for example). I have also added prompts where possible in case only some tasks of a script are useful (such as the unnecessary update of EndeavourOs mirrorlists in an Arch system, for example).

My system runs Arch based EndeavourOs, with a KDE Plasma 6 desktop environment, along with a systemd-boot bootloader.

I expect most of these tools should work at least for those running an Arch based Linux system just fine, but no testing other than on my own system was made. Use them at your own risk.

## ManualBackupConfigs

Backs up the specified configs (or other files) into the a designated folder.

- CONFIG variable designates the desired configs (or other files to backup);
- DEST_FOLDER parameter designates the desired folder to backup the configs to (otherwise it will be set as the current folder);

Example execution:

```
./manualBackupConfigs
```

Or

```
./manualBackupConfigs path/to/folder
```

## BootOptimizations

Boot optimizations I have personally done to my machine to improve boot times.

It was not intended to be executed as is, and, while it can be, it's not recommended to do so unless you understand the commands executed, as they could be harmful to do so.

An explanation of any commands contained is provided as a comment in the script.

## GetInstalledPackages

Outputs a text file containing all currently installed packages, both through pacman and the AUR.

Careful when using it to reinstall packages, as it also includes distro specific packages that may not be necessary when changing distro.

- DEST_FOLDER parameter designates the desired folder to output the file to (otherwise it will be set as the current folder);
- DEST_FILE variable designated the desired text file name (and possibly extension, though that wasn't tested);

## GlobalizeScripts

Makes the selected scripts from the current directory global (copies them into /usr/bin), to make them executable anywhere in the system instead of only on the folder they're contained in.

## PrepareSystemD

Script to reinstall kernels, copied from this tutorial when switching to systemd-boot:
<https://forum.endeavouros.com/t/tutorial-convert-to-systemd-boot/13290>

## SortImages

Sorts images in a folder (recursively, includes images within subfolders) by pixel amount and exports the sorted list to text file in the current folder.

- List includes the image path, the image resolution, the image format and the pixel amount;
- The intended folder can be defined by a parameter (otherwise it's the current folder);
- If instead of a folder, a file's path is inserted, only that image's information is exported to the text file;

Example execution:

```
./sortImages
```

Or

```
./sortImages path/to/folder
```

Or

```
./sortImages path/to/image
```

## ManualSystemCleaning

Automates some of the maintenance that should be done to keep the machine 'healthy', so that only the script needs to be executed instead of the individual commands.

- Cleans the journal entries older than 4 weeks;
- Cleans pacman and yay cache and removes ALL uninstalled packages;
- Prompts the user if removing orphan packages is desired and outputs a text file with all the orphan packages found;

- DEST_FOLDER parameter designates the desired folder to output the file to (otherwise it will be set as the current folder);
- DEST_FILE variable designated the desired text file name (and possibly extension, though that wasn't tested)

## SystemCleaning

Same as ManualSystemCleaning, but with changes to permit execution by a systemd service (removed prompts and unnecessary stuff). Also removed orphan packages removal, as their removal could possibly be problematic and should be done carefully.

Use with systemCleaning.service and systemCleaning.timer to automate.

## SystemCleaning.service and SystemCleaning.timer

Automates systemCleaning execution and executes the script once a month

```
/usr/bin/systemCleaning should be changed to whatever is your systemCleaning script path
```

## ManualUpdateMirrorList

Automates updating the mirrorlists, so that only the script needs to be executed instead of the individual commands.

- Updates Arch mirrorlist
- Updates EndeavourOs mirrorlist
- Updates system (yay -Syyu)

## UpdateGlobalScripts

Checks if the scripts contained in the current directory are global (exist in /usr/bin) and prompts the user if they should be updated.
