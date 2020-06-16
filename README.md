# Backup-Script

![backup-script](https://user-images.githubusercontent.com/8832013/84669169-3bce8200-af2d-11ea-850c-d40e2521e6d5.png)

A Bash script to generate a tar.gz backup file of a folder, with an option to automatically upload the backup file to a cloud service using [rclone](https://github.com/rclone/rclone), and remove local copy afterwards.

List of cloud/storage providers currently supported by rclone can be found [here](https://github.com/rclone/rclone#storage-providers).

Last released version: 1.1.0 ([Changelog](https://github.com/MichaelYochpaz/Backup-Script/blob/master/changelog.md))
## Requirements
* `rclone` configured with at least one remote (only if you plan to use the upload feature)

## Usage
Configuration can be set on the script itself, under the "Configuration" section, to run the script without any argument,  
or using command-line arguments (which will override configuration set on on the script).
```
 Usage: backup [-n <name>] [-s <path>] [-e <pattern>]... [-u <path>] [-r] [-v] <path-to-backup>

 Options:
   -n <name>     Sets the tar.gz file name [default: "backup"]
   -s <path>     Path to which the generated backup file will be saved to [default: current working directory]
   -e <pattern>  Exclude a pattern (specific files / folders) from being backed up
   -u <path>     rclone path to which the backup file will be uploaded to (not providing one will skip the upload process)
   -r            Removes local copy of backup file after it's been uploaded
   -v            Uses the '-v' option when running tar and rclone

 Commands:
   -h            Displays this help and exists.

 Examples:
 backup "/home/user/important_stuff"
 backup -u "GDrive:/Backups" -r "/home/user/important_stuff/"
 backup -n "important-stuff-backup" -s "/home/user/backups" -e "*.pdf" -e "important_stuff/dont_backup_this_folder" "/home/user/important_stuff/"
```

## To Do
- [ ] Add an option to restore a backup through the script
- [ ] Add an option to customize date format on backup's file name.
- [ ] Add '-l' option to save a log file.
- [ ] Add a scheduled backups setup guide using `cron` and `systemd` to *README*.
