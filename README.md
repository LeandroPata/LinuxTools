# LinuxTools

## System Information

These tools were created to help improve my own personal Linux experience, so they might not work for others, especially with vastly different distros (such as Debian based distros due to it using a different package manager, for example).

My system runs Arch based EndeavourOs, with a KDE Plasma 6 desktop environment, along with a systemd-boot bootloader.

I expect these tools should work at least for those running an Arch based Linux system just fine, but no testing other than on my own system was made. Use them at your own risk.

## BackupConfigs

Backs up the specified configs (or other files) into the a designated folder.

- CONFIG variable designates the desired configs (or other files to backup);
- DEST_FOLDER variable designates the desired folder to backup the configs to;

## BootOptimizations

Boot optimizations I have personally done to my machine to improve boot times.

It was not intended to be executed as is, and, while it can be, it's not recommended to do so unless you understand the commands executed, as they could be harmful to do so.

An explanation of any commands contained is provided as a comment in the script.

## GetInstalledPackages

Outputs a text file containing all currently installed packages, both through pacman and the AUR.

Careful when using it to reinstall packages, as it also includes distro specific packages that may not be necessary when changing distro.

- DEST_FOLDER variable designates the desired folder to output the file to;
- DEST_FILE variable designated the desired text file name (and possible extension, though that wasn't tested);

## MaintenanceCleaning

Automates some of the maintenance that should be done to keep the machine 'healthy', so that only the script needs to be executed instead of the individual commands.

- Cleans the journal entries older than 4 weeks;
- Cleans pacman cache and removes ALL uninstalled packages;
- Prompts the user if removing orphan packages is desired and outputs a text file with all the orphan packages found;

- DEST_FOLDER variable designates the desired folder to output the file to;
- DEST_FILE variable designated the desired text file name (and possible extension, though that wasn't tested)

## PrepareSystemD

Script to reinstall kernels, copied from this tutorial when switching to systemd-boot:
https://forum.endeavouros.com/t/tutorial-convert-to-systemd-boot/13290

## UpdateMirrorList

Automates updating the mirrorlists, so that only the script needs to be executed instead of the individual commands.

- Updates Arch mirrorlist
- Updates EndeavourOs mirrorlist
- Updates system (yay -Syyu)
