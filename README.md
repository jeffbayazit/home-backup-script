Linux Home Directory Backup Script
----------------------------------
A lightweight Bash utility designed to automate the backup of a Linux home directory to an external USB drive. It features automatic mount-point detection and uses rsync for efficient, incremental data transfers.

Features

Smart Drive Detection: Automatically identifies the backup destination by searching for a drive labeled "Backup".


Fallback Logic: If no label is found, it attempts to identify an external partition (sdX) to ensure the backup doesn't fail.


Timestamped Backups: Creates unique directories for every run using the format bkup_YYYY-MM-DD_HH-MM-SS.


Optimized Transfer: Uses rsync with the -avh flags to preserve permissions and provide human-readable progress, while excluding heavy or unnecessary directories like snap and virtual machines.

Prerequisites
Linux OS: Designed for Linux environments (tested on ChromeOS/Linux environments).

rsync: Ensure rsync is installed on your system.


USB Drive: A drive with the partition label "Backup" is recommended for the best experience.

Installation & Usage
Download the script:
Save the bkup file to your local machine.

Make it executable:
Open your terminal and run:

Bash
chmod +x bkup
Run the backup:
Plug in your USB drive and execute the script:

Bash
./bkup
Script Logic Overview
The script follows a specific hierarchy to ensure your data ends up in the right place:


Define Source: Targets /home/jeff as the primary directory.


Locate Target: Uses lsblk and awk to find a valid mount point that isn't the boot or root partition.


Validate: If no drive is detected, the script exits safely with an error message to prevent accidental local data writes.


Execute: Synchronizes files and folders while displaying a progress bar.
