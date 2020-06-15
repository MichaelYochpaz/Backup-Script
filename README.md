# Backup-Script
A Bash script to generate a tar.gz backup file of a folder, with an option to automatically upload the backup file to a cloud service using [rclone](https://github.com/rclone/rclone), and remove local copy afterwards.

List of cloud/storage providers currently supported by rclone can be found [here](https://github.com/rclone/rclone#storage-providers).

## Dependencies
* `tar`
* `rclone` (needs to be configured)

## Usage
Configuration can be set on the script itself, under the "Configuration" section, to run the script without any argument,  
or using command-line arguments (which will override configuration set on on the script).
```
Usage: backup [-n <name>] [-s <path>] [-u <path>] [-r] <path-to-backup>

Options:
  -n <name>  Sets the tar.gz file name [default: "backup"]
  -s <path>  Path to which the generated backup file will be saved to [default: current working directory]
  -u <path>  Rclone path to which the backup file will be uploaded to (not providing one will skip the upload process)
  -r         Remove local copy of backup file after it's been uploaded

Commands:
  -h         Displays this help and exists.

Examples:
  backup "/home/user/important_stuff"
  backup -n "important-stuff-backup" -s "/home/user/backups" -u "GDrive:/Backups" -r "/home/user/important_stuff/"
```

## Todo
* Add an option to restore a backup.
* Add option to customize date format on backup's file name.
* Add option to exclude files from backup using `tar`'s `--exclude=` argument.
* Add '-v' option to show `tar` and `rclone` outputs.
* Add '-l' option to save a log file.
* Add a scheduled backups setup guide using `cron` and `systemd` to *README.md*.
