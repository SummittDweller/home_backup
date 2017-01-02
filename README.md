This was a backup-script written in Python using 'rsync'. It is tested on Ubuntu 14.04 and Arch Linux (using --legacy).
It can backup incremental and differential. It will send you an email and summarize the backup.

For additional info see... https://www.zufallsheld.de/2013/09/29/python-backup-script-with-rsync/

Usage:

python home_backup.py [-h] [-t] [-e EXCLUDE] [-l LOGFILE] [-q] [-m MAIL] [-u]
                      [-d] [-c CONFIG] [--delete] [--legacy] [--check]
                      [--link LINK] [--date]
                        SOURCE TARGET
                     

Positional arguments:

  SOURCE                Specify the directory to backup (SOURCE).
  
  TARGET                Specify the directory where the backup should be
                        stored (TARGET).
                        

Optional arguments:

  -h, --help            Show this help message and exit.

  -r, --remove          Passes --remove-source-files to rsync so that successfully copied files are deleted from SOURCE.

  -t, --trash           Delete unnecessary files and empty the trash.
  
  -e EXCLUDE, --exclude EXCLUDE     Exclude the specified directories from backup.
                        
  -l FILE, --logfile FILE     Specify a log file to create.
                        
  -q, --quiet           Do not print to stdout.
  
  -m MAIL, --mail MAIL  eMail-Adress to send the rsync-log to. Use this with the --config option to provide
                        a properties file with an SMTPSection entry.
                        
  -u, --update          Keeps files in destination if they are more recent.
  
  -d, --debug           Generates a detailed rsync log.
  
  -c CONFIG, --config CONFIG    Loads the config from a specified property file.
                        
  --delete              Deletes DESTINATION files and folders that do NOT exist in SOURCE.
                        
  --legacy              Support for some systems without the ability to change permissions.
                        
  --check               Checks the transfered files byte-by-byte with a generated checksum. This can take a while.
                        This option verifies that the DESTINATION files are identical to the SOURCE.
                        
  --link LINK           Creates a new backup and only saves differences to the specified main-backup. For an
                        incremental backup use this option with the argument ->last<-. The script
                        then looks up the last backup in the target directory.
                        
  --date                Saves the backup into a subfolder named after the actual date in format YYYY-MM-DD in DESTINATION.


Change log:

01/17: Mark McFate: Added --remove option.
02/15: Pascal Laub: Improved the script, added a mail-option.

-Sebastian Gumprich http://zufallsheld.de
-Pascal Laub
