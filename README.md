# LinuxTools

## System Information

These tools were created to help improve my own personal Linux experience, so they might not work for others, especially with vastly different distros (such as Debian based distros due to it using a different package manager, for example). I have also added prompts where possible in case only some tasks of a script are useful (such as the unnecessary update of EndeavourOs mirrorlists in an Arch system, for example).

My system runs Arch based EndeavourOs, with a KDE Plasma 6 desktop environment, along with a systemd-boot bootloader.

I expect most of these tools should work at least for those running an Arch based Linux system just fine, but no testing other than on my own system was made. Also not sure how they'll behave on systems with multiple users. Use them at your own risk.

## backupConfigs

Backs up the specified configs (or other files) into the a designated folder.

- CONFIG variable designates the desired configs (or other files to backup);
- DEST_FOLDER parameter designates the desired folder to backup the configs to;

Example execution:

```
./backupConfigs
```

## autoBackupConfigs

Same as backupConfigs, but with changes to permit execution by a systemd service (removed prompts and unnecessary stuff).

Use with backup-configs.service and backup-configs.timer to automate.

## backup-configs.service and backup-configs.timer

Automates backupConfigs execution and executes the script once a month.
Should be placed in /etc/systemd/system/

```
/usr/bin/autoBackupConfigs should be changed to whatever is your autoBackupConfigs script path
```

To activate the timer:

```
systemctl daemon-reload
sudo systemctl enable backup-configs.timer
sudo systemctl start backup-configs.timer
sudo systemctl list-timers # optional, just to check if the timer has been activated
```

## bootOptimizations

Boot optimizations I have personally done to my machine to improve boot times.

It was not intended to be executed as is, and, while it can be, it's not recommended to do so unless you understand the commands executed, as they could be harmful to do so.

An explanation of any commands contained is provided as a comment in the script.

## getInstalledPackages

Outputs a text file containing all currently installed packages, both through pacman and the AUR.

Careful when using it to reinstall packages, as it also includes distro specific packages that may not be necessary when changing distro.

- DEST_FOLDER parameter designates the desired folder to output the file to (otherwise it will be set as the current folder);
- DEST_FILE variable designated the desired text file name (and possibly extension, though that wasn't tested);

## autoGetInstalledPackages

Same as getInstalledPackages, but with changes to permit execution by a systemd service (removed prompts and unnecessary stuff).

Use with getInstalledPackages.service and getInstalledPackages.timer to automate.

## getInstalledPackages.service and getInstalledPackages.timer

Automates getInstalledPackages execution and executes the script once a month.
Should be placed in /etc/systemd/system/

```
/usr/bin/autoGetInstalledPackages should be changed to whatever is your autoGetInstalledPackages script path
```

To activate the timer:

```
systemctl daemon-reload
sudo systemctl enable getInstalledPackages.timer
sudo systemctl start getInstalledPackages.timer
sudo systemctl list-timers # optional, just to check if the timer has been activated
```

## globalizeScripts

Makes the selected scripts from the current directory global (copies them into /usr/bin), to make them executable anywhere in the system instead of only on the folder they're contained in.

## open-wofi

Simple script to only open wofi if it isn't currently already open.

Intended to be used when assigned to a keybind.

## prepareSystemD

Script to reinstall kernels, copied from [this tutorial when switching to systemd-boot](https://forum.endeavouros.com/t/tutorial-convert-to-systemd-boot/13290)

## sortImages

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

## systemCleaning

Automates some of the maintenance that should be done to keep the machine 'healthy', so that only the script needs to be executed instead of the individual commands.

- Cleans the journal entries older than 4 weeks;
- Cleans pacman and yay cache and removes ALL uninstalled packages;
- Prompts the user if removing orphan packages is desired and outputs a text file with all the orphan packages found;

- DEST_FOLDER parameter designates the desired folder to output the file to (otherwise it will be set as the current folder);
- DEST_FILE variable designated the desired text file name (and possibly extension, though that wasn't tested)

## autoSystemCleaning

Same as systemCleaning, but with changes to permit execution by a systemd service (removed prompts and unnecessary stuff). Also removed orphan packages removal, as their removal could possibly be problematic and should be done carefully.

Use with systemCleaning.service and systemCleaning.timer to automate.

## systemCleaning.service and systemCleaning.timer

Automates systemCleaning execution and executes the script once a month.
Should be placed in /etc/systemd/system/

```
/usr/bin/autoSystemCleaning should be changed to whatever is your autoSystemCleaning script path
```

To activate the timer:

```
systemctl daemon-reload
sudo systemctl enable systemCleaning.timer
sudo systemctl start systemCleaning.timer
sudo systemctl list-timers # optional, just to check if the timer has been activated
```

## updateConfigs

Checks if the configs contained in the directory provided are in the list and prompts the user if they should be updated.

- The configs system path have to be included in the CONFIGS variable. Any configs not included in CONFIGS will be ignored
- CUR_DIR parameter designates the provided folder with the configs (otherwise it will be set as the current folder);

Example execution:

```
./updateConfigs
```

Or

```
./updateConfigs path/to/folder
```

## updateGlobalScripts

Checks if the scripts contained in the directory provided are global (exist in /usr/bin) and prompts the user if they should be updated.

- CUR_DIR parameter designates the provided folder with the scripts (otherwise it will be set as the current folder);

Example execution:

```
./updateGlobalScripts
```

Or

```
./updateGlobalScripts path/to/folder
```

## updateMirrorlist

Automates updating the mirrorlists, so that only the script needs to be executed instead of the individual commands.

- Updates Arch mirrorlist
- Updates EndeavourOs mirrorlist
- Updates system (yay -Syyu)

## autoUpdateMirrorlist

Same as updateMirrorlist, but with changes to permit execution by a systemd service (removed prompts and unnecessary stuff).

Use with updateMirrorlist.service and updateMirrorlist.timer to automate.

## updateMirrorlist.service and updateMirrorlist.timer

Automates updateMirrorlist execution and executes the script once a month.
Should be placed in /etc/systemd/system/

```
/usr/bin/autoUpdateMirrorlist should be changed to whatever is your autoUpdateMirrorlist script path
```

To activate the timer:

```
systemctl daemon-reload
sudo systemctl enable updateMirrorlist.timer
sudo systemctl start updateMirrorlist.timer
sudo systemctl list-timers # optional, just to check if the timer has been activated
```
