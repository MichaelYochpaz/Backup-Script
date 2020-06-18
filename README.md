# Backup-Script

![backup-script](https://user-images.githubusercontent.com/8832013/84669169-3bce8200-af2d-11ea-850c-d40e2521e6d5.png)

A Bash script to generate a tar.gz backup file of a folder, with an option to automatically upload the backup file to a cloud service using [rclone](https://github.com/rclone/rclone), and remove local copy afterwards.

List of cloud/storage providers currently supported by rclone can be found [here](https://github.com/rclone/rclone#storage-providers).

Latest version: 1.2.0 ([changelog](https://github.com/MichaelYochpaz/Backup-Script/blob/master/changelog.md))
## Features
* Generate a tar.gz backup file of a folder
* Exclude specific folders / patterns
* Automatic upload of backup file to a cloud service using rclone
* Automatic removal of local backup file once upload is finished
* Pushbullet notifications  



##  Requirements
### Optional
* `rclone` , configured with at least one remote (for using the upload feature)
* A [Pushbullet](https://www.pushbullet.com/) account (for receiving Pushbullet notifications)

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
   -p <API key>  Sends a Pushbullet notification once backup is done to the given API key
   -r            Removes local copy of backup file after it's been uploaded
   -y            Skip warnings (by default, warnings require user input to contine)
   -v            Uses '-v' option when running tar and rclone

 Commands:
   -h            Displays this help and exists.

 Examples:
 backup "/home/user/important_stuff"
 backup -u "GDrive:/Backups" -r -y -p "XXXXXXXXXXXXXXXX" "/home/user/important_stuff/" 
 backup -n "important-stuff-backup" -s "/home/user/backups" -e "*.pdf" -e "important_stuff/dont_backup_this_folder" "/home/user/important_stuff/"
```

## FAQ
**Q:** Why use `tar` and not `gzip` for backups?  
**A:** The tar format can store symlinks and file permissions, whereas the zip format, can't.

**Q:** I have a Pushbullet account. Where do I find my API key?  
**A:** Go to your Pushbullet account's [settings page](https://www.pushbullet.com/#settings/account), and click the "Create Access Token" button.

**Q:** I found a bug, or have an idea for a feature. What do I do?  
**A:** Feel free to open a [issue](https://github.com/MichaelYochpaz/Backup-Script/issues) with bugs / suggestions / improvments.
