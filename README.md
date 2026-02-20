# CSF-Sweeper
A tool for ConfigServer Firewall that will ban any IP's permanently if they get caught doing bad things enough times

# Note
- It is recommended to run this script daily, to ensure nothing can slip through the cracks.
- If there are any changes or improvements you want to make, feel free to send a push request and we will check it out.
- Make sure the CHMOD permissions are set to ```700``` to ensure the script runs without errors.

# Installation
Download the csfsweeper file save it under /scripts.
To add a cron job for this file to be executed, follow these commands:
- Use the terminal and navigate to the server's files.
- Use ```crontab -e``` to view and edit all your cron jobs.
- If you want to run this at 6:30 every day, this would be the cron job entry you need to add ```30 6 * * * /scripts/csfsweeper```

You install csfsweepber by manually saving it under /scripts, or by using the following command to set up the file in the right location and set up the cron job.
```curl -fsSL https://raw.githubusercontent.com/Linuxweb/CSF-Sweeper/main/csfsweeper -o /scripts/csfsweeper && chmod 700 /scripts/csfsweeper && (crontab -l 2>/dev/null; echo "30 6 * * * /scripts/csfsweeper") | crontab -```

# Settings
- **$test_mode**           = Use 1 for Live Mode and 0 for Test Mode. (Live uses your real csf.deny file, and test uses a test file)
- **$dry_run_mode**        = Use 1 to simulate the actions (Sends a report as if they were executed) and 0 to perform the changes for real.
- **$BACKUP_RETENTION**    = Number of backups to keep (First In, First Out)    
- **$OCTET_COUNT**        = First number of octets to use in the search (3 = xxx.xxx.xxx.0/24)
- **$MIN_OCCURRENCES**     = Minimum number of occurences for it to ban
- **$MAIL_TO**             = Email address the report is going to send to
- **$MAIL_FROM**          = Email address the report is going to come from
- **$BACKUP_DIR**          = Backups storage location
- **$CSF_DENY_LIVE**       = Directory for your real csf.deny file
- **$CSF_DENY_TEST**       = Directory for your test csf.deny file

# Using the deny.csf.test file
- Make sure the **$CSF_DENY_TEST** reflects the directory of the file
- This file is intended for use with an **$OCTET_COUNT** of 3, and a **$MIN_OCCURRENCES** of 3
