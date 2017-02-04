#home_backup.py

This is a backup script written in Python using 'rsync'. I use it to backup files from my personal MacBook Air and iMac computers.
It can be used for incremental and differential backup. If properly configured it will send an email and summarize the backup.

For additional info see... https://www.zufallsheld.de/2013/09/29/python-backup-script-with-rsync/

**Usage:**

    python home_backup.py [-h] [-t] [-e DIR] [-l FILE] [-q] [-m MAIL] [-u]
                          [-d] [--delete] [--legacy] [--check]
                          [--link LINK] [--date]
                            SOURCE TARGET
                     
Note: In my case the alias _home_backup_ is defined in .bash_profile as 
    
    home_backup = python /Users/mark/Projects/Python/home_backup/home_backup/home_backup.py
    

**Positional arguments:**

    SOURCE      Specify the directory to backup from.  Do NOT follow with a slash!
        
  
    TARGET      Specify the directory where the backup should be stored.  Do NOT follow with a slash!
                        

**Optional arguments:**

    -h, --help                  Show this help message and exit.
        
    -r, --remove                Passes --remove-source-files so that successfully copied files are 
                                    deleted from SOURCE.
                                    
    -t, --trash                 Delete unnecessary files and empty the trash.
        
    -e DIR, --exclude DIR       Exclude the specified directory from backup.
        
    -l FILE, --logfile FILE     Specify a log file to create.  If FILE exists it will be overwritten.
        
    -q, --quiet                 Do not print to stdout.
        
    -m MAIL, --mail MAIL        eMail address to send the rsync log to.
        
    -u, --update                Keeps files in destination if they are more recent.
        
    -d, --debug                 Generates a detailed rsync log.
        
    --delete                    Deletes DESTINATION files and folders that do NOT exist in SOURCE.  
    
    --legacy                    Support for some systems without the ability to change permissions.
        
    --check                     Checks the transfered files byte-by-byte with a generated checksum. 
                                    This can take a while.  This option verifies that the 
                                    DESTINATION files are identical to the SOURCE.
                                        
    --link LINK                 Creates a new backup and only saves differences to the specified 
                                    main-backup. For an incremental backup use this option with the 
                                    argument ->last<-. The script then looks up the last backup in 
                                    the target directory.
                                    
    --date                      Saves the backup into a subfolder named after the actual date in 
                                    format YYYY-MM-DD inside DESTINATION.

**Deprecated arguments:**    
    
    -c CONFIG, --config CONFIG    Loads the config from a specified property file.


**Change log:**

    01/17: Mark McFate: Added --remove option and .netrc for SMTP credentials.
    02/15: Pascal Laub: Improved the script, added a mail-option.
        
        
        -Sebastian Gumprich http://zufallsheld.de
        -Pascal Laub
